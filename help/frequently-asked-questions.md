---
title: FAQ
seo-title: FAQ
description: 일반적인 쿼리 또는 FAQ
seo-description: 자동화된 Forms 전환 서비스에 대한 FAQ
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 92cd241915ef5818fb004a8982674b4f6753c171
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 4%

---


# FAQ{#frequently-asked-questions}

1. **자동화된 Forms 전환 서비스는 어떤 버전의 AEM Forms을 지원합니까?**

   <p>자동화된 Forms 전환 서비스는 AEM 6.4 Forms 및 AEM 6.5 Forms을 지원합니다. OSGi에서 AEM Forms과 JEE에서 AEM 양식을 모두 사용할 수 있습니다. 서비스를 사용하려면 AEM 작성자 인스턴스의 맨 위에 있는 최신 AEM Forms 추가 기능 패키지가 필요합니다. For detailed instructions, see <a href="configure-service.md">Configure the Automated Forms Conversion</a> service.</p> 
    <br>

1. **서비스를 자체적으로 설치할 수 있습니까?**

   <p>Adobe은 새로운 데이터 세트를 사용하여 자동화된 Forms 전환 서비스의 AI 및 ML 알고리즘을 정기적으로 교육하여 전환율 정확도를 높입니다. 업데이트된 알고리즘은 Adobe Cloud에서 실행되는 전환 서비스에 주기적으로 배포됩니다. 서비스의 모든 고객은 업데이트된 알고리즘으로 혜택을 받습니다. 따라서 클라우드 호스팅 중앙 배포는 모든 고객에게 지속적으로 향상된 기능을 학습하고 전달하는 데 가장 적합합니다.</p> 
    <p>서비스는 빈 양식을 응용 양식으로 변환합니다. 서비스는 채워진 양식과 채워진 양식의 데이터 추출을 지원하지 않습니다. 양식을 서비스로 변환하기 전에 채워진 양식에서 데이터를 제거하고 양식에서 독점 정보허용 목록에 추가하다를 제거 또는할 수 있습니다</p> <br>

1. **서비스는 모든 PDF forms 형식을 지원합니까? 지원되는 모든 언어는 무엇입니까?**

   <p>이 서비스는 비대화형 PDF forms, XFA 기반 XDP 및 PDF forms, AcroForms를 적응형 양식으로 변환할 수 있습니다. 서비스가 스캔하거나 채워진 양식을 지원하지 않습니다. 기타 제한 사항은 <a href="known-issues.md">알려진 문제</a> 문서를 참조하십시오.<br /> </p> 
    <p>다른 소스 유형에 대한 지원을 정기적으로 추가하고 있습니다. 최근에 추가된 기능 및 기능에 대한 정기적인 업데이트를 위해 <a href="introduction.md">지원되는PDF 양식</a> 섹션을 감시 목록에 유지하십시오.</p>

   이 서비스는 영어 양식만 적응형 양식으로 전환할 수 있습니다. You can translate the generated adaptive forms to another language using [AEM translation workflow.](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **서비스는 적응형 양식 대신 XDP를 생성할 수 있습니까?**

   <p>서비스는 XDP 출력을 생성하지 않습니다. 정기적으로 기능 및 서비스를 추가하고 있습니다. 최근에 추가된 기능과 기능을 <a href="introduction.md">정기적으로 업데이트하려면 지원되는 언어와 PDF forms</a> 섹션을 감시 목록에 두십시오.</p> <br>

1. **생성된 스키마의 유형은 무엇입니까?**

   <p>서비스를 사용하여 다음을 생성할 수 있습니다. </p>

   * JSON 스키마에 바인딩된 적응형 양식 및
   * 적응형 양식이 스키마에 바인딩되지 않음 <br><br>

1. **서비스가 Microsoft Word 양식을 응용 양식으로 변환할 수 있습니까?**

   <p>아니요. 서비스는 Microsoft Word 양식을 응용 양식으로 변환하지 않습니다. Microsoft Word 양식을 PDF 양식으로 저장하고 PDF 양식을 적응형 양식으로 변환할 수 있습니다. 전체 프로세스는 </p> <br>

   1. Adobe Acrobat을 사용하여 Word 문서를 [비대화형 PDF로 변환할 수 있습니다](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Adobe Acrobat을 사용하여 제작한 PDF forms을 입력 가능한 PDF 양식으로 [변환할 수 있습니다](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Adobe Acrobat을 사용하여 양식 필드를 수동으로 업데이트하고 수정할 수 있습니다.
   1. PDF 양식을 저장합니다. 이제 전환 서비스와 함께 양식을 사용하여 적응형 양식을 생성할 수 있습니다. 또한 양식을 기록 문서로 사용할 수도 있습니다.


1. **이 서비스는 스캔한 종이 양식과 컬러 양식을 적응형 양식으로 변환할 수 있습니까?**

   <p>이 서비스는 색상 PDF forms을 응용 양식으로 변환할 수 있습니다. 서비스가 스캔하거나 채워진 양식을 지원하지 않습니다. 기타 제한 사항은 <a href="known-issues.md">알려진 문제</a> 문서를 참조하십시오.</p> <br>

1. **서비스가 스캔한 양식이나 양식의 이미지만 응용 양식으로 변환할 수 있습니까?**

   <p>서비스는 스캔한 양식 또는 양식의 이미지를 즉시 적응형 양식으로 변환하는 것을 지원하지 않습니다. 그러나 Adobe Acrobat을 사용하면 양식의 이미지를 PDF 양식으로 전환할 수 있습니다. 그런 다음 이 서비스를 사용하여 PDF 양식을 적응형 양식으로 전환합니다. Acrobat에서 전환하려면 항상 고품질 양식 이미지를 사용하십시오. 전환 품질이 향상됩니다.</p> <br>

1. **일부 XDP 기반 양식에서는 양식 조각을 사용하며, 이러한 양식 조각을 어디에서 업로드해야 합니까?**

   <p class="MsoNormal">양식 조각을 전환 폴더에 업로드하고 원래 폴더 구조를 유지합니다. XDP 기반 양식 및 양식 조각에 사용되는 상대 경로를 유지하는 데 도움이 됩니다.</p> <br>

1. **서비스가 스키마 바인딩된 XDP 양식을 지원합니까? 스키마에 XDP가 바인딩되어 있는 경우 XDP에 스키마를 포함시켜야 합니까?**

   <p>예. 서비스는 스키마 바인딩된 XDP 양식을 지원하며 소스 XDP 양식에 스키마를 포함시켜야 합니다. 스키마 바인딩된 XDP 양식을 변환할 때 서비스는 JSON 스키마를 생성합니다. JSON 스키마는 소스 XDP 양식의 XSD 스키마와 구조적으로 유사합니다.</p> <br>

1. **서비스에서 양식을 변환하지 못했습니다. 이 문제를 해결하는 이유와 방법은?**
변환이 실패하는 가장 일반적인 이유는 다음과 같습니다.
</p>
   * 변환에 대해 보안 PDF forms이 제공됩니다. 변환에는 암호로 보호되거나 보안 PDF forms을 사용하지 마십시오.
   * 인터넷 연결이 중단되었습니다. 변환 중 인터넷에 연결되어 있는지 확인합니다.
   * 소스 PDF에는 실제 양식 대신 양식 이미지가 포함되어 있습니다.
   * 서비스가 잘못 구성되었거나, 서비스 URL이 제공되지 않았거나, 제공된 서비스 URL이 잘못되었습니다. > [>](configure-service.md#configure-the-cloud-service) >에서 **[!UICONTROL AEM]** **[!UICONTROL Tools]** 서비스 구성 **[!UICONTROL Cloud Services]** 을 **[!UICONTROL Automated Forms Conversion configuration]**&#x200B;확인하십시오.
   * IMS 구성이 제대로 구성되지 않았습니다. IMS 구성이 제대로 작동하는지 확인하려면 IMS 구성에 대한 상태 확인을 수행합니다. IMS 구성이 올바른지 확인하려면:
      1. 다음으로 이동:`http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. 구성을 선택합니다. 헤더에서 **[!UICONTROL Check Health]** 을 클릭하고 을 클릭합니다 **[!UICONTROL Check]**. 성공하면 **[!UICONTROL Token retrieved successfully!]** 메시지가 표시됩니다. <br> <br>

1. **사용자 정의 글꼴을 사용하는 것은 전환에 영향을 줍니까?**

   <p>비대화형 PDF 양식을 적응형 양식으로 변환하여 변환 품질을 향상시키면 글꼴이 PDF 양식에 포함됩니다. 글꼴 임베드 지원은 비대화형 PDF forms으로 제한됩니다. AcroForm 및 XFA 기반 PDF forms 변환을 최적화하기 위해 대체 글꼴이 사용됩니다.</p> 
    <p>CQ-DAM-Handler-Gibson Font Manager 서비스 <strong>구성의</strong> 고객 글꼴 디렉토리 <strong></strong> 필드에 나열된 사용자 정의 글꼴 디렉토리에 있는 양식만 비대화형 PDF 양식에 포함됩니다.</p> 
    <p> </p> <br>

1. **출력에서 소스 PDF 글꼴을 식별하고 사용합니까?**

   <p>반응형 HTML 양식의 스타일과 레이아웃은 일반적으로 PDF 또는 종이 기반 양식과 다릅니다. 조직 전체에서 일관된 레이아웃과 스타일을 지원하기 위해 적응형 양식에서는 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">테마를 사용하여 양식의 스타일을 지정합니다</a>. 전환 서비스는 전환 중에 적용된 테마에 지정된 글꼴 및 글꼴 스타일을 사용합니다. 테마의 글꼴 및 글꼴 스타일을 변경하여 적응형 양식의 구성 요소에 고유한 모양과 느낌을 제공할 수 있습니다.</p> <br>

1. **서비스가 XDP 기반 양식에서 JavaScript를 자동으로 추출하여 해당 적응형 양식에 적용합니까?**

   <p>이 서비스는 XFA 기반 양식 또는 Acro Forms의 스크립트를 해당 적응형 양식 규칙으로 자동 변환하지 않습니다. 양식 작성자(양식 작성자)는 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">규칙 편집기를</a> 사용하여 적응형 양식에 인터랙티브한 요소를 추가할 수 있습니다.</p> <br>

1. **일부 양식 개체가 응용 양식 구성 요소로 올바르게 변환되지 않습니다. 문제 해결 방법**

   <p>자동화된 Forms 전환 서비스는 다양한 형태로 교육됩니다. 그러나 AI/ML 기반의 애플리케이션은 교육 데이터와 패턴으로 제한됩니다. 다양한 필드 유형, 레이아웃, 패턴 및 상황에 따라 사람의 인사이트를 구별할 수 있지만 자동화된 인식으로 인식하기는 어려울 수 있습니다. 서비스가 이러한 개체를 식별하지 못하거나 잘못 인식할 수 있습니다. 검토 <a href="review-correct-ui-edited.md" target="_blank">및 수정</a> 편집기를 사용하여 입력 양식의 익숙한 종이 양식 레이아웃에서 필요한 사항을 수정할 수 있습니다.</p> <br/>

1. **양식에 일부 수정 사항이 반복됩니다. 서비스는 향후 전환에서 이러한 모든 인스턴스를 식별하고 수정할 수 있습니까?**

   이 서비스는 양식과 패턴에 대한 트레이닝을 일관되게 제공합니다. 매일 새로운 패턴을 학습합니다. 양식 전체에 걸쳐 반복된 교정 자동 적용을 아직 시작할 수 없습니다. 이러한 기능을 사용할 수 있도록 프리릴리스 양식에 주의하십시오. <br/><br/>

   메타 모델을 사용하여 양식 객체를 선택한 적응형 양식 구성 요소에 매핑하고 구성 요소의 유효성 검사, 규칙, 데이터 패턴, 도움말 텍스트 및 액세서빌러티 속성을 미리 구성할 수 있습니다. 전환 중에 지정된 모든 속성이 적용됩니다. 메타 모델을 사용하여 필드에 공통 속성을 적용할 수 있습니다. 양식 전체에서 반복되는 문제를 줄일 수 있습니다.<br/><br/>

1. **PII(개인 식별 정보) 정보와 같은 민감한 데이터가 있는 양식에 대한 옵션은 무엇입니까?**
서비스는 비어 있거나 채워지지 않은 양식만 지원합니다. 채워진 양식 또는 양식에 PII(개인 식별 정보)를 업로드하지 마십시오. 또한 소스 양식에서 미리 채워진 데이터, 개인 식별 정보(PII), 기밀 및 독점적 정보를 제거할 수 있습니다. 
<br/>

1. **머리글과 바닥글을 어디에 배치해야 합니까?**

   <p>적응형 양식 템플릿에 머리글과 바닥글을 배치합니다. 소스 PDF 양식에 머리글과 바닥글이 있는 경우 전환 중에 검색된 머리글과 바닥글을 감지하여 적응형 양식 템플릿에서 사용할 수 있는 머리글과 바닥글로 바꿉니다. 응용 양식에 추가 머리글이나 바닥글이 포함되어 있는 경우 <a href="review-correct-ui-edited.md">검토 및 수정</a> 편집기를 사용하여 이러한 머리글이나 바닥글을 수정하거나 제거할 수 있습니다.</p> <br />

1. **자산(테마, 템플릿) 생성, 적응형 양식 작성 및 게시 등의 수동 프로세스에 비해 서비스가 얼마나 절약됩니까?**

   <p>시간은 입력 양식의 크기와 복잡도와 요청 수에 따라 다릅니다. 이 서비스는 양식을 수동으로 변환하는 과정과 비교하여 PDF forms을 적응형 양식으로 보다 신속하게 변환하여 가치를 높이는 데 걸리는 시간을 크게 단축하고자 합니다. </p> <br />

1. **RSA 라이브러리와 관련된 오류가 발생하면 어떻게 해야 합니까? 오류 메시지는 아래에 언급된 메시지와 유사합니다.**<br/>

앞서 언급한 오류는 부팅 위임이 RSA/BouncyCastle 라이브러리에 대해 구성되지 않은 경우 발생합니다. 아래 단계를 수행하여 문제를 해결하십시오.   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
앞서 언급한 오류는 부팅 위임이 RSA/BouncyCastle 라이브러리에 대해 구성되지 않은 경우 발생합니다. 아래 단계를 수행하여 문제를 해결하십시오.
   <p> </p>

   1. AEM 인스턴스를 중지합니다. 폴더를 `[AEM installation directory]\crx-quickstart\conf\` 탐색합니다. 편집할 sling.properties 파일을 엽니다. AEM 인스턴스 `[AEM installation directory]\crx-quickstart\bin\start.bat` 를 시작하는 데 사용하는 경우 에 있는 sling.properties를 편집합니다 `[AEM_root]\crx-quickstart\`.
   1. sling.properties 파일에 다음 속성을 추가합니다.<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 파일을 저장하고 닫습니다. <br/>
   1. AEM 인스턴스를 시작합니다.<br/>

   <br/>

1. **적응형 양식 텍스트의 대소문자를 자동으로 변경하는 방법**

   <p>테마 또는 스타일 편집기에서 적응형 양식을 사용하여 적응형 양식 필드의 대소문자를 변경할 수 있습니다. 예를 들어 테마 편집기를 열고 양식의 모든 텍스트에 대한 Case 속성 값을 대문자, 소문자 또는 camelCase로 설정할 수 있습니다. 테마 편집기의 CSS 재정의 옵션을 사용하여 다양한 유형의 스타일을 만들 수도 있습니다.</p>

1. **자동화된 Forms 전환 서비스에서 Adobe Sign 텍스트 태그를 사용할 수 있습니까?**

   <p> 자동화된 Forms 전환 서비스를 사용하여 PDF 양식을 적응형 양식으로 변환하고 PDF 양식에 Adobe Sign 텍스트 태그가 있는 경우 이러한 태그는 해당 적응형 양식 필드로 변환되고 서명자 세부 정보가 자동으로 채워집니다.  이 기능은 Acro Forms에서만 사용할 수 있으며 적응형 양식은 제한된 수의 Adobe Sign 필드를 지원합니다.</p>  </br>

1. **Adobe Sign 사용 PDF 양식을 만드는 방법**

   </p>Adobe Sign 사용 PDF 양식을 만들려면:</p>

   필드 이름에 [Adobe Sign 텍스트 태그](https://helpx.adobe.com/sign/using/text-tag.html) 를 추가하거나 [Adobe Sign 양식으로 [변환] 옵션을](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html) 사용합니다.
