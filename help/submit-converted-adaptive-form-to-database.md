---
title: JSON 스키마와 함께 변환된 적응형 양식을 데이터베이스로 전송
description: 양식 데이터 모델을 만들고 AEM 워크플로우에서 참조하여 JSON 스키마와 함께 변환된 적응형 양식을 데이터베이스에 제출합니다.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: b879a0ddecd5370c754dfe9e1bf33121dd5ecc97

---


# AEM 워크플로우를 사용하여 적응형 양식 통합 {#submit-forms-to-database-using-forms-portal}

자동화된 양식 변환 서비스를 사용하면 비대화형 PDF 양식, Acro Form 또는 XFA 기반 PDF 양식을 적응형 양식으로 변환할 수 있습니다. 변환 프로세스를 시작하는 동안 데이터 바인딩을 사용하거나 사용하지 않고 적응형 양식을 생성할 수 있습니다.

데이터 바인딩 없이 적응형 양식을 생성하도록 선택하는 경우 변환 후 변환된 적응형 양식을 양식 데이터 모델, XML 스키마 또는 JSON 스키마와 통합할 수 있습니다. 양식 데이터 모델의 경우 적응형 양식 필드를 양식 데이터 모델과 수동으로 바인딩해야 합니다. 그러나 데이터 바인딩으로 응용 양식을 생성하는 경우 전환 서비스는 적응형 양식을 JSON 스키마와 자동으로 연결하고 적응형 양식과 JSON 스키마로 사용할 수 있는 필드 간에 데이터 바인딩을 만듭니다. 그런 다음 적응형 양식을 원하는 데이터베이스와 통합하고, 양식의 데이터를 채우고, 데이터베이스에 제출할 수 있습니다. 마찬가지로, 데이터베이스와 성공적으로 통합한 후 변환된 적응형 양식의 필드를 구성하여 데이터베이스에서 값을 검색하고 적응형 양식 필드를 미리 채울 수 있습니다.

다음 그림은 변환된 응용 양식을 데이터베이스와 통합하는 여러 단계를 설명합니다.

![데이터베이스 통합](assets/integrate-adaptive-form-with-database.png)

이 문서에서는 이러한 모든 통합 단계를 성공적으로 실행하기 위한 단계별 지침을 설명합니다.

## 전제 조건 {#pre-requisites}

* 최신 AEM 6.5 서비스 팩이 포함된 AEM 6.5 작성자 인스턴스
* 최신 버전의 AEM Forms 추가 기능 패키지
* [자동화된 양식 변환 서비스](configure-service.md)
* 통합할 데이터베이스입니다. 샘플 구현에서 사용되는 데이터베이스는 MySQL 5.6.24입니다.그러나 변환된 적응형 양식을 원하는 데이터베이스와 통합할 수 있습니다.

## 샘플 적응형 양식 {#sample-adaptive-form}

변환된 적응형 양식을 AEM 작업 과정을 사용하여 데이터베이스와 통합하는 사용 사례를 실행하려면 다음 샘플 PDF 파일을 다운로드하십시오.

다음을 사용하여 문의 양식 샘플을 다운로드할 수 있습니다.

[파일 가져오기](assets/sample_contact_us_form.pdf)

PDF 파일은 자동화된 양식 변환 서비스에 대한 입력으로 사용됩니다. 서비스는 이 파일을 응용 형식으로 변환합니다. 다음 이미지는 샘플 연락처 양식을 PDF 형식으로 보여 줍니다.

![샘플 대출 신청서](assets/sample_contact_us_form.png)

## mysql-connector-java-5.1.39-bin.jar 파일 설치 {#install-mysql-connector-java-file}

모든 작성자 및 게시 인스턴스에 대해 다음 단계를 수행하여 mysql-connector-java-5.1.39-bin.jar 파일을 설치합니다.

1. com.mysql.jdbc 패키지로 이동하여 `http://server:port/system/console/depfinder` 검색합니다.
1. 내보내기 기준 열에서 패키지가 번들에 의해 내보내졌는지 확인합니다. 패키지를 번들에 의해 내보내지 않은 경우 계속 진행합니다.
1. 탐색하여 `http://server:port/system/console/bundles` 클릭합니다 **[!UICONTROL Install/Update]**.
1. 을 클릭하고 **[!UICONTROL Choose File]** 탐색하여 mysql-connector-java-5.1.39-bin.jar 파일을 선택합니다. 확인란을 **[!UICONTROL Start Bundle]** 선택하고 **[!UICONTROL Refresh Packages]** 선택합니다.
1. 또는 **[!UICONTROL Install]** 을 **[!UICONTROL Update]**&#x200B;클릭합니다. 완료되면 서버를 다시 시작합니다.
1. (Windows 전용) 운영 체제의 시스템 방화벽을 해제합니다.

## 양식 모델에 대한 데이터 준비 {#prepare-data-for-form-model}

AEM Forms 데이터 통합을 사용하여 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 변환 프로세스를 사용하여 적응형 양식을 생성한 후 양식 데이터 모델, XSD 또는 JSON 스키마를 기반으로 양식 모델을 정의할 수 있습니다. 데이터베이스, Microsoft Dynamics 또는 다른 타사 서비스를 사용하여 양식 데이터 모델을 만들 수 있습니다.

이 자습서에서는 MySQL 데이터베이스를 소스로 사용하여 양식 데이터 모델을 만듭니다. 데이터베이스에 스키마를 만들고 적응형 형식으로 **사용 가능한** 필드를 기반으로 스키마에 동시성 테이블을 추가합니다.

![샘플 데이터 mysql](assets/db_entries_sample_form.png)

다음 DDL 문을 사용하여 데이터베이스에 **동시 테이블을 만들** 수 있습니다.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## AEM 인스턴스와 데이터베이스 간의 연결 구성 {#configure-connection-between-aem-instance-and-database}

AEM 인스턴스와 MYSQL 데이터베이스 간의 연결을 만들려면 다음 구성 단계를 수행하십시오.

1. 의 AEM 웹 콘솔 구성 페이지로 `http://server:port/system/console/configMgr`이동합니다.
1. 찾기 및 클릭하여 웹 콘솔 구성에서 편집 **[!UICONTROL Apache Sling Connection Pooled DataSource]** 모드로 엽니다. 다음 표에 설명된 대로 속성 값을 지정합니다.

   <table> 
    <tbody> 
    <tr> 
    <th><strong>속성</strong></th> 
    <th><strong>값</strong></th> 
    </tr> 
    <tr> 
    <td><p>데이터 소스 이름</p></td> 
    <td><p>데이터 소스 풀에서 드라이버를 필터링하기 위한 데이터 소스 이름입니다.</p></td>
    </tr>
    <tr> 
    <td><p>JDBC 드라이버 클래스</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC 연결 URI</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>사용자 이름</p></td> 
    <td><p>데이터베이스 테이블에서 인증 및 작업을 수행할 사용자 이름</p></td>
    </tr>
    <tr> 
    <td><p>암호</p></td> 
    <td><p>사용자 이름과 연결된 암호</p></td>
    </tr>
    <tr> 
    <td><p>트랜잭션 격리</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>최대 활성 연결</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>최대 유휴 연결</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>최소 유휴 연결</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>초기 크기</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>최대 대기 시간</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>대여시 테스트</p></td> 
    <td><p>선택됨</p></td>
    </tr>
     <tr> 
    <td><p>유휴 상태 테스트</p></td> 
    <td><p>선택됨</p></td>
    </tr>
     <tr> 
    <td><p>유효성 검사 쿼리</p></td> 
    <td><p>예 값은 SELECT 1(mysql), dual(oracle), SELECT 1(MS Sql Server)(validationQuery)입니다.</p></td>
    </tr>
     <tr> 
    <td><p>유효성 검사 쿼리 시간 초과</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

## Create form data model {#create-form-data-model}

MYSQL을 데이터 소스로 구성한 후에는 다음 단계를 수행하여 양식 데이터 모델을 만듭니다.

1. AEM 작성자 인스턴스에서 **[!UICONTROL Forms]** >으로 이동합니다 **[!UICONTROL Data Integrations]**.

1. 탭하기 **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. 마법사에서 **[!UICONTROL Create Form Data Model]** workflow_submit **** 를 양식 데이터 모델의 이름으로 지정합니다. 탭하기 **[!UICONTROL Next]**.

1. 이전 섹션에서 구성한 MYSQL 데이터 소스를 선택하고 을 **[!UICONTROL Create]**&#x200B;누릅니다.

1. 왼쪽 창에 나열된 데이터 소스를 **[!UICONTROL Edit]** 탭하여 확장하여 **동시 표** , **[!UICONTROL get]**&#x200B;서비스를 선택한 다음 **[!UICONTROL insert]** 을 탭합니다 **[!UICONTROL Add Selected]**.

   ![샘플 데이터 mysql](assets/fdm_details_workfdlow_submit.png)

1. 오른쪽 창에서 데이터 모델 개체를 선택하고 을 **[!UICONTROL Edit Properties]**&#x200B;누릅니다. 및 **[!UICONTROL get]** 드롭다운 **[!UICONTROL insert]** 목록에서 **[!UICONTROL Read Service]** **[!UICONTROL Write Service]** 을 선택합니다. 읽기 서비스의 인수를 지정하고 **[!UICONTROL Done]**&#x200B;탭합니다.

1. 탭에서 **[!UICONTROL Services]** 서비스를 선택하고 을 **[!UICONTROL get]** **[!UICONTROL Edit Properties]**&#x200B;누릅니다. 토글을 **[!UICONTROL Output Model Object]**&#x200B;선택하고 **[!UICONTROL Return array]** 비활성화한 다음 을 탭합니다 **[!UICONTROL Done]**.

1. 서비스를 **[!UICONTROL Insert]** 선택하고 을 누릅니다 **[!UICONTROL Edit Properties]**. 을 **[!UICONTROL Input Model Object]** 선택하고 을 누릅니다 **[!UICONTROL Done]**.

1. 양식 데이터 모델을 **[!UICONTROL Save]** 저장하려면 을 누릅니다.

다음을 사용하여 샘플 양식 데이터 모델을 다운로드할 수 있습니다.

[파일 가져오기](assets/DownloadedFormsPackage_1497728018502500.zip)

## JSON 바인딩을 사용하여 적응형 양식 생성 {#generate-adaptive-forms-with-json-binding}

자동 양식 [변환 서비스를 사용하여 연락처 양식을](convert-existing-forms-to-adaptive-forms.md) 데이터 [바인딩이 있는 적응형 양식으로](#sample-adaptive-form) 변환할수 있습니다. 적응형 양식을 생성하는 동안 **[!UICONTROL Generate adaptive form(s) without data bindings]** 확인란을 선택하지 않아야 합니다.

![JSON 바인딩을 사용한 적응형 양식](assets/generate_af_with_data_bindings.png)

의 **폴더에서 사용할 수 있는 변환된 연락처 양식을** 선택하고 **[!UICONTROL output]** 을 **[!UICONTROL Forms & Documents]** **[!UICONTROL Edit]**&#x200B;누릅니다. 적응형 양식 필드를 **[!UICONTROL Preview]**&#x200B;누르고 값을 입력한 다음 탭합니다 **[!UICONTROL Submit]**.

crx- **repository에** 로그온하고 */content/forms/fp/admin/submit/data* 로 이동하여 제출된 값을 JSON 형식으로 봅니다. 변환된 Contact Us 적응형 양식을 제출할 때 JSON 형식의 샘플 **데이터는 다음과** 같습니다.

```json
{
  "afData": {
    "afUnboundData": {
      "data": {}
    },
    "afBoundData": {
      "data": {
        "name1": "Gloria",
        "email": "abc@xyz.com",
        "phone_number": "2346578965",
        "issue_description": "Test message"
      }
    },
    "afSubmissionInfo": {
      "computedMetaInfo": {},
      "stateOverrides": {},
      "signers": {},
      "afPath": "/content/dam/formsanddocuments/docs_conversion/output/sample_form_json",
      "afSubmissionTime": "20191204014007"
    }
  }
}
```

이 데이터를 처리하고 이전 섹션에서 만든 양식 데이터 모델을 사용하여 MYSQL 데이터베이스에 제출할 수 있는 워크플로우 모델을 만들어야 합니다.

## JSON 데이터를 처리하는 워크플로우 모델 만들기 {#create-workflow-model}

다음 단계를 수행하여 응용 양식 데이터를 데이터베이스에 제출하는 워크플로우 모델을 생성합니다.

1. 워크플로우 모델 콘솔을 엽니다. 기본 URL은 `https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`입니다.

1. 을 **[!UICONTROL Create]**&#x200B;선택한 다음 **[!UICONTROL Create Model]**&#x200B;선택합니다. 대화 상자가 **[!UICONTROL Add Workflow Model]** 나타납니다.

1. 및 **[!UICONTROL Title]** 를 **[!UICONTROL Name]** 입력합니다(선택 사항). 예: **workflow_json_submit**. 을 **[!UICONTROL Done]** 눌러 모델을 생성합니다.

1. 워크플로우 모델을 선택하고 을 눌러 편집 모드에서 모델을 **[!UICONTROL Edit]** 엽니다. +를 누르고 워크플로우 모델에 **[!UICONTROL Invoke Form Data Model Service]** 단계를 추가합니다.

1. 단계를 **[!UICONTROL Invoke Form Data Model Service]** 누르고 구성을 ![누릅니다](assets/configure_icon.png).

1. 탭에서 **[!UICONTROL Form Data Model]** 필드에 만든 양식 데이터 모델을 선택하고 **[!UICONTROL Form Data Model path]** 드롭다운 목록에서 **[!UICONTROL insert]** **[!UICONTROL Service]** 선택합니다.

1. 이 **[!UICONTROL Input for Service]** 탭에서 드롭다운 목록에서 **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]** 선택한 다음 **[!UICONTROL Map input fields from input JSON]** 확인란을 선택하고 **[!UICONTROL Relative to payload]**&#x200B;선택한 다음 **data.xml** 을 **[!UICONTROL Select input JSON document using]** 필드의 값으로 제공합니다.

1. 섹션에서 양식 데이터 모델 인수에 대해 다음 값을 **[!UICONTROL Service Arguments]** 제공합니다.

   ![양식 데이터 모델 서비스 호출](assets/invoke_form_data_model_service.png)

   양식 데이터 모델 필드(예: contactus 점 이름)는 **aafData.afBoundData.data.name1**(제출된 적응형 양식의 JSON 스키마 바인딩)에 매핑됩니다.

## 적응형 양식 제출 구성 {#configure-adaptive-form-submission}

다음 단계를 실행하여 이전 섹션에서 만든 워크플로우 모델에 적응형 양식을 제출합니다.

1. 에서 **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 연락처 양식을 **[!UICONTROL Forms & Documents]** 선택하고 을 **[!UICONTROL Edit]**&#x200B;누릅니다.

1. [구성]을 탭한 **[!UICONTROL Form Container]** 다음 탭하여 적응형 양식 속성을 ![엽니다](assets/configure_icon.png).

1. 이 **[!UICONTROL Submission]** 섹션의 드롭다운 목록에서 **[!UICONTROL Invoke an AEM workflow]** 선택한 **[!UICONTROL Submit Action]** 다음 이전 섹션에서 만든 워크플로우 모델을 선택하고 **필드에** data.xml **[!UICONTROL Data File Path]** 을 지정합니다.

1. 저장을 ![눌러](assets/save_icon.png) 속성을 저장합니다.

1. 적응형 양식 필드를 **[!UICONTROL Preview]**&#x200B;누르고 값을 입력한 다음 탭합니다 **[!UICONTROL Submit]**. 이제 제출된 값이 crx- **repository**&#x200B;대신 MYSQL 데이터베이스 테이블에 표시됩니다.

## 데이터베이스에서 값을 미리 채우도록 적응형 양식 구성

다음 단계를 수행하여 테이블에 정의된 기본 키를 기반으로 MYSQL 데이터베이스에서 값을 미리 채우도록 적응형 양식을 구성합니다(이 경우 이메일).

1. 적응형 **양식의 이메일** 필드를 누르고 규칙 ![편집을 누릅니다](assets/edit-rules.png).

1. 섹션의 **[!UICONTROL Create]** 드롭다운 목록에서 **[!UICONTROL is changed]** 을 탭하고 선택합니다 **[!UICONTROL Select State]** **[!UICONTROL When]** .

1. 섹션에서 이 **[!UICONTROL Then]** 문서의 이전 섹션에서 만든 양식 데이터 모델의 서비스로 **[!UICONTROL Invoke Service]** 선택하고 **가져옵니다** .

1. 양식 데이터 모델의 **섹션 및 필드 세 개, 이름,****[!UICONTROL Input]** 전화번호 **,** Rest ****&#x200B;전화 번호, RestTelephone 설명 섹션 내에서 전자 메일을 **** **[!UICONTROL Output]** 선택합니다. 을 **[!UICONTROL Done]** 눌러 설정을 저장합니다.

   ![이메일 자동 채우기 설정 구성](assets/email_prefill_settings.png)

   따라서 MYSQL 데이터베이스의 기존 전자 메일 항목을 기반으로 응용 양식 **[!UICONTROL Preview]** 모드에서 나머지 세 필드의 값을 미리 채울 수 있습니다. 예를 들어, 전자 메일 **필드(이 문서의** 양식 준비 데이터 모델 [섹션의 기존 데이터를 기반으로 함)에 aya.tan@xyz.com을 지정하고](#prepare-data-for-form-model) 필드 밖으로 탭하면 나머지 부분, 이름, **전화 번호**, 응용 ******** 프로그램 번호, 전화 번호 및 발행물 설명 양식이 자동으로 표시됩니다.

다음을 사용하여 변환된 적응형 양식 샘플을 다운로드할 수 있습니다.

[파일 가져오기](assets/DownloadedFormsPackage_1498226829041200.zip)
