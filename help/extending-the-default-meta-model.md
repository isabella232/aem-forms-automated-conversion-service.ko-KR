---
title: 기본 메타 모델 확장
seo-title: 기본 메타 모델 확장
description: 기본 메타 모델을 확장하여 조직에 맞는 패턴, 유효성 검사 및 개체를 추가하고 Automated forms conversion 서비스를 실행하는 동안 적응형 양식 필드에 구성을 적용합니다.
seo-description: 기본 메타 모델을 확장하여 조직에 맞는 패턴, 유효성 검사 및 개체를 추가하고 Automated forms conversion 서비스를 실행하는 동안 적응형 양식 필드에 구성을 적용합니다.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: 77bdb4e88194bd634dea125852ff2a897bc24678
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 1%

---


# 기본 메타 모델 확장 {#extend-the-default-meta-model}

automated forms conversion 서비스는 소스 양식에서 양식 개체를 식별하고 추출합니다. 의미론적 매퍼는 서비스가 추출된 개체가 응용 형식으로 표현되는 방식을 결정하는 데 도움이 됩니다. 예를 들어, 소스 양식에는 날짜를 나타내는 여러 가지 유형의 표현이 있을 수 있습니다. 의미론적 매퍼는 소스 양식의 날짜 양식 개체의 모든 표현을 응용 양식의 날짜 구성 요소와 매핑하는 데 도움이 됩니다. 또한 의미론적 매퍼에서는 전환 중에 유효성 검사, 규칙, 데이터 패턴, 도움말 텍스트 및 액세서빌러티 속성을 미리 구성하고 응용 양식 구성 요소에 적용할 수 있습니다.

![](assets/meta-model.gif)

메타 모델은 JSON 스키마입니다. 메타 모델로 시작하기 전에 JSON에 익숙한지 확인하십시오. JSON 형식으로 저장된 데이터를 작성, 편집 및 읽을 수 있는 경험이 있어야 합니다.

## 기본 메타 모델 {#default-meta-model}

automated forms conversion 서비스에는 기본 메타 모델이 있습니다. JSON 스키마이며 Automated forms conversion 서비스의 다른 구성 요소와 함께 Adobe 클라우드에 있습니다. 로컬 AEM 서버에서 메타 모델의 사본을 찾을 수 있습니다.http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json. 기본 스키마에 액세스하거나 다운로드하려면 [여기를 클릭](assets/global.schema.json)할 수도 있습니다.

메타 모델의 스키마는 https://schema.org/docs/schemas.html의 스키마 엔티티에서 파생됩니다. 개인, PostalAddress, LocalBusiness 및 https://schema.org에 정의된 더 많은 개체가 있습니다. 메타 모델의 모든 엔티티는 JSON 스키마 객체 유형을 준수합니다. 다음 코드는 샘플 메타 모델 구조를 나타냅니다.

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## 기본 메타 모델 {#download-the-default-meta-model} 다운로드

기본 메타 모델을 로컬 파일 시스템에 다운로드하려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에 로그인합니다.
1. **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **** **[!UICONTROL Meta Model]** 폴더로 이동합니다.
1. **[!UICONTROL global.schema.json]** 파일을 선택하고 **[!UICONTROL Download]**&#x200B;을 누릅니다. 다운로드 대화 상자가 나타납니다. **[!UICONTROL Download asset(s) as binary files]** 옵션을 선택합니다. 탭하기 **[!UICONTROL Download]**. 보관 파일이 다운로드됩니다.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## 메타 모델 {#understanding-the-meta-model} 이해

메타 모델은 엔티티가 포함된 JSON 스키마 파일을 참조합니다. JSON 스키마 파일의 모든 개체에는 이름과 ID가 포함됩니다. 각 엔터티에는 여러 속성이 포함될 수 있습니다. 엔티티와 해당 속성은 도메인에 따라 다를 수 있습니다. 키워드 및 필드 구성으로 스키마 파일을 늘려 적응형 양식 구성 요소에 스키마 속성을 매핑할 수 있습니다.

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

이 예제에서 **Event**&#x200B;는 **id**&#x200B;에 대한 값이 **Event**&#x200B;인 엔터티의 이름을 나타냅니다. 이벤트 엔터티에는 다음과 같은 여러 속성이 포함됩니다.

* startDate
* endDate
* 위치

메타 모델의 **allOf** 구문은 엔티티 간에 상속을 활성화합니다.

각 속성은 다음을 추가로 포함할 수 있습니다.

* [JSON 스키마 속성](#jsonschemaproperties)
* [생성된 적응형 양식 필드에 속성을 적용하는 키워드 기반 검색](#keywordsearch)
* [추가 속성](#additionalproperties)

![메타 모델 속성](assets/meta_model_elements.gif)

**aem:affKeyword**&#x200B;를 사용하여 참조한 키워드를 기준으로 전환 서비스는 소스 양식 필드에 대해 검색 작업을 수행합니다. 전환 서비스는 검색 조건을 충족하는 필드에 JSON 스키마 속성 및 추가 속성을 적용합니다.

이 예에서 전환 서비스는 소스 양식의 전화, 전화, 휴대폰, 직장 전화, 집 전화, 전화 번호, 전화 번호 및 전화 번호 키워드를 검색합니다. 이러한 키워드를 포함하는 필드를 기반으로 전환 서비스는 전환 후 적응형 양식 필드에 유형, 패턴 및 aem:afProperties를 적용합니다.

### 생성된 적응형 양식 필드 {#jsonschemaproperties}에 대한 JSON 스키마 속성

메타 모델은 Automated forms conversion 서비스를 사용하여 생성된 적응형 양식 필드에 대해 다음 JSON 스키마 공통 속성을 지원합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>속성 이름</strong></th> 
   <th><strong>설명</strong></th> 
  </tr> 
  <tr> 
   <td><p>제목</p></td> 
   <td> 
    <p>메타 모델의 제목 속성 내에 언급된 텍스트는 생성된 적응형 양식 필드에 대해 작업을 수행하기 위한 검색 키워드 역할을 합니다. 예를 들어 적응형 양식 필드의 레이블을 수정합니다. 자세한 내용은 <strong>사용자 지정 메타 모델 예제의 양식 필드</strong> 레이블 수정을 참조하십시오.</a><a href="#custommetamodelexamples"></a></p> </td> 
  </tr>
  <td><p>설명</p></td> 
   <td> 
    <p>설명 속성은 생성된 적응형 양식 필드에 대한 도움말 텍스트를 설정합니다. 자세한 내용은 <a href="#custommetamodelexamples">사용자 지정 메타 모델 예제의 양식 필드</strong>에 도움말 텍스트 추가를 참조하십시오.</a><strong></strong></p> </td> 
  </tr>
  <td><p>유형</p></td> 
   <td> 
    <p>type 속성은 생성된 적응형 양식 필드에 대한 데이터 유형을 정의합니다. 제목 속성에 사용할 수 있는 값은 다음과 같습니다.</p>
    <ul> 
     <li>string:텍스트 데이터 유형의 적응형 양식 필드를 생성합니다.</li> 
     <li>number:숫자 데이터 유형의 적응형 양식 필드를 생성합니다.</li>
     <li>정수:하위 유형이 정수로 설정된 숫자 데이터 형식의 응용 양식 필드를 생성합니다.</li>
     <li>boolean:스위치 응용 양식 구성 요소를 생성합니다.</li>
     </ul><p>메타 모델에서 type 속성을 사용하는 방법에 대한 자세한 내용은 <strong>사용자 지정 메타 모델 예제의 양식 필드</strong> 유형 수정을 참조하십시오.</a><a href="#custommetamodelexamples"></a></p></td> 
  </tr>
  <td><p>패턴</p></td> 
   <td> 
    <p>패턴 속성은 정규 표현식을 기반으로 생성된 적응형 양식 필드의 값을 제한합니다. 예를 들어 메타 모델의 다음 코드는 생성된 적응형 양식 필드에 대한 값을 10자리로 제한합니다.<br>"pattern":"/\\d{10}/"<br>마찬가지로 메타 모델의 다음 코드에서는 필드 값을 특정 날짜 형식으로 제한합니다.<br> "pattern":"date{DD MMM, YYYY}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>형식 속성은 정규 표현식 대신 명명된 패턴을 기반으로 생성된 적응형 양식 필드의 값을 제한합니다. 형식 속성에 사용할 수 있는 값은 다음과 같습니다.<ul><li>이메일:이메일 응용 양식 구성 요소를 생성합니다.</li><li>hostname:텍스트 상자 응용 양식 구성 요소를 생성합니다.</li></ul>메타 모델에서 형식 속성을 사용하는 방법에 대한 자세한 내용은 <strong>사용자 지정 메타 모델 예제의 양식 필드</strong> 형식 수정을 참조하십시오.</a><a href="#custommetamodelexamples"></a></p> </td> 
  </tr>
  <td><p>enum 및 enumNames</p></td> 
   <td> 
    <p>enum 및 enumNames 속성은 드롭다운, 확인란 또는 라디오 단추 필드의 값을 고정 세트로 제한합니다. enumNames에 나열된 값이 사용자 인터페이스에 표시됩니다. enum 속성을 사용하여 나열된 값은 계산에 사용됩니다.<br>자세한 내용은 적응형 양식의 <strong> 양식 필드</strong>를 객관식 <strong> 확인란</strong>으로 변환, 적응형 양식의 <strong> 텍스트 필드를 드롭다운 목록으로 </strong> 변환 및 드롭다운 목록 사용자 지정  <a href="#custommetamodelexamples">메타 모델 예에 추가 옵션 추가를 참조하십시오.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### 생성된 적응형 양식 필드에 속성을 적용하는 키워드 기반 검색 {#keywordsearch}

automated forms conversion 서비스는 전환 중에 소스 양식에서 키워드 검색을 수행합니다. 검색 기준을 충족하는 필드를 필터링한 후 전환 서비스는 메타 모델의 해당 필드에 대해 정의된 속성을 생성된 적응형 양식 필드에 적용합니다.

키워드는 **aem:affKeyword** 속성을 사용하여 참조됩니다.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

이 예에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **은행 계정 번호** 텍스트를 검색한 후 **type** 속성을 사용하여 필드를 **number** 유형으로 변환합니다.

### 생성된 적응형 양식 필드 {#additionalproperties}에 대한 추가 속성

메타 모델에서 **aem:afProperties** 속성을 사용하여 Automated forms conversion 서비스를 사용하여 생성된 적응형 양식 필드에 대해 다음과 같은 추가 속성을 정의할 수 있습니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>속성 이름</strong></th> 
   <th><strong>설명</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>multiLine 속성은 변환 후 소스 양식 필드를 적응형 양식의 여러 줄 필드로 변환합니다. 자세한 내용은 <a href="#custommetamodelexamples">사용자 지정 메타 모델 예제의 <strong>문자열 필드를 여러 줄 필드</strong>로 변환을 참조하십시오.</a></p> </td> 
  </tr>
  <td><p>mandatory</p></td> 
   <td> 
    <p>필수 속성은 전환 후 적응형 양식 필드에 대한 입력을 필수로 설정합니다.<br>자세한 내용은 사용자  <strong>지정 메타 모델 </strong> 예제에서  <a href="#custommetamodelexamples">응용 양식 필드에 유효성 검사추가를 참조하십시오.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>제목 JSON 스키마 속성이 있는 jcr:title 속성을 사용하면 변환 후 적응형 양식 필드의 레이블을 수정할 수 있습니다.<br>자세한 내용은  <strong>사용자 지정 메타 모델 예제 양식 </strong> 필드의  <a href="#custommetamodelexamples">레이블 수정을 참조하십시오.</a><br>JSON 스키마 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">를 사용하여 적응형 양식 </a> 필드에 적용할 수 있는 추가 속성에 대한 자세한 내용은 JSON 스키마를 사용한 적응형 양식 작성을 참조하십시오.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType 및 guideNodeClass</p></td> 
   <td> 
    <p>sling:resourceType 및 guideNodeClass 속성을 사용하면 양식 필드를 해당 적응형 양식 구성 요소에 매핑할 수 있습니다.<br>자세한 내용은 응용 형식 <strong>의 양식 필드를 객관식 </strong> 확인란으로 변환 및  <strong>사용자 지정 메타 모델 예제</strong> 의 응용 형식 드롭다운 목록 <a href="#custommetamodelexamples">으로 텍스트 필드를변환을참조하십시오.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>validatePictureClause 속성은 변환 후 적응형 양식 필드에 허용되는 형식에 대한 유효성 검사를 설정합니다.<br>자세한 내용은 사용자  <strong>지정 메타 모델 </strong> 예제에서  <a href="#custommetamodelexamples">응용 양식 필드에 유효성 검사추가를 참조하십시오.</p> </td> 
  </tr>
 </tbody> 
</table>

## 사용자 지정 메타 모델 {#modify-adaptive-form-fields-using-custom-meta-model}을(를) 사용하여 적응형 양식 필드 수정

조직은 기본 메타 모델에 나열된 패턴 및 유효성 검사 외에도 패턴을 가질 수 있습니다. 기본 메타 모델을 확장하여 조직에 맞는 패턴, 유효성 검사 및 개체를 추가할 수 있습니다. automated forms conversion 서비스는 전환 중에 사용자 지정 메타 모델을 양식 필드에 적용합니다. 조직 고유의 새 패턴, 유효성 검사 및 엔티티가 검색되므로 메타 모델을 계속 업데이트할 수 있습니다.

automated forms conversion 서비스는 다음 위치에 저장된 기본 메타 모델을 사용하여 전환 중에 소스 양식 필드를 적응형 양식 필드에 매핑합니다.

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

그러나 사용자 지정 메타 모델을 폴더에 저장하고 변환 서비스 속성을 수정하여 전환 중에 사용자 지정 메타 모델을 사용할 수 있습니다.

### 전환 중 사용자 지정 메타 모델 사용 {#use-custom-meta-model-during-conversion}

변환 중에 사용자 지정 메타 모델을 사용하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Forms]** **[!UICONTROL Forms & Documents]**&#x200B;에서 폴더를 만들고 사용자 정의 메타 모델 JSON 스키마 파일을 폴더에 업로드합니다.
1. 다음을 사용하여 전환 서비스 속성을 엽니다.

   **[!UICONTROL Tools]** >  **[!UICONTROL Cloud Services]** >  **[!UICONTROL Automated Forms Conversion Configuration]**>  **&lt;>선택한 구성의 속성**>****

1. **[!UICONTROL Basic]** 탭에서 **[!UICONTROL Custom Meta-model]** 필드에 사용자 지정 메타 모델의 위치를 지정하고 **[!UICONTROL Save & Close]**&#x200B;를 누릅니다.
1. [변환을 ](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) 실행하여 사용자 지정 메타 모델을 전환 프로세스에 적용합니다.

### 사용자 지정 메타 모델 예제 {#custommetamodelexamples}

사용자 지정 메타 모델을 사용하여 적응형 양식 필드 속성을 수정하는 일반적인 예는 다음과 같습니다.

* 양식 필드의 레이블 수정
* 양식 필드 유형 수정
* 양식 필드에 도움말 텍스트 추가
* 양식 필드를 적응형 양식의 객관식 라디오 단추로 변환
* 양식 필드의 형식 수정
* 적응형 양식 필드에 유효성 검사 추가
* 양식 필드를 적응형 양식의 드롭다운 목록 옵션으로 변환
* 드롭다운 목록에 추가 옵션 추가
* 문자열 필드를 여러 줄 필드로 변환

#### 양식 필드 {#modify-the-label-of-a-form-field} 레이블 수정

**예:** 양식의 은행 계정 번호 레이블을 전환 후 적응형 양식의 사용자 지정 계정 번호로 수정합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **title** 속성을 검색 키워드로 사용합니다. 양식에서 **은행 계정 번호** 텍스트를 검색한 후 전환 서비스는 **aem:afProperties** 섹션의 **jcr:title** 속성과 함께 언급된 **고객 계정 번호** 문자열로 텍스트를 대체합니다.

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### 양식 필드 {#modify-the-type-of-a-form-field} 유형 수정

**예**:변환 후 적응형 양식의 숫자 유형 필드로 변환하기 전에 양식에서  **은행 계정** 번호 입력 필드를 수정합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **은행 계정 번호** 텍스트를 검색한 후 **type** 속성을 사용하여 필드를 숫자 유형으로 변환합니다.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### 양식 필드 {#add-help-text-to-a-form-field}에 도움말 텍스트 추가

**예**:적응형 양식의  **은행 계정** 번호 필드에 도움말 텍스트를 추가합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **은행 계정 번호** 텍스트를 검색한 후 **description** 속성을 사용하여 응용 양식 필드에 도움말 텍스트를 추가합니다.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### 양식 필드를 적응형 양식 {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}의 객관식 확인란으로 변환

**예**:변환 전 양식에서  **** 문자열 유형의 국가 필드를 전환 후 적응형 양식의 확인란으로 변환합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **Country** 텍스트를 검색한 후 **enum** 속성을 사용하여 필드를 다음 확인란으로 변환합니다.

* 인도
* 잉글랜드
* 오스트레일리아
* 뉴질랜드

**sling:** resourceTypeand  **** guideNodeClassproperties는 양식 필드를 확인란 적응형 양식 구성 요소에 매핑합니다.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### 양식 필드 {#modify-the-format-of-a-form-field} 형식 수정

**예**:이메일 주소 형식을  **이메일** 형식으로 수정합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **이메일 주소** 텍스트를 검색한 후 **format** 속성을 사용하여 필드를 이메일 형식으로 변환합니다.

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### 응용 양식 필드 {#add-validations-to-adaptive-form-fields}에 유효성 검사 추가

**예 1:** 응용 양식의  **우편** 코드 필드에 유효성 검사를 추가합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **우편 번호** 텍스트를 검색한 후 **aem:afProperties** 섹션에 정의된 **validatePictureClause** 속성을 사용하여 필드에 유효성 검사를 추가합니다. 유효성 검사에 따라 전환 후 응용 양식의 **우편 번호** 필드에 지정한 입력에는 6자가 포함되어야 합니다.

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**예 2:** 적응형 양식의  **은행 계정 번호** 필드에 검증을 추가합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **은행 계정 번호** 텍스트를 검색한 후 **aem:afProperties** 섹션에 정의된 **필수** 속성을 사용하여 필드에 유효성 검사를 추가합니다. 유효성 검사에 따라 전환 후 양식을 제출하기 전에 **은행 계정 번호** 필드에 값을 지정해야 합니다.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### 텍스트 필드를 응용 양식 {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}의 드롭다운 목록으로 변환

**예**:변환 전 양식에서  **** 문자열 유형의 국가 필드를 적응형 양식의 드롭다운 옵션으로 변환합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 전환 서비스는 양식에서 **국가** 텍스트를 검색한 후 **enum** 속성을 사용하여 필드를 다음 드롭다운 목록 옵션으로 변환합니다.

* 인도
* 잉글랜드
* 오스트레일리아
* 뉴질랜드

**sling:** resourceTypeand  **** guideNodeClassproperties는 양식 필드를 드롭다운 적응형 양식 구성 요소에 매핑합니다.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### 드롭다운 목록 {#add-additional-options-to-the-drop-down-list}에 추가 옵션 추가

**예: 사용자 지정 메타 모델** 을 사용하여  **Sri Lankaas** 를 기존 드롭다운 목록에 추가 옵션으로 추가합니다.

추가 옵션을 추가하려면 새 옵션으로 **enum** 속성을 업데이트하십시오. 이 예제에서 **enum** 속성을 **스리랑카**&#x200B;의 추가 옵션으로 업데이트합니다. **enum** 속성에 나열된 값이 드롭다운 목록에 표시됩니다.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### 문자열 필드를 여러 줄 필드 {#convert-a-string-field-to-a-multi-line-field}로 변환

**예:** 문자열 유형의  **** 주소 필드를 변환 후 양식에서 여러 줄 필드로 변환합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **aem:affKeyword** 내의 텍스트를 검색 키워드로 사용합니다. 양식에서 **주소** 텍스트를 검색한 후 서비스는 **aem:afProperties** 섹션에 정의된 **multiLine** 속성을 사용하여 텍스트 필드를 다중 라인 필드로 변환합니다.

```
{
 "multiLine" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiLine": "true"
    }
  }
}
```
