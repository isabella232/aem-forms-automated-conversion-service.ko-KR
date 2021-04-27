---
title: 'PDF 양식을 적응형 양식으로 전환 '
seo-title: 'PDF 양식을 적응형 양식으로 전환 '
description: automated forms conversion 서비스를 실행하여 PDF forms을 적응형 양식으로 변환
seo-description: automated forms conversion 서비스를 실행하여 PDF forms을 적응형 양식으로 변환
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: c4f0d07b38cdb6aa162a0b61abe12fe9d1677a8c
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 8%

---


# PDF 양식을 적응형 양식으로 전환 {#convert-print-forms-to-adaptive-forms}

Adobe Sensei 기반의 AEM Forms Automated forms conversion 서비스는 PDF forms을 장치 친화적인 적응형 양식으로 자동으로 변환합니다. 비대화형 PDF forms, Acro Forms 또는 XFA 기반 PDF forms을 사용하는 경우 Automated forms conversion 서비스는 이러한 양식을 적응형 양식으로 쉽게 변환할 수 있습니다. 기능, 전환 워크플로우 및 온보딩 정보에 대한 자세한 내용은 [Automated forms conversion](introduction.md) 서비스를 참조하십시오.

## 전제 조건 {#pre-requisites}

* [**전환 서비스 구성**](configure-service.md)

* **변환된  [&#128279;](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) 양식에 적용할 템플릿 준비:** 템플릿을 사용하면 모든 적응형 양식에 일관성 있는 브랜딩을 적용할 수 있습니다. 또한 Automated forms conversion 서비스는 소스 PDF 문서의 머리글과 바닥글을 추출하고 사용하지 않습니다. 적응형 양식 템플릿을 사용하여 머리글과 바닥글을 지정할 수 있습니다. 템플릿에 지정된 머리글과 바닥글은 전환 중에 적응형 양식에 적용됩니다. 템플릿의 폴더를 만들 때 모든 사용자에 대해 **[!UICONTROL Browse configurations]** 옵션을 선택합니다.

* **변환된  [&#128279;](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) 양식에 적용할 테마 준비:** 테마를 사용하면 조직의 모든 적응형 양식에 일관된 스타일을 적용할 수 있습니다.

* **(선택 사항)** [**소스 PDF forms을 Adobe Sign 양식으로 변환**](frequently-asked-questions.md)


## 전환 프로세스 {#start-the-conversion-process} 시작

AEM 인스턴스를 AEM Forms Conversion Service에 연결하면 PDF forms을 적응형 양식으로 변환할 수 있습니다. 양식을 변환하려면 다음 단계를 순서대로 수행합니다.

* [AEM Forms 서버에 PDF forms 업로드](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [전환 실행](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [변환된 양식 검토 및 수정](review-correct-ui-edited.md)

### AEM Forms 서버에 PDF forms 업로드 {#upload-pdf-forms-to-your-aem-forms-server}

전환 서비스는 AEM Forms 인스턴스에서 사용할 수 있는 PDF forms을 적응형 양식으로 변환합니다. 필요에 따라 모든 PDF forms을 한 번에 또는 단계적으로 업로드할 수 있습니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 한 폴더에 있는 양식 수를 15개 미만으로 유지하고 폴더의 총 페이지 수를 50개 미만으로 유지합니다.
* 폴더 크기를 10MB보다 작게 유지합니다. 양식을 하위 폴더에 보관하지 마십시오.
* 양식의 페이지 수를 15개 미만으로 유지합니다.
* 보호된 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 보호된 양식을 변환하지 않습니다.
* 파일 이름에 공백이 포함된 소스 양식을 업로드하지 마십시오. 양식을 업로드하기 전에 파일 이름에서 공간을 제거합니다.
* [PDF 포트폴리오](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)를 업로드하지 마십시오. 서비스는 PDF Portfolio을 적응형 양식으로 변환하지 않습니다.
* [알려진 문제](known-issues.md) 및 [우수 사례 및 고려 사항](styles-and-pattern-considerations-and-best-practices.md) 섹션을 읽고 양식을 제안된 대로 변경합니다.

AEM Forms 인스턴스에서 폴더로 변환할 양식을 업로드하려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에 로그인합니다.

1. **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**&#x200B;를 탭합니다.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 폴더의 **제목** 및 **이름**&#x200B;을 지정합니다. 탭하기 **[!UICONTROL Create]**. 폴더가 생성됩니다.
1. 을 눌러 새로 만든 폴더를 엽니다.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 업로드할 양식을 선택하고 **[!UICONTROL Open]**&#x200B;을 클릭한 다음 **[!UICONTROL Upload]**&#x200B;을 클릭합니다. 양식이 업로드됩니다.

### 전환 {#run-the-conversion} 실행

양식을 업로드하고 서비스를 구성한 후 다음 단계를 수행하여 변환을 시작합니다.

1. AEM Forms 인스턴스에서 **[!UICONTROL Adobe Experience Manager]** ![전환 설정 대화 상자](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**&#x200B;를 탭합니다.
1. 양식이나 PDF forms이 포함된 폴더(변환할 양식)를 선택하고 **[!UICONTROL Start Automated Conversion]**&#x200B;을 누릅니다. **[!UICONTROL Conversion Settings]** 대화 상자가 나타납니다.

   ![구성 지정](assets/conversion-settings-dialog.png)

1. [변환 설정] 대화 상자의 **[!UICONTROL Basic]** 탭에서 다음을 수행합니다.

   * **[!UICONTROL Select a cloud configuration]**. 구성을 선택하면 기본 템플릿과 테마가 이미 지정됩니다. 필요한 경우 다른 템플릿 또는 테마를 지정할 수 있습니다.
   * 생성된 적응형 양식 및 해당 스키마를 저장할 위치를 지정합니다. 기본 경로를 사용하거나 사용자 지정 경로를 지정할 수 있습니다.
   * 데이터 모델 바인딩 없이 응용 양식 생성&#x200B;**옵션을 사용하여 데이터 모델 바인딩이 있거나 없는 응용 양식을 생성할지 여부를 선택합니다.**
이 옵션을 선택하지 않으면 전환 서비스는 적응형 양식을 JSON 스키마와 자동으로 연관시키고 적응형 양식과 JSON 스키마에서 사용 가능한 필드 간에 데이터 바인딩을 만듭니다. **[!UICONTROL Save generated data model schema at]** 필드는 생성된 JSON 스키마를 저장할 기본 위치를 표시합니다. 생성된 스키마를 저장하도록 위치를 사용자 지정할 수도 있습니다.
이 옵션을 선택하면 변환 서비스는 데이터 모델 바인딩 없이 응용 양식을 생성합니다. 변환 성공 후 적응형 양식을 양식 데이터 모델, XML 스키마 또는 JSON 스키마에 연결할 수 있습니다. 자세한 내용은 [적응형 양식 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)를 참조하십시오.

   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. 전환 설정 대화 상자의 **[!UICONTROL Additional]** 탭에서
   * 전환 서비스에서 변환된 양식의 양식 조각을 식별, 추출 및 다운로드할 수 있도록 하려면 **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 선택합니다. **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 선택하면 추출된 양식 조각 및 해당 양식 조각 스키마를 저장할 경로를 지정하는 옵션이 활성화됩니다.
   * 기존 JSON 스키마 기반 및 스키마가 적은 적응형 양식 조각이 있는 경우 **[!UICONTROL existing adaptive form fragments]** 위치를 지정하고 이러한 조각을 자동으로 생성된 적응형 양식으로 사용할 계획입니다. 전환 서비스는 사용 가능한 JSON 스키마 기반 및 입력 PDF forms(비대화형 PDF forms만 해당)을 사용하여 스키마 덜 적응형 양식 조각과 일치시킵니다. 일치하는 항목이 있으면 일치하는 적응형 양식 조각은 해당 적응형 양식에 사용됩니다.

   >[!NOTE]
   >
   >
   > * 한 번에 **[!UICONTROL  Extract Fragment]** 또는 **[!UICONTROL Use existing adaptive form fragments]** 옵션만 사용할 수 있습니다. 두 옵션을 동시에 사용할 수는 없습니다.
   > * **[!UICONTROL Use existing adaptive form fragments]** 옵션은 비대화형 PDF forms에서만 사용할 수 있습니다. 다른 양식 유형은 아직 지원되지 않습니다.
   > * 자동화된 전환 서비스를 사용하여 언바운드 조각 또는 JSON 스키마에 바인딩된 조각만 사용할 수 있습니다. XFA 조각을 사용하지 마십시오. XFA 조각은 지원되지 않습니다.


   * 데스크톱 및 랩탑과 같은 대형 화면의 소스 양식 레이아웃을 유지하려면 **[!UICONTROL Auto-detect multi-column layout of input forms]** 옵션을 선택합니다. 이 옵션은 소스 양식의 여러 열 레이아웃을 유지하는 데 유용합니다. 예를 들어 소스 PDF에 2열 레이아웃이 있는 경우 서비스는 대형 화면 디스플레이에 대한 2열 레이아웃과 휴대폰과 같은 작은 화면 장치에 대한 단일 열 레이아웃으로 출력 적응형 양식을 생성합니다. 이 기능에는 데이터 소스 스키마 구조와 관련하여 몇 가지 알려진 문제가 있습니다. 자세한 내용은 [알려진 문제](known-issues.md) 문서를 참조하십시오.
   * 기본적으로 이 서비스를 통해 PDF 양식의 각 페이지마다 별도의 최상위 패널을 만들 수 있습니다. 이제 **[!UICONTROL Auto-detect logical sections]** 옵션을 사용하여 페이지 수준 패널(페이지 번호 기반 패널)을 만들지 않고 논리 패널만 만들 수 있습니다. 또한 이전 논리 섹션이 포함된 어떤 섹션에도 속하지 않는 필드와 두 장의 인접한 페이지에 걸쳐 있는 논리 섹션의 필드를 단일 논리 섹션으로 병합할 수 있습니다. 예를 들어, 논리 섹션의 일부 필드가 1페이지의 끝에 있고 일부는 2페이지의 시작에 있는 경우 그러한 모든 필드는 단일 논리 섹션으로 병합됩니다.

      >[!NOTE]
      > **[!UICONTROL Auto-detect logical sections]** 기능을 사용하려면 커넥터 패키지 1.1.38 이상이 필요합니다.



1. 탭하기 **[!UICONTROL Start Conversion]**. 전환이 시작되었습니다. 변환 진행 상태는 변환이 진행 중일 때까지 폴더 또는 양식에 표시됩니다. 변환이 완료된 후 다른 상태 메시지(전환됨, 부분적으로 변환됨 또는 전환 실패)가 대체됩니다. 전환 완료 시 구성된 이메일 주소에도 상태 이메일이 전송됩니다.

   * 성공적으로 변환하면 변환된 적응형 양식 및 관련 스키마가 변환 대화 상자의 **[!UICONTROL Basic]** 탭에 지정된 경로로 다운로드됩니다. 양식 조각 및 해당 스키마는 변환을 시작하기 전에 [조각 추출] 옵션을 선택한 경우에만 다운로드됩니다.
   * 변환 실패 시 일부 입력 양식만 변환되지 않으면 모든 입력 양식이 변환되지 않거나 **[!UICONTROL Conversion Failed]** 메시지가 표시됩니다. **[!UICONTROL Partially Failed]** 상태 이메일이 [구성된 이메일 주소](configure-service.md#configureemailnotification)에 전송되고 error.log 파일에 오류가 기록됩니다.

   XFA 기반 PDF 양식을 적응형 양식으로 변환하는 경우 변환 서비스는 PDF 양식을 변환한 적응형 양식에 레코드 문서 템플릿으로 자동으로 연결합니다. 변환 후 적응형 양식 속성을 열어 **[!UICONTROL Form Model]** 탭의 **[!UICONTROL Document of Record Template Configuration]** 섹션에서 기록 문서를 볼 수 있습니다.</br>

   전환 서비스는 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 활성화한 경우에만 PDF 양식을 변환된 적응형 양식으로 자동 업로드합니다.

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
   >변환 프로세스가 60분 이상 걸리고 PDF 양식이 여전히 적응형 양식으로 변환되지 않은 경우 AEM Forms 인스턴스에서 폴더를 만들고 PDF 양식을 새로 만든 폴더에 업로드하고 변환을 다시 시작합니다.

## 변환된 양식 {#review-and-correct-the-converted-forms} 검토 및 수정

실제 양식에는 복잡한 데이터 캡처 요구 사항이 있습니다. 자동 변환이 완료되면 사용자는 양식의 전환 품질을 검토하고 필요한 양식 업데이트를 수행할 수 있습니다. AEM Forms은 [검토 및](review-correct-ui-edited.md) 편집기를 제공하여 필요한 변경 작업을 수행합니다. 이 기능을 사용하면 양식 필드에 대한 자동 식별 기능을 향상시키고 식별된 필드를 한 유형에서 다른 유형으로 변환할 수 있습니다. 예를 들어 양식의 2열 레이아웃을 식별하고 라디오 단추로 자동 식별되는 필드를 여러 선택 필드로 변경할 수 있습니다.
