## jpa 分页

```java
        PageRequest pageRequest = new PageRequest(jobInfo.getOffset(), jobInfo.getLimit());
        Page<JobInfo> pageInfo = jobInfoRepository.findAll(new Specification<JobInfo>() {
            @Override
            public Predicate toPredicate(Root<JobInfo> root, CriteriaQuery<?> query, CriteriaBuilder cb) {
                List<Predicate> list = new ArrayList<>();
                String jobName = jobInfo.getJobName();
                if (StringUtils.isNotBlank(jobName)) {
                    list.add(cb.like(root.get("jobName").as(String.class), "%" + jobName + "%"));
                }
                String jobDesc = jobInfo.getJobDesc();
                if (StringUtils.isNotBlank(jobDesc)) {
                    list.add(cb.equal(root.get("jobDesc").as(String.class), "%" + jobDesc + "%"));
                }
                String isCubeSql = jobInfo.getIsCubeSql();
                if (StringUtils.isNotBlank(isCubeSql)) {
                    list.add(cb.equal(root.get("isCubeSql").as(String.class), isCubeSql));
                }
                Integer isModel = jobInfo.getIsModel();
                if (isModel != null) {
                    list.add(cb.equal(root.get("isModel").as(String.class), isModel));
                }
                String jobStatus = jobInfo.getJobStatus();
                if (StringUtils.isNotBlank(jobStatus)) {
                    list.add(cb.equal(root.get("jobStatus").as(String.class), jobStatus));
                }
                list.add(cb.equal(root.get("isDelete").as(Integer.class), 0));

                Predicate[] p = new Predicate[list.size()];
                return cb.and(list.toArray(p));
            }
        }, pageRequest);
        return pageInfo.getContent();

```
