---
title: 'PDF 양식을 적응형 양식으로 전환 '
seo-title: 'PDF 양식을 적응형 양식으로 전환 '
description: 자동화된 양식 변환 서비스를 실행하여 PDF 양식을 적응형 양식으로 변환
seo-description: 자동화된 양식 변환 서비스를 실행하여 PDF 양식을 적응형 양식으로 변환
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: bcd55fa59f37b71b95b7cbfd80fcda368eaba408

---


# PDF 양식을 적응형 양식으로 전환 {#convert-print-forms-to-adaptive-forms}

Adobe Sensei 기반의 AEM Forms Automated Forms Conversion Service는 PDF 양식을 장치 친화적인 적응형 양식으로 자동 변환합니다. 비대화형 PDF 양식, Acro Forms 또는 XFA 기반 PDF 양식을 사용하는 경우 자동화된 양식 변환 서비스를 사용하면 이러한 양식을 적응형 양식으로 손쉽게 변환할 수 있습니다. 기능, 전환 워크플로우 및 온보딩 정보에 대한 자세한 내용은 자동화된 [양식 전환 서비스를](introduction.md) 참조하십시오.

## 전제 조건 {#pre-requisites}

* [**전환 서비스 구성&#x200B;**](configure-service.md)

* **변환된 양식에 적용할[템플릿을](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)준비합니다.** 템플릿을 사용하면 모든 적응형 양식에 일관된 브랜딩을 적용할 수 있습니다. 또한 자동화된 양식 변환 서비스는 소스 PDF 문서의 머리글과 바닥글을 추출하여 사용하지 않습니다. 적응형 양식 템플릿을 사용하여 머리글과 바닥글을 지정할 수 있습니다. 템플릿에 지정된 머리글과 바닥글은 변환 중 적응형 양식에 적용됩니다.

* **변환된 양식에 적용할[테마를](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)준비합니다.** 테마를 사용하면 조직의 모든 적응형 양식에 일관된 스타일을 적용할 수 있습니다.

## 전환 프로세스 시작 {#start-the-conversion-process}

AEM 인스턴스를 AEM Forms 전환 서비스와 연결하면 PDF 양식을 적응형 양식으로 변환할 수 있습니다. 양식을 변환하려면 나열된 순서대로 다음 단계를 수행하십시오.

* [AEM Forms 서버에 PDF 양식 업로드](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [전환 실행](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [변환된 양식 검토 및 수정](review-correct-ui-edited.md)

### AEM Forms 서버에 PDF 양식 업로드 {#upload-pdf-forms-to-your-aem-forms-server}

전환 서비스는 AEM Forms 인스턴스에서 사용할 수 있는 PDF 양식을 적응형 양식으로 변환합니다. 필요에 따라 모든 PDF 양식을 한 번에 또는 단계별로 업로드할 수 있습니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 폴더의 양식 수는 15개 미만으로 유지하고 폴더의 총 페이지 수는 50개 미만으로 유지합니다.
* 폴더 크기를 10MB 이하로 유지합니다. 양식을 하위 폴더에 보관하지 마십시오.
* 양식의 페이지 수를 15개 미만으로 유지합니다.
* 보호된 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 보호된 양식을 변환하지 않습니다.
* 파일 이름에 공백이 있는 소스 양식을 업로드하지 마십시오. 양식을 업로드하기 전에 파일 이름에서 공백을 제거합니다.
* [PDF 포트폴리오](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)를 업로드하지 마십시오. 이 서비스는 PDF 포트폴리오를 적응형 양식으로 전환하지 않습니다.
* 알려진 문제 [및](known-issues.md) 우수 사례 [및 고려 사항](styles-and-pattern-considerations-and-best-practices.md) 섹션을 읽고 양식을 제안된 대로 변경합니다.

AEM Forms 인스턴스의 폴더로 변환할 양식을 업로드하려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에 로그인합니다.

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL Folder]**. 폴더의 **제목** 및 **이름을** 지정합니다. 탭하기 **[!UICONTROL Create]**. 폴더가 생성됩니다.
1. 을 눌러 새로 만든 폴더를 엽니다.
1. 탭하기 **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. 업로드할 양식을 선택하고 클릭한 **[!UICONTROL Open]**&#x200B;다음 을 클릭합니다 **[!UICONTROL Upload]**. 양식이 업로드됩니다.

### 전환 실행 {#run-the-conversion}

양식을 업로드하고 서비스를 구성한 후 다음 단계를 수행하여 변환을 시작합니다.

1. AEM Forms 인스턴스에서 전환 설정 대화 **[!UICONTROL Adobe Experience Manager]** 상자 > ![>](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** 를 ![](assets/compass.png) 탭합니다 **[!UICONTROL Forms]** **[!UICONTROL Forms & Documents]**.
1. 양식이나 PDF 양식(변환할 양식)이 들어 있는 폴더를 선택하고 을 **[!UICONTROL Start Automated Conversion]**&#x200B;누릅니다. 대화 상자가 **[!UICONTROL Conversion Settings]** 나타납니다.

   ![구성 지정](assets/conversion-settings-dialog.png)

1. 전환 설정 대화 상자의 **[!UICONTROL Basic]** 탭에서 다음을 수행합니다.

   * **[!UICONTROL Select a cloud configuration]**. 구성을 선택하면 기본 템플릿과 테마가 이미 지정되어 있습니다. 필요한 경우 다른 템플릿 또는 테마를 지정할 수 있습니다.
   * 생성된 적응형 양식과 해당 스키마를 저장할 위치를 지정합니다. 기본 경로를 사용하거나 사용자 지정 경로를 지정할 수 있습니다.
   * 데이터 **모델 바인딩** 없이 적응형 양식 생성 옵션을 사용하여 데이터 모델 바인딩이 있거나 없는 적응형 양식을 생성할지 여부를 선택합니다.
이 옵션을 선택하지 않으면 전환 서비스는 적응형 양식을 JSON 스키마와 자동으로 연결하고 적응형 양식과 JSON 스키마로 사용할 수 있는 필드 간에 데이터 바인딩을 만듭니다. 이 **[!UICONTROL Save generated data model schema at]** 필드에는 생성된 JSON 스키마를 저장할 기본 위치가 표시됩니다. 생성된 스키마를 저장할 위치를 사용자 지정할 수도 있습니다.
이 옵션을 선택하면 변환 서비스는 데이터 모델 바인딩 없이 적응형 양식을 생성합니다. 변환 성공 후 적응형 양식을 양식 데이터 모델, XML 스키마 또는 JSON 스키마와 연결할 수 있습니다. 자세한 내용은 적응형 [양식](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)만들기를 참조하십시오.
   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. [전환 설정] 대화 상자의 **[!UICONTROL Additional]** 탭에서
   * 변환 서비스에서 변환된 양식의 양식 조각을 식별, 추출 및 다운로드할 수 있도록 하려면 이 **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 선택합니다. 이 **[!UICONTROL Extract fragment from adaptive forms]** 옵션을 선택하면 추출된 양식 조각 및 해당 양식 조각 스키마를 저장할 경로를 지정하는 옵션이 활성화됩니다.
   * 기존 JSON 스키마 기반 및 스키마 덜 적응형 양식 조각이 **[!UICONTROL existing adaptive form fragments]**&#x200B;있는 경우 해당 위치를 지정하고 이러한 조각을 자동으로 생성된 적응형 양식으로 사용할 계획입니다. 전환 서비스는 입력 PDF 양식(비대화형 PDF Forms 전용)을 사용하여 사용 가능한 JSON 스키마 기반 및 스키마 덜 적응형 양식 조각과 일치하며 일치하는 적응형 양식 조각이 해당 적응형 양식에서 사용됩니다.
   >[!NOTE]
   >
   >
   > * 한 번에 **[!UICONTROL  Extract Fragment]** 또는 **[!UICONTROL Use existing adaptive form fragments]** 옵션만 사용할 수 있습니다. 두 옵션을 동시에 사용할 수 없습니다.
   > * 이 **[!UICONTROL Use existing adaptive form fragments]** 옵션은 비대화형 PDF 양식에서만 사용할 수 있습니다. 다른 양식 유형은 아직 지원되지 않습니다.
   > * 자동화된 전환 서비스를 사용하면 JSON 스키마에 바인딩되는 언바운드 조각 또는 조각만 사용할 수 있습니다. XFA 조각을 사용하지 마십시오. XFA 조각은 지원되지 않습니다.


   * 데스크톱 및 랩탑과 같은 대형 화면에 대해 소스 양식의 레이아웃을 유지하려면 이 **[!UICONTROL Auto-detect multi-column layout of input forms]** 옵션을 선택합니다. 이 옵션은 소스 양식의 다중 열 레이아웃을 유지하는 데 유용합니다. 예를 들어 소스 PDF에 2열 레이아웃이 있는 경우 서비스는 대형 화면 디스플레이에 대한 2열 레이아웃과 휴대폰과 같은 작은 화면 장치에 대한 단일 열 레이아웃으로 출력 적응형 양식을 생성합니다. 이 기능에는 데이터 소스 스키마 구조에 알려진 몇 가지 문제가 있습니다. 자세한 내용은 [알려진 문제](known-issues.md) 문서를 참조하십시오.
   * 기본적으로 서비스는 PDF 양식의 각 페이지에 대해 별도의 최상위 패널을 만듭니다. 이제 이 **[!UICONTROL Auto-detect logical sections]** 옵션을 사용하여 페이지 수준 패널(페이지 번호 기반 패널)을 삭제하고 논리 패널만 만들 수 있습니다. 또한 논리 섹션과 논리 섹션의 필드가 인접한 두 페이지에 걸쳐 하나의 논리 섹션으로 분산되어 있는 섹션이 없는 필드를 분류합니다. 예를 들어 논리 섹션의 일부 필드가 페이지 1의 끝에 있고, 일부 필드가 페이지 2의 시작 부분에 있는 경우, 이러한 모든 필드가 단일 논리 섹션으로 컴파일됩니다.

      >[!NOTE]
      > 이 **[!UICONTROL Auto-detect logical sections]** 기능을 사용하려면 커넥터 패키지 1.1.38 이상이 필요합니다.



1. 탭하기 **[!UICONTROL Start Conversion]**. 전환이 시작되었습니다. 변환 진행 상태는 변환이 진행 중일 때까지 폴더나 양식에 표시됩니다. 전환이 완료된 후 메시지가 다른 상태 메시지(전환됨, 부분적으로 변환됨 또는 전환 실패)로 바뀝니다. 상태 이메일은 전환 완료 시 구성된 이메일 주소로도 전송됩니다.

   * 변환이 성공하면 변환된 적응형 양식과 관련 스키마가 변환 대화 상자의 **[!UICONTROL Basic]** 탭에 지정된 경로로 다운로드됩니다. 양식 조각 및 해당 스키마는 변환을 시작하기 전에 조각 추출 옵션을 선택한 경우에만 다운로드됩니다.
   * 변환 실패 시, 모든 입력 양식을 변환할 수 없거나 일부 입력 양식만 변환되지 않으면 메시지가 표시됩니다 **[!UICONTROL Conversion Failed]** **[!UICONTROL Partially Failed]** . 상태 이메일은 [구성된 이메일 주소에](configure-service.md#configureemailnotification) 전송되며 error.log 파일에 오류가 기록됩니다.
   XFA 기반 PDF 양식을 적응형 양식으로 변환하는 경우 변환 서비스는 PDF 양식을 변환된 적응형 양식으로 기록 문서 템플릿으로 자동 연관시킵니다. 전환 후 적응형 양식 속성을 열어 **[!UICONTROL Document of Record Template Configuration]** 탭의 **[!UICONTROL Form Model]** 섹션에서 기록 문서 템플릿을 볼 수 있습니다. </br>

   전환 서비스는 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 활성화한 경우에만 변환된 적응형 양식으로 PDF 양식을 자동으로 업로드합니다.

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
   >변환 프로세스가 60분 이상 걸리고 PDF 양식이 여전히 적응형 양식으로 변환되지 않는 경우 AEM Forms 인스턴스에 새 폴더를 만들고 PDF 양식을 새로 만든 폴더에 업로드한 다음 변환을 다시 시작합니다.

## Review and correct the converted forms {#review-and-correct-the-converted-forms}

실제 양식에는 복잡한 데이터 캡처 요구 사항이 있습니다. 자동 변환이 완료되면 고객은 양식의 전환 품질을 검토하고 필요한 업데이트를 수행할 수 있습니다. AEM Forms는 필요한 변경 작업을 수행하는 [검토 및 수정](review-correct-ui-edited.md) 편집기를 제공합니다. 양식 필드의 자동 식별을 개선하고 식별된 필드를 한 유형에서 다른 유형으로 변환할 수 있습니다. 예를 들어 양식의 두 열 레이아웃을 식별하고 라디오 단추로 자동 식별된 필드를 여러 선택 필드로 변경할 수 있습니다.
