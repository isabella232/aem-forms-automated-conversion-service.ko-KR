---
title: 변환 중 기록 문서 생성
seo-title: 변환 중 기록 문서 생성
description: 변환에 사용된 소스 양식 유형을 기반으로 DoR을 생성하는 데 권장되는 경로
seo-description: 변환에 사용된 소스 양식 유형을 기반으로 DoR을 생성하는 데 권장되는 경로
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
translation-type: tm+mt
source-git-commit: 640d72d7961ef0c2393bf0ae6745d918e388a056

---


# 적응형 양식의 기록 문서 생성을 활성화하는 권장 워크플로우 {#recommended-workflows-dor-generation}

기록 문서(DoR)를 사용하면 사용자가 제공한 정보를 기록하고 나중에 참조할 수 있도록 적응형 양식으로 제출할 수 있습니다.
DoR은 기본 템플릿을 사용하여 레이아웃을 정의합니다. 기본 템플릿을 사용하거나 다른 템플릿을 적응형 양식과 연결할 수 있습니다.

![생성된 기록 문서](assets/document_of_record.gif)

DoR 생성에 대한 자세한 내용은 적응형 [양식에](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)대한 기록 문서 생성을 참조하십시오.

자동화된 [양식 변환 서비스는](../help/introduction.md) 다음 소스 양식을 적응형 양식으로 변환합니다.

* 비대화형 PDF 양식
* Acro Forms
* XFA 기반의 PDF 양식

변환에 사용하는 소스 양식에 따라 다음을 사용하여 DoR을 생성할 수 있습니다.

* 기본 템플릿
* 소스 양식을 템플릿으로 사용 - 이 옵션을 선택하면 전환 서비스는 변환된 적응형 양식과 소스 양식을 DoR 템플릿으로 자동으로 연결합니다.
* 다른 템플릿과 변환된 적응형 양식 연결

다음 표에서는 사용하는 DoR 템플릿이 생성된 DoR의 레이아웃에 어떻게 영향을 주는지 보여 줍니다.

<table> 
 <tbody>
 <tr>
  <td><p><strong>소스 양식</strong></p></td>
  <td><p><strong>생성된 DoR</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>기본 템플릿을 사용하여 DoR을 생성하는 경우</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>소스 양식을 템플릿으로 사용하여 DoR을 생성하는 경우:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

표 그림과 같이 소스 양식을 템플릿으로 사용하면 DoR은 소스 양식의 레이아웃을 유지합니다.
이 문서에서는 세 가지 유형의 소스 양식을 기반으로 DoR을 생성하기 위해 권장되는 경로에 대해 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>소스 양식</strong></th> 
   <th><strong>DoR 생성 방법</strong></th> 
  </tr> 
  <tr> 
   <td><p>비대화형 PDF 양식</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">적응형 양식 변환 전에 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR 생성</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">적응형 양식 변환 후 적응형 양식 속성을 편집하여 기본값 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화합니다</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>Acro Forms 또는 XFA 기반 PDF 양식</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">적응형 양식 변환 전에 DoR 생성을 활성화하여 소스 양식을 템플릿으로 사용하여 DoR 생성</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">적응형 양식 변환 후 적응형 양식 속성을 편집하여 기본 템플릿, 소스 양식을 템플릿으로 사용 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화합니다</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## 비대화형 PDF 양식에 대한 기록 문서 생성 {#generate-document-of-record-non-interactive-pdf}

비대화형 PDF 양식을 자동화된 양식 변환 서비스의 소스 양식으로 사용하는 경우 다음을 수행할 수 있습니다.

* 적응형 양식 변환 전에 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR을 생성합니다.
* 또는 적응형 양식 변환 후 적응형 양식 속성을 편집하여 기본 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화하거나

### 변환 전 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR 생성 {#generate-document-of-record-using-cloud-configuration}

1. > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > 전환에 사용된 클라우드 구성의 속성 > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 선택합니다.

   ![클라우드 구성을 사용하여 기록 문서 생성](assets/generate_dor_cloud_config.gif)

1. 을 **[!UICONTROL Save & Close]** 눌러 설정을 저장합니다.

1. [변환을 실행합니다](../help/convert-existing-forms-to-adaptive-forms.md). 이러한 지침의 1단계에서 편집한 클라우드 구성을 사용해야 합니다.
변환된 응용 양식을 제출하면 기본 템플릿을 사용하여 DoR이 자동으로 생성됩니다.

### 전환 후 적응형 양식 속성을 편집하여 DoR 생성 활성화 {#edit-adaptive-form-properties-generate-document-of-record}

소스 양식을 적응형 양식으로 변환하기 전에 DoR 생성을 활성화하지 않는 경우 변환 후에도 계속 수행할 수 있습니다.

1. [비대화형 PDF 양식에서 변환을](../help/convert-existing-forms-to-adaptive-forms.md) 실행하여 적응형 양식을 생성합니다.

1. 폴더에서 적응형 양식을 선택하고 **[!UICONTROL output]** 을 누릅니다 **[!UICONTROL Properties]**.

1. 탭에서 **[!UICONTROL Form Model]** 섹션을 확장하고 **[!UICONTROL Document of Record Template Configuration]** **[!UICONTROL Generate Document of Record]**&#x200B;선택합니다.

   ![기록 문서 생성](assets/generate_dor_af_properties.png)

1. 을 **[!UICONTROL Save & Close]** 눌러 설정을 저장합니다.

변환된 응용 양식을 제출하면 기본 템플릿을 사용하여 DoR이 자동으로 생성됩니다. 다른 DoR 템플릿을 변환된 적응형 양식과 연결하려면 **[!UICONTROL Associate form template as the Document of Record template]** 옵션을 선택할 수 있습니다.

## Acrobat 양식 또는 XFA 기반 PDF 양식에 대한 기록 문서 생성 {#generate-document-of-record-acroform-xfaform}

Acro Form 또는 XFA 기반 PDF 양식을 자동화된 양식 변환 서비스의 소스 양식으로 사용하는 경우 다음을 수행할 수 있습니다.

* 적응형 양식 변환 전에 DoR 생성을 활성화하여 소스 양식을 템플릿으로 사용하여 DoR을 생성합니다.

* 기본 템플릿, 소스 양식 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화하기 위해 적응형 양식 변환 후 적응형 양식 속성을 편집하거나

### 변환 전에 DoR 생성을 활성화하여 소스 양식 템플릿을 사용하여 DoR 생성 {#use-input-form-as-template-to-generate-document-of-record}

1. > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > 전환에 사용된 클라우드 구성의 속성 > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 선택합니다.

1. 을 **[!UICONTROL Save & Close]** 눌러 설정을 저장합니다.

1. [변환을 실행합니다](../help/convert-existing-forms-to-adaptive-forms.md). 이러한 지침의 1단계에서 편집한 클라우드 구성을 사용해야 합니다.
변환 서비스는 Acro Form 또는 XFA 기반 PDF 양식을 DoR 템플릿으로 변환된 적응형 양식에 자동으로 연결합니다.
적응형 양식 속성을 열어 DoR 템플릿을 탭의 **[!UICONTROL Document of Record Template Configuration]** 섹션에서 볼 수 **[!UICONTROL Form Model]** 있습니다.

   ![적응형 양식 속성을 편집하여 기록 문서 생성](assets/generate_dor_af_properties_xdp_acro.png)

   변환된 응용 양식을 제출하면 DoR은 소스 양식 템플릿을 사용하여 자동으로 생성됩니다.

### 전환 후 적응형 양식 속성을 편집하여 DoR 생성 활성화 {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [비대화형 PDF 양식에서 변환을](../help/convert-existing-forms-to-adaptive-forms.md) 실행하여 적응형 양식을 생성합니다.

1. 폴더에서 적응형 양식을 선택하고 **[!UICONTROL output]** 을 누릅니다 **[!UICONTROL Properties]**.

1. 탭에서 **[!UICONTROL Form Model]** 섹션을 확장하고 기본 템플릿을 **[!UICONTROL Document of Record Template Configuration]** **[!UICONTROL Generate Document of Record]** 사용하여 DoR 생성을 사용하도록 선택합니다.
또한 이 **[!UICONTROL Associate form template as the Document of Record template]** 옵션을 선택하고 템플릿을 선택하여 소스 양식 템플릿 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화할 수 있습니다.

1. 을 **[!UICONTROL Save & Close]** 눌러 설정을 저장합니다.
