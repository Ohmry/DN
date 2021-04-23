# Spring
- [Spring](#spring)
  - [배치에서 Step 나누는 방법](#배치에서-step-나누는-방법)
  - [JUnit에서 @After와 @AfterClass의 차이점](#junit에서-after와-afterclass의-차이점)

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

## JUnit에서 @After와 @AfterClass의 차이점
참고 사이트 [java - JUnit @Before 및 @After 모든 테스트 전후에 실행](https://pythonq.com/so/java/806111)

```
이것이 @Before와 @After의 정상적인 동작입니다. 예를 들어, @Before의 문서를 인용하면 :


@Before로 public void 메소드에 주석을 달면 해당 메소드가 Test 메소드보다 먼저 실행됩니다.


모든 테스트 전후에 한 번만 메소드를 실행하려면 @BeforeClass 및 @AfterClass를 사용할 수 있습니다. @BeforeClass 문서를 인용하면 다음과 같습니다.


@BeforeClass로 public static void no-arg 메소드에 주석을 달면 클래스의 테스트 메소드보다 한 번 실행됩니다.
```