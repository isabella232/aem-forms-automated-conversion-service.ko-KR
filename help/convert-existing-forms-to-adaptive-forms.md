---
title: 'PDF 양식을 적응형 양식으로 전환 '
seo-title: Convert PDF forms to adaptive forms
description: automated forms conversion 서비스를 실행하여 PDF forms을 적응형 양식으로 변환
seo-description: Run the Automated Forms Conversion service to convert PDF forms to adaptive forms
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
exl-id: 415e05b5-5a90-490c-bf7c-d3365ce95e24
source-git-commit: 5f07f5df6369007a491cf0873839f84a61827cb5
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 7%

---

# PDF 양식을 적응형 양식으로 전환 {#convert-print-forms-to-adaptive-forms}

Adobe Sensei을 기반으로 하는 AEM Forms Automated forms conversion 서비스는 PDF forms을 장치 친화적인 반응형 적응형 양식으로 자동 변환합니다. 비대화형 PDF forms, Acro Forms 또는 XFA 기반 PDF forms을 사용하는 경우 Automated forms conversion 서비스에서 이러한 양식을 적응형 양식으로 쉽게 변환할 수 있습니다. 기능, 전환 워크플로우 및 온보딩 정보에 대한 자세한 내용은 [automated forms conversion](introduction.md) 서비스.

## 전제 조건 {#pre-requisites}

* [**전환 서비스 구성**](configure-service.md)

* **준비 [템플릿](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) 변환된 양식에 적용하려면 다음을 수행하십시오.** 템플릿을 사용하면 모든 적응형 양식에 일관된 브랜딩을 적용할 수 있습니다. 또한 Automated forms conversion 서비스는 소스 PDF 문서의 머리글과 바닥글을 추출하고 사용하지 않습니다. 적응형 양식 템플릿을 사용하여 머리글 및 바닥글을 지정할 수 있습니다. 템플릿에 지정된 머리글 및 바닥글은 전환 중에 적응형 양식에 적용됩니다. 템플릿에 대한 폴더를 만들 때 **[!UICONTROL Browse configurations]** 모두를 위한 옵션.

* **준비 [테마](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) 변환된 양식에 적용하려면 다음을 수행하십시오.** 테마를 사용하면 조직의 모든 적응형 양식에 일관된 스타일을 적용할 수 있습니다.

* **(선택 사항)** [**소스 PDF forms을 Adobe Sign 양식으로 변환**](frequently-asked-questions.md)

## 변환 프로세스 시작 {#start-the-conversion-process}

AEM 인스턴스를 AEM Forms 전환 서비스와 연결한 후 PDF forms을 적응형 양식으로 전환할 수 있습니다. 양식을 전환하려면 다음 단계를 나열된 순서로 수행합니다.

* [AEM Forms 서버에 PDF forms 업로드](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [전환 실행](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [전환된 양식을 검토하고 수정합니다](review-correct-ui-edited.md)

### AEM Forms 서버에 PDF forms 업로드 {#upload-pdf-forms-to-your-aem-forms-server}

전환 서비스는 AEM Forms 인스턴스에서 사용할 수 있는 PDF forms을 적응형 양식으로 변환합니다. 필요에 따라 모든 PDF forms을 한 번에 또는 단계별로 업로드할 수 있습니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 폴더의 양식 수를 15개 미만으로 유지하고 폴더의 총 페이지 수를 50개 미만으로 유지합니다.
* 폴더 크기를 10MB 미만으로 유지합니다. 양식을 하위 폴더에 보관하지 마십시오.
* 양식의 페이지 수를 15개 미만으로 유지합니다.
* 보호된 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 보안 양식을 전환하지 않습니다.
* 파일 이름에 공백이 있는 소스 양식을 업로드하지 마십시오. 양식을 업로드하기 전에 파일 이름에서 공백을 제거합니다.
* [PDF 포트폴리오](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)를 업로드하지 마십시오. 이 서비스는 PDF Portfolio을 적응형 양식으로 전환하지 않습니다.
* 다음 문서를 참조하십시오. [알려진 문제](known-issues.md) 그리고 [모범 사례 및 고려 사항](styles-and-pattern-considerations-and-best-practices.md) 섹션을 수정하고 양식에 제안된 변경 사항을 적용합니다.

AEM Forms 인스턴스의 폴더로 변환할 양식을 업로드하려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에 로그인합니다.

1. 탭 **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 지정 **제목** 및 **이름** 섹션에 있는 마지막 항목이 될 필요가 없습니다. **[!UICONTROL Create]**&#x200B;을 누릅니다. 폴더가 만들어집니다.
1. 탭하여 새로 만든 폴더를 엽니다.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 업로드할 양식을 선택하고 을(를) 클릭합니다. **[!UICONTROL Open]**&#x200B;를 클릭하고 **[!UICONTROL Upload]**. 양식이 업로드됩니다.

### 전환 실행 {#run-the-conversion}

양식을 업로드하고 서비스를 구성한 후 다음 단계를 수행하여 전환을 시작합니다.

1. AEM Forms 인스턴스에서 을 탭합니다 **[!UICONTROL Adobe Experience Manager]** ![변환 설정 대화 상자](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 양식 또는 PDF forms(변환할 양식)가 포함된 폴더를 선택하고 **[!UICONTROL Start Automated Conversion]**. 다음 **[!UICONTROL Conversion Settings]** 대화 상자가 나타납니다.

   ![구성을 지정합니다](assets/conversion-settings-dialog.png)

1. 에서 **[!UICONTROL Basic]** 전환 설정 대화 상자의 탭:

   * **[!UICONTROL Select a cloud configuration]**. 구성을 선택하면 기본 템플릿과 테마가 이미 지정됩니다. 필요한 경우 다른 템플릿 또는 테마를 지정할 수 있습니다.
   * 생성된 적응형 양식 및 해당 스키마를 저장할 위치를 지정합니다. 기본 경로를 사용하거나 사용자 지정 경로를 지정할 수 있습니다.
   * 를 사용하십시오 **데이터 모델 바인딩 없이 적응형 양식 생성** 데이터 모델 바인딩이 있거나 없는 적응형 양식을 생성하려는 경우 선택합니다.
이 옵션을 선택하지 않으면 전환 서비스는 적응형 양식을 JSON 스키마와 자동으로 연결하고 적응형 양식과 JSON 스키마에서 사용할 수 있는 필드 간에 데이터 바인딩을 만듭니다. 다음 **[!UICONTROL Save generated data model schema at]** 필드에는 생성된 JSON 스키마를 저장할 기본 위치가 표시됩니다. 위치를 사용자 지정하여 생성된 스키마를 저장할 수도 있습니다.
이 옵션을 선택하면 변환 서비스는 데이터 모델 바인딩 없이 적응형 양식을 생성합니다. 성공적으로 변환한 후 적응형 양식을 양식 데이터 모델, XML 스키마 또는 JSON 스키마와 연결할 수 있습니다. 자세한 내용은 [적응형 양식 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. 에서 **[!UICONTROL Additional]** 전환 설정 대화 상자의 탭,
   * 을(를) 선택합니다 **[!UICONTROL Extract fragment from adaptive forms]** 전환 서비스에서 전환된 양식의 양식 조각을 식별, 추출 및 다운로드할 수 있는 옵션입니다. 을(를) 선택하는 경우 **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 사용하면 추출된 양식 조각 및 해당 양식 조각 스키마를 저장할 경로를 지정하는 옵션이 활성화됩니다.
   * 위치 지정 **[!UICONTROL existing adaptive form fragments]**&#x200B;기존 JSON 스키마 기반 및 스키마 덜 적응형 양식 조각이 있는 경우 자동으로 생성된 적응형 양식에 이러한 조각을 사용할 계획이라면 이러한 조각을 사용할 수 있습니다. 전환 서비스는 입력 PDF forms이 있는 사용 가능한 JSON 스키마 기반 및 스키마 없는 적응형 양식 조각과 일치합니다(비대화형 PDF forms만 해당). 일치하는 항목이 있으면 일치하는 적응형 양식 조각이 해당 적응형 양식에 사용됩니다.

   >[!NOTE]
   >
   >
   > * 만 사용할 수 있습니다 **[!UICONTROL  Extract Fragment]** 또는 **[!UICONTROL Use existing adaptive form fragments]** 한 번에 선택할 수 있습니다. 두 옵션을 동시에 사용할 수 없습니다.
   > * 를 사용할 수 있습니다 **[!UICONTROL Use existing adaptive form fragments]** 비대화형 PDF forms이 있는 경우에만 옵션을 선택합니다. 다른 양식 유형은 아직 지원되지 않습니다.
   > * 자동화된 변환 서비스를 사용하여 JSON 스키마에 바인딩된 언바운드 조각이나 조각만 사용할 수 있습니다. XFA 조각을 사용하지 마십시오. XFA 조각은 지원되지 않습니다.


   * 을(를) 선택합니다 **[!UICONTROL Auto-detect multi-column layout of input forms]** 데스크탑 및 노트북과 같은 대형 화면의 소스 양식의 레이아웃을 유지하는 옵션 이 옵션은 소스 양식의 다중 열 레이아웃을 유지하는 데 유용합니다. 예를 들어 소스 PDF에 2열 레이아웃이 있는 경우 이 서비스는 큰 화면 디스플레이에 대한 2열 레이아웃과 휴대폰과 같은 작은 화면 장치에 대한 단일 열 레이아웃으로 출력 적응형 양식을 생성합니다. 이 기능에는 데이터 소스 스키마 구조에 대해 알려진 몇 가지 문제가 있습니다. 자세한 내용은 [알려진 문제](known-issues.md) 문서.
   * 기본적으로 이 서비스를 통해 PDF 양식의 각 페이지마다 별도의 최상위 패널을 만들 수 있습니다. 이제 **[!UICONTROL Auto-detect logical sections]** 페이지 수준 패널(페이지 번호 기반 패널)을 만들지 않고 논리 패널만 만드는 옵션입니다. 또한 이전 논리 섹션이 포함된 어떤 섹션에도 속하지 않는 필드와 두 장의 인접한 페이지에 걸쳐 있는 논리 섹션의 필드를 단일 논리 섹션으로 병합할 수 있습니다. 예를 들어, 논리 섹션의 일부 필드가 1페이지의 끝에 있고 일부는 2페이지의 시작에 있는 경우 그러한 모든 필드는 단일 논리 섹션으로 병합됩니다.

      >[!NOTE]
      > 를 사용하려면 커넥터 패키지 1.1.38 이상이 필요합니다  **[!UICONTROL Auto-detect logical sections]** 기능.


* (AEM Forms as a Cloud Service 전용) [섹션을 조각으로 자동 변환] 옵션이 15페이지가 넘는 PDF forms에 적용됩니다. 감지된 최상위 섹션을 단편으로 변환합니다. 또한 생성된 모든 조각에 대해 레이지 로드를 가능하게 합니다. 이것은 변환된 양식의 렌더링 속도를 개선하는 데 도움이 되며 적응형 양식 편집기에서 큰 양식을 더 쉽게 로드할 수 있도록 합니다.

   >[!NOTE]
   > 섹션을 조각으로 자동 변환 옵션을 사용하는 동안 응답형 레이아웃 템플릿을 사용하지 마십시오.
   > 작은 패널을 큰 패널에 병합하려면 검토 및 수정 편집기를 사용하십시오. 변환된 적응형 양식의 조각 수를 줄이는 데 도움이 됩니다.
   > &quot;너무 많은 호출&quot; 예외가 발생하는 경우,
   >
   > * 간소화된 계층 구조를 만들기 위해 양식 재구성
   > * [sling.max.calls 매개 변수의 값을 늘립니다.]예외가 사라질 때까지 충분히 높은 수치로.
   > * [캐시 크기 증가](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html). 양식이 너무 복잡하며 테이블 수가 많고 다중 수준 계층 구조가 있는 경우 오류가 발생합니다.


1. **[!UICONTROL Start Conversion]**&#x200B;을 누릅니다. 전환이 시작됩니다. 변환 진행 상태는 전환이 진행될 때까지 폴더 또는 양식에 표시됩니다. 전환이 완료된 후 메시지가 다른 상태 메시지(전환됨, 부분적으로 변환됨 또는 변환 실패)로 바뀝니다. 전환 완료 시 구성된 이메일 주소에서도 상태 이메일을 보냅니다.

   * 성공적으로 변환되면 변환된 적응형 양식 및 관련 스키마가 **[!UICONTROL Basic]** 전환 대화 상자의 탭입니다. 양식 조각 및 해당 스키마는 전환을 시작하기 전에 조각 추출 옵션을 선택한 경우에만 다운로드됩니다.
   * 변환 실패 시 **[!UICONTROL Conversion Failed]** 모든 입력 양식이 변환되지 않거나 **[!UICONTROL Partially Failed]** 일부 입력 양식만 변환되지 않으면 메시지가 표시됩니다. 상태 이메일은 [구성된 전자 메일 주소](configure-service.md#configureemailnotification) error.log 파일에 오류가 기록됩니다.

   XFA 기반 PDF 양식을 적응형 양식으로 전환하는 경우 전환 서비스는 PDF 양식을 전환된 적응형 양식에 레코드 문서 템플릿으로 자동으로 연결합니다. 변환 후 적응형 양식 속성을 열어 **[!UICONTROL Document of Record Template Configuration]** 섹션 **[!UICONTROL Form Model]** 탭. </br>

   전환 서비스는 사용자가 PDF을 사용하도록 설정한 경우에만 양식을 변환된 적응형 양식으로 자동 업로드합니다 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 선택 사항입니다.

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
   >전환 프로세스가 60분 이상 걸리며 PDF 양식이 여전히 적응형 양식으로 전환되지 않은 경우 AEM Forms 인스턴스에서 폴더를 만들고 PDF 양식을 새로 만든 폴더로 업로드한 다음 전환을 다시 시작합니다.

## 전환된 양식을 검토하고 수정합니다 {#review-and-correct-the-converted-forms}

실제 양식에는 복잡한 데이터 캡처 요구 사항이 있습니다. 자동 전환이 완료되면 고객은 양식의 전환 품질을 검토하고 양식에 필요한 업데이트를 수행할 수 있습니다. AEM Forms은 다음을 제공합니다 [검토 및 수정](review-correct-ui-edited.md) 필요한 변경 작업을 수행하는 편집기입니다. 양식 필드를 자동으로 식별하고 식별된 필드를 한 유형에서 다른 유형으로 변환할 수 있습니다. 예를 들어, 양식의 두 열 레이아웃을 식별하고 라디오 단추로 자동 식별되는 필드를 여러 선택 항목 필드로 변경할 수 있습니다.
