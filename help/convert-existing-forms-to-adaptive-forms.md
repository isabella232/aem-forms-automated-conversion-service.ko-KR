---
title: 'PDF 양식을 적응형 양식으로 전환 '
seo-title: 'PDF 양식을 적응형 양식으로 전환 '
description: 자동화된 Forms 변환 서비스를 실행하여 PDF forms을 적응형 양식으로 변환
seo-description: 자동화된 Forms 변환 서비스를 실행하여 PDF forms을 적응형 양식으로 변환
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: 0bff37d64df233dc52310266e306edb734887727
workflow-type: tm+mt
source-wordcount: '1599'
ht-degree: 7%

---


# PDF 양식을 적응형 양식으로 전환 {#convert-print-forms-to-adaptive-forms}

Adobe Sensei에서 제공하는 AEM Forms 자동화된 Forms 전환 서비스는 PDF forms을 장치 친화적인 반응형 적응형 양식으로 자동 변환합니다. 비대화형 PDF forms, Acro Forms 또는 XFA 기반 PDF forms을 사용하는 경우 자동화된 Forms 변환 서비스는 이러한 양식을 적응형 양식으로 손쉽게 변환할 수 있습니다. 기능, 전환 워크플로우 및 온보딩 정보에 대한 자세한 내용은 [자동화된 Forms 전환](introduction.md) 서비스를 참조하십시오.

## 전제 조건 {#pre-requisites}

* [**전환 서비스 구성**](configure-service.md)

* **변환된 양식에 적용할 [템플릿](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) 준비:** 템플릿을 사용하면 모든 적응형 양식에 일관성 있는 브랜딩을 적용할 수 있습니다. 또한 자동화된 Forms 변환 서비스는 소스 PDF 문서의 머리글과 바닥글을 추출하여 사용하지 않습니다. 적응형 양식 템플릿을 사용하여 머리글과 바닥글을 지정할 수 있습니다. 템플릿에 지정된 머리글과 바닥글은 전환 중에 적응형 양식에 적용됩니다. 템플릿의 폴더를 만들 때 모든 사용자에 대한 **[!UICONTROL Browse configurations]** 옵션을 선택합니다.

* **변환된 양식에 적용할 [테마](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) 준비:** 테마를 사용하면 조직의 모든 적응형 양식에 일관된 스타일을 적용할 수 있습니다.

* **소스 PDF 문서에 Adobe Sign 텍스트 태그 추가:** 소스 PDF 양식에 [Adobe Sign 텍스트 태그가](https://helpx.adobe.com/sign/using/text-tag.html)있는 경우 변환 과정에서 모든 서명자 관련 정보가 유지됩니다. 생성된 적응형 양식이 모든 서명자 세부 사항을 채우고 적응형 양식을 Adobe Sign 서비스로 보내 서명을 합니다. 이 기능은 AcroForms에서만 사용할 수 있으며 적응형 양식 속성은 AcroForm 속성에 정확하게 정렬됩니다.

   원본 PDF 문서에 Adobe Sign 텍스트 태그를 추가하려면 원본 PDF 문서의 필드 이름을 [텍스트 태그로](https://helpx.adobe.com/sign/using/text-tag.html) 바꾸거나 Acrobat DC를 사용하여 양식 [만들기 문서에 설명된 대로 Adobe Sign](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html#) 양식으로변환을 사용하십시오.



## 전환 프로세스 시작 {#start-the-conversion-process}

AEM 인스턴스를 AEM Forms 전환 서비스와 연결한 후 PDF forms을 적응형 양식으로 변환할 수 있습니다. 양식을 변환하려면 나열된 순서대로 다음 단계를 수행하십시오.

* [AEM Forms 서버에 PDF forms 업로드](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [전환 실행](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [변환된 양식 검토 및 수정](review-correct-ui-edited.md)

### AEM Forms 서버에 PDF forms 업로드 {#upload-pdf-forms-to-your-aem-forms-server}

전환 서비스는 AEM Forms 인스턴스에서 사용 가능한 PDF forms을 적응형 양식으로 변환합니다. 필요에 따라 한 번에 또는 단계별로 모든 PDF forms을 업로드할 수 있습니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 폴더의 양식 수를 15개 미만으로 유지하고 폴더의 총 페이지 수를 50개 미만으로 유지합니다.
* 폴더 크기를 10MB 이하로 유지합니다. 양식을 하위 폴더에 보관하지 마십시오.
* 양식의 페이지 수를 15개 미만으로 유지합니다.
* 보호된 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 보호된 양식을 변환하지 않습니다.
* 파일 이름에 공백이 포함된 소스 양식을 업로드하지 마십시오. 양식을 업로드하기 전에 파일 이름에서 공백을 제거합니다.
* [PDF 포트폴리오](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)를 업로드하지 마십시오. 서비스는 PDF Portfolio을 응용 양식으로 변환하지 않습니다.
* 알려진 문제 [및](known-issues.md) 우수 사례 [및 고려 사항 섹션을](styles-and-pattern-considerations-and-best-practices.md) 읽어 보고 양식변경 사항을 제안하십시오.

다음 단계를 수행하여 AEM Forms 인스턴스의 폴더로 변환할 양식을 업로드합니다.

1. AEM Forms 인스턴스에 로그인합니다.

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 폴더의 **제목** 및 **이름** 을 지정합니다. 탭하기 **[!UICONTROL Create]**. 폴더가 생성됩니다.
1. 을 눌러 새로 만든 폴더를 엽니다.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 업로드할 양식을 선택하고 을 클릭한 **[!UICONTROL Open]**&#x200B;다음 을 클릭합니다 **[!UICONTROL Upload]**. 양식이 업로드됩니다.

### 전환 실행 {#run-the-conversion}

양식을 업로드하고 서비스를 구성한 후 다음 단계를 수행하여 변환을 시작합니다.

1. AEM Forms 인스턴스에서 [ **[!UICONTROL Adobe Experience Manager]** 전환 설정 대화 상자] > ![>](assets/adobeexperiencemanager.png)**[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**&#x200B;을 누릅니다.
1. 양식이나 PDF forms(변환할 양식)이 포함된 폴더를 선택하고 을 누릅니다 **[!UICONTROL Start Automated Conversion]**. 대화 상자가 **[!UICONTROL Conversion Settings]** 나타납니다.

   ![구성 지정](assets/conversion-settings-dialog.png)

1. [전환 설정] 대화 상자의 **[!UICONTROL Basic]** 탭에서 다음을 수행합니다.

   * **[!UICONTROL Select a cloud configuration]**. 구성을 선택하면 기본 템플릿과 테마가 이미 지정되어 있습니다. 필요한 경우 다른 템플릿 또는 테마를 지정할 수 있습니다.
   * 생성된 적응형 양식 및 해당 스키마를 저장할 위치를 지정합니다. 기본 경로를 사용하거나 사용자 지정 경로를 지정할 수 있습니다.
   * 데이터 모델 바인딩 **이 없는 적응형 양식** 생성 옵션을 사용하여 데이터 모델 바인딩이 있거나 없는 적응형 양식을 생성할지 여부를 선택합니다.
이 옵션을 선택하지 않으면 전환 서비스는 적응형 양식을 JSON 스키마와 자동으로 연결하고 적응형 양식과 JSON 스키마에서 사용 가능한 필드 간에 데이터 바인딩을 생성합니다. 생성된 JSON 스키마를 저장할 기본 위치가 **[!UICONTROL Save generated data model schema at]** 필드에 표시됩니다. 생성된 스키마를 저장하도록 위치를 사용자 지정할 수도 있습니다.
이 옵션을 선택하면 전환 서비스는 데이터 모델 바인딩 없이 응용 양식을 생성합니다. 변환 성공 후 적응형 양식을 양식 데이터 모델, XML 스키마 또는 JSON 스키마에 연결할 수 있습니다. 자세한 내용은 응용 양식 [만들기를 참조하십시오](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. [전환 설정] 대화 상자의 **[!UICONTROL Additional]** 탭에서
   * 전환 서비스에서 변환된 양식의 양식 조각을 식별, 추출 및 다운로드할 수 있도록 하려면 이 **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 선택합니다. 이 **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 선택하면 추출된 양식 조각 및 해당 양식 조각 스키마를 저장할 경로를 지정하는 옵션이 활성화됩니다.
   * 기존 JSON 스키마 기반 및 스키마 덜 적응형 양식 조각이 있는 경우 **[!UICONTROL existing adaptive form fragments]**&#x200B;의 위치를 지정하고 이러한 조각을 자동으로 생성된 적응형 양식으로 사용할 계획입니다. 전환 서비스는 입력 PDF forms(비대화형 PDF forms만 해당)을 사용하는 사용 가능한 JSON 스키마 기반 및 스키마 없는 적응형 양식 조각과 일치하며 일치하는 일치하는 적응형 양식 조각을 해당 적응형 양식에 사용합니다.

   >[!NOTE]
   >
   >
   > * 한 번에 **[!UICONTROL  Extract Fragment]** 또는 **[!UICONTROL Use existing adaptive form fragments]** 옵션만 사용할 수 있습니다. 두 옵션을 동시에 사용할 수는 없습니다.
   > * 비대화형 PDF forms에서만 **[!UICONTROL Use existing adaptive form fragments]** 옵션을 사용할 수 있습니다. 다른 양식 유형은 아직 지원되지 않습니다.
   > * 자동화된 전환 서비스를 사용하면 언바운드 조각 또는 JSON 스키마에 바인딩된 조각만 사용할 수 있습니다. XFA 조각을 사용하지 마십시오. XFA 조각은 지원되지 않습니다.


   * 데스크탑 및 랩탑과 같은 대형 화면의 소스 양식 레이아웃을 유지하려면 이 **[!UICONTROL Auto-detect multi-column layout of input forms]** 옵션을 선택합니다. 이 옵션은 소스 양식의 다중 열 레이아웃을 유지하는 데 유용합니다. 예를 들어, 소스 PDF에 2열 레이아웃이 있는 경우 서비스는 대형 화면 디스플레이에 대한 2열 레이아웃과 휴대폰과 같은 작은 화면 장치에 대한 단일 열 레이아웃으로 출력 적응형 양식을 생성합니다. 이 기능에는 데이터 소스 스키마 구조에 알려진 몇 가지 문제가 있습니다. 자세한 내용은 [알려진 문제](known-issues.md) 문서를 참조하십시오.
   * 기본적으로 이 서비스를 통해 PDF 양식의 각 페이지마다 별도의 최상위 패널을 만들 수 있습니다. Now, you can use the **[!UICONTROL Auto-detect logical sections]** option to not create page level panels (page number-based panels) and create only logical panels. 또한 이전 논리 섹션이 포함된 어떤 섹션에도 속하지 않는 필드와 두 장의 인접한 페이지에 걸쳐 있는 논리 섹션의 필드를 단일 논리 섹션으로 병합할 수 있습니다. 예를 들어, 논리 섹션의 일부 필드가 1페이지의 끝에 있고 일부는 2페이지의 시작에 있는 경우 그러한 모든 필드는 단일 논리 섹션으로 병합됩니다.

      >[!NOTE]
      > 이 기능을 사용하려면 커넥터 패키지 1.1.38 이상이 **[!UICONTROL Auto-detect logical sections]** 필요합니다.



1. 탭하기 **[!UICONTROL Start Conversion]**. 전환이 시작되었습니다. 변환 진행 상태는 전환이 진행 중일 때까지 폴더나 양식에 표시됩니다. 전환이 완료된 후 메시지가 다른 상태 메시지(변환됨, 부분적으로 변환됨 또는 전환 실패)로 대체됩니다. 전환 완료 시 구성된 이메일 주소에서도 상태 이메일이 전송됩니다.

   * 성공적으로 변환하면 변환된 응용 양식 및 관련 스키마가 전환 대화 상자의 **[!UICONTROL Basic]** 탭에 지정된 경로로 다운로드됩니다. 양식 조각 및 해당 스키마는 변환을 시작하기 전에 조각 추출 옵션을 선택한 경우에만 다운로드됩니다.
   * 변환 실패 시 일부 입력 양식만 변환되지 않으면 모든 입력 양식이 변환되지 않거나 메시지 **[!UICONTROL Conversion Failed]** **[!UICONTROL Partially Failed]** 가 표시되는 경우 메시지가 표시됩니다. 상태 이메일은 [구성된 이메일 주소로](configure-service.md#configureemailnotification) 전송되며 error.log 파일에 오류가 기록됩니다.

   XFA 기반 PDF 양식을 적응형 양식으로 변환하는 경우 변환 서비스는 PDF 양식을 변환한 적응형 양식으로 자동 연결하여 문서 템플릿으로 사용합니다. 전환 후 적응형 양식 속성을 열어 탭의 **[!UICONTROL Document of Record Template Configuration]** 섹션에서 기록 문서를 볼 수 **[!UICONTROL Form Model]** 있습니다. </br>

   전환 서비스는 **[!UICONTROL Tools]** > > > > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** 옵션 **[!UICONTROL Generate Document of Record]** 을 활성화한 경우에만 변환된 적응형 양식으로 PDF 양식을 자동으로 업로드합니다.

   <!--
   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >변환 프로세스가 60분 이상 걸리고 PDF 양식이 여전히 적응형 양식으로 변환되지 않은 경우, AEM Forms 인스턴스에 폴더를 만들고 PDF 양식을 새로 만든 폴더에 업로드한 다음 변환을 다시 시작합니다.

## Review and correct the converted forms {#review-and-correct-the-converted-forms}

실제 양식에는 복잡한 데이터 캡처 요구 사항이 있습니다. 자동 전환이 완료되면 고객은 양식의 전환 품질을 검토하고 필요한 사항을 업데이트할 수 있습니다. AEM Forms은 [검토 및 올바른](review-correct-ui-edited.md) 편집기를 제공하여 필요한 사항을 변경합니다. 이 기능을 사용하면 양식 필드에 대한 자동 식별 기능을 개선하고, 식별된 필드를 한 유형에서 다른 유형으로 변환할 수 있습니다. 예를 들어 양식의 두 열 레이아웃을 식별하고 라디오 단추로 자동 식별되는 필드를 여러 선택 항목 필드로 변경하는 데 도움이 됩니다.
