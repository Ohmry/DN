# Spring
- [Spring](#spring)
  - [배치에서 Step 나누는 방법](#배치에서-step-나누는-방법)

## 배치에서 Step 나누는 방법

```xml
<job id="cms003.CmsOthcomCouponPublishJob" xmlns="http://www.springframework.org/schema/batch" restartable="true" >
  <step id="cms003.prepared" next="cms003.executed">
    <tasklet ref="CmsOthcomCouponPublishPreparedTasklet"/>
  </step>

  <step id="cms003.executed">
    <tasklet ref="CmsOthcomCouponPublishTasklet"/>
  </step>
</job>

<bean id="CmsOthcomCouponPublishPreparedTasklet" class="batchJobs.sm.st.cms.cms003.CmsOthcomCouponPublishPreparedTasklet" scope="step"></bean>
<bean id="CmsOthcomCouponPublishTasklet" class="batchJobs.sm.st.cms.cms003.CmsOthcomCouponPublishTasklet" scope="step"></bean>
```