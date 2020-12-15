---
title: 변환된 적응형 양식을 JSON 스키마와 함께 데이터베이스에 제출
description: 양식 데이터 모델을 만들고 AEM 워크플로우에서 참조하는 JSON 스키마로 변환된 적응형 양식을 데이터베이스에 제출합니다.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: c552f4073ac88ca9016a746116a27a5898df7f7d
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 2%

---


# AEM 워크플로우를 사용하여 적응형 양식과 데이터베이스 통합 {#submit-forms-to-database-using-forms-portal}

automated forms conversion 서비스를 사용하면 비대화형 PDF 양식, Acro Form 또는 XFA 기반 PDF 양식을 적응형 양식으로 변환할 수 있습니다. 변환 프로세스를 시작하는 동안 데이터 바인딩이 있거나 없는 응용 양식을 생성하는 옵션이 있습니다.

데이터 바인딩 없이 적응형 양식을 생성하도록 선택하는 경우 변환된 적응형 양식을 변환 후 양식 데이터 모델, XML 스키마 또는 JSON 스키마에 통합할 수 있습니다. 양식 데이터 모델의 경우 양식 데이터 모델로 적응형 양식 필드를 수동으로 바인딩해야 합니다. 그러나 데이터 바인딩으로 응용 양식을 생성하는 경우 변환 서비스는 자동으로 적응형 양식을 JSON 스키마와 연결하며 적응형 양식과 JSON 스키마에서 사용할 수 있는 필드 간에 데이터 바인딩을 만듭니다. 그런 다음 적응형 양식을 원하는 데이터베이스와 통합하고, 양식에 데이터를 채우고, 데이터베이스에 제출할 수 있습니다. 마찬가지로, 데이터베이스와 성공적으로 통합한 후 변환된 적응형 양식의 필드를 구성하여 데이터베이스에서 값을 검색하고 적응형 양식 필드를 미리 채울 수 있습니다.

다음 그림은 변환된 응용 양식을 데이터베이스와 통합하는 여러 단계를 보여 줍니다.

![데이터베이스 통합](assets/integrate-adaptive-form-with-database.png)

이 문서에서는 이러한 모든 통합 단계를 성공적으로 실행하기 위한 단계별 지침에 대해 설명합니다.

## 전제 조건 {#pre-requisites}

* AEM 6.4 또는 6.5 작성자 인스턴스 설정
* AEM 인스턴스에 대해 [최신 서비스 팩](https://helpx.adobe.com/kr/experience-manager/aem-releases-updates.html)을 설치합니다.
* 최신 버전의 AEM Forms Add-on 패키지
* [Automated forms conversion 서비스](configure-service.md) 구성
* 데이터베이스를 설정합니다. 샘플 구현에 사용되는 데이터베이스는 MySQL 5.6.24입니다. 그러나 변환된 적응형 양식을 원하는 데이터베이스와 통합할 수 있습니다.

## 샘플 적응형 양식 {#sample-adaptive-form}

AEM 작업 과정을 사용하여 변환된 적응형 양식을 데이터베이스와 통합하는 사용 사례를 실행하려면 다음 샘플 PDF 파일을 다운로드합니다.

다음을 사용하여 문의 양식 샘플을 다운로드할 수 있습니다.

[파일 가져오기](assets/sample_contact_us_form.pdf)

PDF 파일은 Automated forms conversion 서비스에 대한 입력 역할을 합니다. 서비스는 이 파일을 응용 형식으로 변환합니다. 다음 이미지는 샘플 연락처 양식을 PDF 형식으로 보여 줍니다.

![샘플 대출 신청서](assets/sample_contact_us_form.png)

## mysql-connector-java-5.1.39-bin.jar 파일 {#install-mysql-connector-java-file} 설치

모든 작성자 및 게시 인스턴스에서 mysql-connector-java-5.1.39-bin.jar 파일을 설치하려면 다음 단계를 수행합니다.

1. `http://server:port/system/console/depfinder`으로 이동하여 com.mysql.jdbc 패키지를 검색합니다.
1. 내보내기 기준 열에서 패키지가 번들에 의해 내보내졌는지 확인합니다. 패키지를 번들에 의해 내보내지 않으면 계속합니다.
1. `http://server:port/system/console/bundles`으로 이동하고 **[!UICONTROL Install/Update]**&#x200B;을 클릭합니다.
1. **[!UICONTROL Choose File]**&#x200B;을 클릭하고 mysql-connector-java-5.1.39-bin.jar 파일을 찾아 선택합니다. 또한 **[!UICONTROL Start Bundle]** 및 **[!UICONTROL Refresh Packages]** 확인란을 선택합니다.
1. **[!UICONTROL Install]** 또는 **[!UICONTROL Update]**&#x200B;을 클릭합니다. 완료되면 서버를 다시 시작합니다.
1. (Windows 전용) 운영 체제의 시스템 방화벽을 해제합니다.

## 양식 모델 {#prepare-data-for-form-model} 데이터 준비

AEM Forms 데이터 통합을 사용하여 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 변환 프로세스를 사용하여 적응형 양식을 생성한 후 양식 데이터 모델, XSD 또는 JSON 스키마를 기반으로 양식 모델을 정의할 수 있습니다. 데이터베이스, Microsoft Dynamics 또는 다른 타사 서비스를 사용하여 양식 데이터 모델을 만들 수 있습니다.

이 자습서에서는 MySQL 데이터베이스를 소스로 사용하여 양식 데이터 모델을 만듭니다. 데이터베이스에서 스키마를 만들고 적응형 형식으로 사용할 수 있는 필드를 기반으로 **contacuity** 테이블을 스키마에 추가합니다.

![샘플 데이터 mysql](assets/db_entries_sample_form.png)

다음 DDL 문을 사용하여 데이터베이스에 **contacuts** 테이블을 만들 수 있습니다.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## AEM 인스턴스와 데이터베이스 {#configure-connection-between-aem-instance-and-database} 간의 연결 구성

AEM 인스턴스와 MYSQL 데이터베이스 간에 연결을 만들려면 다음 구성 단계를 수행합니다.

1. `http://server:port/system/console/configMgr`의 AEM 웹 콘솔 구성 페이지로 이동합니다.
1. 찾기 및 클릭하여 웹 콘솔 구성에서 편집 모드에서 **[!UICONTROL Apache Sling Connection Pooled DataSource]**&#x200B;을(를) 엽니다. 다음 표에 설명된 대로 속성 값을 지정합니다.

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
    <td><p>jdbc:mysql://[호스트]:[포트]/[스키마_이름]</p></td>
    </tr>
    <tr> 
    <td><p>사용자 이름</p></td> 
    <td><p>데이터베이스 테이블에 대해 인증하고 작업을 수행하는 사용자 이름</p></td>
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
    <td><p>최대 활성 연결 수</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>최대 유휴 연결 수</p></td> 
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
    <td><p>예 값은 SELECT 1(mysql), dual(oracle) 중에서 1을, SELECT 1(MS Sql Server)(validationQuery)입니다.</p></td>
    </tr>
     <tr> 
    <td><p>유효성 검사 쿼리 시간 초과</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

## 양식 데이터 모델 {#create-form-data-model} 만들기

MYSQL을 데이터 소스로 구성한 후에는 다음 단계를 수행하여 양식 데이터 모델을 만듭니다.

1. AEM 작성자 인스턴스에서 **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**&#x200B;로 이동합니다.

1. 탭하기 **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. **[!UICONTROL Create Form Data Model]** 마법사에서 양식 데이터 모델의 이름으로 **workflow_submit**&#x200B;를 지정합니다. 탭하기 **[!UICONTROL Next]**.

1. 이전 섹션에서 구성한 MYSQL 데이터 소스를 선택하고 **[!UICONTROL Create]**&#x200B;을 누릅니다.

1. **[!UICONTROL Edit]**&#x200B;을(를) 누르고 왼쪽 창에 나열된 데이터 소스를 확장하여 **contacuity** 표, **[!UICONTROL get]** 및 **[!UICONTROL insert]** 서비스를 선택하고 **[!UICONTROL Add Selected]**&#x200B;를 누릅니다.

   ![샘플 데이터 mysql](assets/fdm_details_workfdlow_submit.png)

1. 오른쪽 창에서 데이터 모델 개체를 선택하고 **[!UICONTROL Edit Properties]**&#x200B;을 누릅니다. **[!UICONTROL Read Service]** 및 **[!UICONTROL Write Service]** 드롭다운 목록에서 **[!UICONTROL get]** 및 **[!UICONTROL insert]**&#x200B;을 선택합니다. 읽기 서비스의 인수를 지정하고 **[!UICONTROL Done]**&#x200B;을(를) 누릅니다.

1. **[!UICONTROL Services]** 탭에서 **[!UICONTROL get]** 서비스를 선택하고 **[!UICONTROL Edit Properties]**&#x200B;를 누릅니다. **[!UICONTROL Output Model Object]**&#x200B;을 선택하고 **[!UICONTROL Return array]** 토글을 비활성화한 다음 **[!UICONTROL Done]**&#x200B;를 누릅니다.

1. **[!UICONTROL Insert]** 서비스를 선택하고 **[!UICONTROL Edit Properties]**&#x200B;을 누릅니다. **[!UICONTROL Input Model Object]**&#x200B;을 선택하고 **[!UICONTROL Done]**&#x200B;을 누릅니다.

1. 양식 데이터 모델을 저장하려면 **[!UICONTROL Save]**&#x200B;을 누릅니다.

다음을 사용하여 샘플 양식 데이터 모델을 다운로드할 수 있습니다.

[파일 가져오기](assets/DownloadedFormsPackage_1497728018502500.zip)

## JSON 바인딩 {#generate-adaptive-forms-with-json-binding}을 사용하여 적응형 양식 생성

[Automated forms conversion 서비스를 사용하여 [연락처 양식](#sample-adaptive-form)을 데이터 바인딩이 있는 응용 양식으로 변환합니다. ](convert-existing-forms-to-adaptive-forms.md) 적응형 양식을 생성하는 동안 **[!UICONTROL Generate adaptive form(s) without data bindings]** 확인란을 선택하지 않아야 합니다.

![JSON 바인딩이 있는 적응형 양식](assets/generate_af_with_data_bindings.png)

**[!UICONTROL Forms & Documents]**&#x200B;의 **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 **연락처 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;를 탭합니다. **[!UICONTROL Preview]**&#x200B;을(를) 누르고 적응형 양식 필드에 값을 입력한 다음 **[!UICONTROL Submit]**&#x200B;을(를) 누릅니다.

**crx-repository**&#x200B;에 로그온하고 */content/forms/fp/admin/submit/data*&#x200B;으로 이동하여 제출된 값을 JSON 형식으로 확인합니다. 다음은 변환된 **Contact Us** 적응형 양식을 제출할 때 JSON 형식의 샘플 데이터입니다.

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

이전 섹션에서 만든 양식 데이터 모델을 사용하여 이 데이터를 처리하고 MYSQL 데이터베이스에 제출할 수 있는 워크플로우 모델을 만들어야 합니다.

## JSON 데이터 {#create-workflow-model} 처리를 위한 워크플로우 모델 만들기

응용 양식 데이터를 데이터베이스에 제출할 워크플로우 모델을 만들려면 다음 단계를 수행하십시오.

1. 워크플로우 모델 콘솔을 엽니다. 기본 URL은 `https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.

1. **[!UICONTROL Create]**&#x200B;을 선택하고 **[!UICONTROL Create Model]**&#x200B;을 선택합니다. **[!UICONTROL Add Workflow Model]** 대화 상자가 나타납니다.

1. **[!UICONTROL Title]** 및 **[!UICONTROL Name]**(선택 사항)을 입력합니다. 예: **workflow_json_submit**. **[!UICONTROL Done]**&#x200B;을 눌러 모델을 생성합니다.

1. 워크플로우 모델을 선택하고 **[!UICONTROL Edit]**&#x200B;을 눌러 편집 모드에서 모델을 엽니다. +를 누르고 워크플로우 모델에 **[!UICONTROL Invoke Form Data Model Service]** 단계를 추가합니다.

1. **[!UICONTROL Invoke Form Data Model Service]** 단계를 누르고 ![구성](assets/configure_icon.png)을 누릅니다.

1. **[!UICONTROL Form Data Model]** 탭에서 **[!UICONTROL Form Data Model path]** 필드에서 만든 양식 데이터 모델을 선택하고 **[!UICONTROL Service]** 드롭다운 목록에서 **[!UICONTROL insert]**&#x200B;를 선택합니다.

1. **[!UICONTROL Input for Service]** 탭의 드롭다운 목록에서 **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]**&#x200B;을 선택하고 **[!UICONTROL Map input fields from input JSON]** 확인란을 선택하고 **[!UICONTROL Relative to payload]**&#x200B;을 선택한 다음 **[!UICONTROL Select input JSON document using]** 필드의 값으로 **data.xml**&#x200B;을 제공합니다.

1. **[!UICONTROL Service Arguments]** 섹션에서 양식 데이터 모델 인수에 다음 값을 제공합니다.

   ![양식 데이터 모델 서비스 호출](assets/invoke_form_data_model_service.png)

   양식 데이터 모델 필드(예: 행위법 점 이름)는 제출된 적응형 양식의 JSON 스키마 바인딩을 참조하는 **afData.afBoundData.data.name1**&#x200B;에 매핑됩니다.

## 적응형 양식 제출 구성 {#configure-adaptive-form-submission}

이전 섹션에서 만든 워크플로우 모델에 적응형 양식을 제출하려면 다음 단계를 수행합니다.

1. **[!UICONTROL Forms & Documents]**&#x200B;의 **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 연락처 양식을 선택하고 **[!UICONTROL Edit]**&#x200B;를 누릅니다.

1. **[!UICONTROL Form Container]**&#x200B;을 탭한 다음 ![구성](assets/configure_icon.png)을 탭하여 응용 양식 속성을 엽니다.

1. **[!UICONTROL Submission]** 섹션의 **[!UICONTROL Submit Action]** 드롭다운 목록에서 **[!UICONTROL Invoke an AEM workflow]**&#x200B;을 선택하고 이전 섹션에서 만든 워크플로우 모델을 선택한 다음 **[!UICONTROL Data File Path]** 필드에 **data.xml**&#x200B;을 지정합니다.

1. ![저장](assets/save_icon.png)을 눌러 속성을 저장합니다.

1. **[!UICONTROL Preview]**&#x200B;을(를) 누르고 적응형 양식 필드에 값을 입력한 다음 **[!UICONTROL Submit]**&#x200B;을(를) 누릅니다. 이제 제출된 값이 **crx-repository** 대신 MYSQL 데이터베이스 테이블에 표시됩니다.

## 데이터베이스의 값을 미리 채우기 위해 응용 양식 구성

테이블에 정의된 기본 키를 기반으로 MYSQL 데이터베이스에서 값을 프리필할 수 있도록 적응형 양식을 구성하려면 다음 단계를 수행하십시오(이 경우 전자 메일).

1. 적응형 양식의 **이메일** 필드를 누르고 ![규칙 편집](assets/edit-rules.png)을 누릅니다.

1. **[!UICONTROL Create]**&#x200B;을(를) 누르고 **[!UICONTROL When]** 섹션의 **[!UICONTROL Select State]** 드롭다운 목록에서 **[!UICONTROL is changed]**&#x200B;을 선택합니다.

1. **[!UICONTROL Then]** 섹션에서 **[!UICONTROL Invoke Service]** 및 **get**&#x200B;을 이 문서의 이전 섹션에 만든 양식 데이터 모델의 서비스로 선택합니다.

1. **[!UICONTROL Output]** 섹션에서 **전자 메일**&#x200B;을 선택하고 양식 데이터 모델의 나머지 세 필드( **이름**, **전화 번호** 및 **발행물 설명**)을 선택합니다. **[!UICONTROL Input]** **[!UICONTROL Done]**&#x200B;을 눌러 설정을 저장합니다.

   ![이메일 미리 채우기 설정 구성](assets/email_prefill_settings.png)

   따라서 MYSQL 데이터베이스의 기존 전자 메일 항목을 기준으로 응용 양식의 **[!UICONTROL Preview]** 모드에서 나머지 세 필드의 값을 미리 입력할 수 있습니다. 예를 들어 **전자 메일** 필드(이 아티클의 [양식 데이터 모델 준비](#prepare-data-for-form-model) 섹션에 있는 기존 데이터 기반)에 aya.tan@xyz.com을 지정하고 나머지 3개 필드, **이름**, **전화 번호** 및 **문제 description**&#x200B;은 적응형 양식에 자동으로 표시됩니다.

다음을 사용하여 변환된 적응형 양식을 다운로드할 수 있습니다.

[파일 가져오기](assets/DownloadedFormsPackage_1498226829041200.zip)
