## java restful api文档生成工具
> 基于接口源码分析来生成接口文档，完全做到零注解侵入，你只需要按照java标准注释的写就能得到一个标准的markdown接口文档

```xml
<dependency>
    <groupId>com.github.shalousun</groupId>
    <artifactId>common-util</artifactId>
    <version>1.4</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.github.shalousun</groupId>
    <artifactId>smart-doc</artifactId>
    <version>1.5</version>
    <scope>test</scope>
</dependency>
```

```java
import com.power.common.util.DateTimeUtil;
import com.power.common.util.FileUtil;
import com.power.doc.builder.ApiDocBuilder;
import com.power.doc.builder.SourceBuilder;
import com.power.doc.model.ApiConfig;
import com.power.doc.model.ApiDoc;
import com.power.doc.model.CustomRespField;
import com.power.doc.model.SourcePath;
import org.junit.Test;

import java.util.ArrayList;
import java.util.List;

/**
 * Description: smart-doc api文档生成
 *
 * @author zuogangju
 * @version V1.0
 * @date 2018/10/25 12:41
 */
public class ApiDocTest {
    /**
     * 生成的文件路径
     */
    private static final String MD_PATH = "D:\\work\\pages\\docs\\projects\\";
    /**
     * 生成的文件名称
     */
    private static final List<String> fileNameList;
    /**
     * 替换的内容
     */
    private static final String replaceContent = "smart-doc currently cannot provide examples of parameters for the RequestParam request mode.";


    static {
        fileNameList = new ArrayList<>();
        SourceBuilder sourceBuilder = new SourceBuilder(true);
        List<ApiDoc> apiDocList = sourceBuilder.getControllerApiData();
        for (ApiDoc apiDoc : apiDocList) {
            fileNameList.add(apiDoc.getName() + "Api.md");
        }
    }

    /**
     * 简单型接口，不需要指定请求头，并且项目是maven的.
     */
    @Test
    public void testBuilderControllersApiSimple() {
        //将生成的文档输出到MD_PATH目录下，严格模式下api-doc会检测Controller的接口注释
        ApiDocBuilder.builderControllersApi(MD_PATH, true);
        String rootPath = MD_PATH;
        for (String fileName : fileNameList) {
            String fileContent = FileUtil.getFileContent(rootPath + fileName);
            String finalStr = fileContent.replaceAll(replaceContent, "No Request-example");
            FileUtil.nioWriteFile(finalStr, rootPath + fileName);
        }

    }

    /**
     * 包括设置请求头，缺失注释的字段批量在文档生成期使用定义好的注释
     */
    @Test
    public void testBuilderControllersApi() {
        ApiConfig config = new ApiConfig();
//        config.setServerUrl("http://localhost:8080");
        config.setStrict(true);//true会严格要求注释，推荐设置true
//        config.setAllInOne(true);//true会将文档合并导出到一个markdown
        config.setOutPath(MD_PATH);
        // @since 1.2,如果不配置该选项，则默认匹配全部的controller,
        // 如果需要配置有多个controller可以使用逗号隔开
        config.setPackageFilters("com.unionpay.cloudatlas.schweb.controller");
        //不指定SourcePaths默认加载代码为项目src/main/java下的,如果项目的某一些实体来自外部代码可以一起加载
        config.setSourcePaths(
                SourcePath.path().setDesc("本项目代码").setPath("src/main/java")
                //  SourcePath.path().setPath("E:\\Test\\Mybatis-PageHelper-master\\src\\main\\java"),
                // SourcePath.path().setDesc("加载项目外代码").setPath("E:\\ApplicationPower\\ApplicationPower\\Common-util\\src\\main\\java")
        );

        //设置请求头，如果没有请求头，可以不用设置
//        config.setRequestHeaders(
//                ApiReqHeader.header().setName("access_token").setType("string").setDesc("Basic auth credentials"),
//                ApiReqHeader.header().setName("user_uuid").setType("string").setDesc("User Uuid key")
//        );
        //对于外部jar的类，编译后注释会被擦除，无法获取注释，但是如果量比较多请使用setSourcePaths来加载外部代码
        //如果有这种场景，则自己添加字段和注释，api-doc后期遇到同名字段则直接给相应字段加注释
        config.setCustomResponseFields(
                CustomRespField.field().setName("succ").setDesc("成功返回true,失败返回false"),
                CustomRespField.field().setName("msg").setDesc("接口响应信息"),
                CustomRespField.field().setName("data").setDesc("接口响应数据"),
                CustomRespField.field().setName("code").setValue("0").setDesc("响应代码")
        );

        //设置项目错误码列表，设置自动生成错误列表,
//        List<ApiErrorCode> errorCodeList = new ArrayList<>();
//        for(ErrorCodeEnum codeEnum: ErrorCodeEnum.values()){
//            ApiErrorCode errorCode = new ApiErrorCode();
//            errorCode.setValue(codeEnum.getCode()).setDesc(codeEnum.getDesc());
//            errorCodeList.add(errorCode);
//        }
        //如果没需要可以不设置
//        config.setErrorCodes(errorCodeList);

        long start = System.currentTimeMillis();
        ApiDocBuilder.builderControllersApi(config);
        long end = System.currentTimeMillis();
        DateTimeUtil.printRunTime(end, start);


        String rootPath = MD_PATH;
        for (String fileName : fileNameList) {
            String fileContent = FileUtil.getFileContent(rootPath + fileName);
            String finalStr = fileContent.replaceAll(replaceContent, "No Request-example");
            FileUtil.nioWriteFile(finalStr, rootPath + fileName);
        }
    }
}

```