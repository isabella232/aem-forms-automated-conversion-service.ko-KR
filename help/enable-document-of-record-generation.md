---
title: 전환 중 기록 문서 생성
seo-title: 전환 중 기록 문서 생성
description: 변환에 사용되는 소스 양식 유형에 따라 DoR을 생성하는 데 권장되는 경로입니다.
seo-description: 변환에 사용되는 소스 양식 유형에 따라 DoR을 생성하는 데 권장되는 경로입니다.
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
exl-id: c24313cd-2b9b-4209-9505-a8e14d8dc530
source-git-commit: 1a3f79925f25dcc7dbe007f6e634f6e3a742bf72
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 3%

---

# 적응형 양식의 기록 문서 생성 활성화를 위한 권장 워크플로우 {#recommended-workflows-dor-generation}

레코드 문서(DoR)를 사용하면 제공하는 정보의 레코드를 보관하고 나중에 참조할 수 있도록 적응형 양식으로 제출할 수 있습니다.
DoR에서는 기본 템플릿을 사용하여 레이아웃을 정의합니다. 기본 템플릿을 사용하거나 다른 템플릿을 적응형 양식과 연결할 수 있습니다.

![생성된 레코드 문서](assets/document_of_record.gif)

DoR 생성에 대한 자세한 내용은 적응형 양식에 대한 레코드 문서 생성](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)을 참조하십시오.[

[Automated forms conversion 서비스](../help/introduction.md)는 다음 소스 양식을 적응형 양식으로 변환합니다.

* 비대화형 PDF forms
* 아크로 Forms
* XFA 기반 PDF forms

변환에 사용하는 소스 양식을 기반으로 다음을 사용하여 DoR을 생성할 수 있습니다.

* 기본 템플릿
* 소스 양식을 템플릿으로 사용 - 이 옵션을 선택하면 변환 서비스는 소스 양식을 DoR 템플릿으로 변환된 적응형 양식과 자동으로 연결합니다.
* 변환된 적응형 양식과 다른 템플릿 연결

다음 표에서는 사용하는 DoR 템플릿이 생성된 DoR 레이아웃에 미치는 영향에 대한 예를 보여 줍니다.

<table> 
 <tbody>
 <tr>
  <td><p><strong>소스 양식</strong></p></td>
  <td><p><strong>생성된 DoR</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>기본 템플릿을 사용하여 DoR을 생성하는 경우:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>소스 양식을 템플릿으로 사용하여 DoR을 생성하는 경우:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

표에 표시된 대로 소스 양식을 템플릿으로 사용하는 경우 DoR은 소스 양식의 레이아웃을 유지합니다.
이 문서에서는 세 가지 유형의 소스 양식을 기반으로 DoR을 생성하는 데 권장되는 경로에 대해 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>소스 양식</strong></th> 
   <th><strong>DoR 생성 방법</strong></th> 
  </tr> 
  <tr> 
   <td><p>비대화형 PDF forms</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">적응형 양식 전환 전에 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR을 생성합니다</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">적응형 양식 전환 후 적응형 양식 속성을 편집하여 기본값 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화합니다</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>Acro Forms 또는 XFA 기반 PDF forms</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">적응형 양식 변환 전에 DoR 생성을 활성화하여 소스 양식을 템플릿으로 사용하여 DoR을 생성합니다</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">적응형 양식 전환 후 적응형 양식 속성을 편집하여 기본 템플릿, 소스 양식을 템플릿으로 사용하거나 기타 양식 템플릿을 사용하여 DoR 생성을 활성화합니다</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## 비대화형 PDF forms에 대한 레코드 문서 생성 {#generate-document-of-record-non-interactive-pdf}

비대화형 PDF 양식을 Automated forms conversion 서비스의 소스 양식으로 사용하는 경우 다음을 수행할 수 있습니다.

* 적응형 양식 변환 전에 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR을 생성합니다.
* 적응형 양식 변환 후 적응형 양식 속성을 편집하거나 기본 또는 기타 양식 템플릿을 사용하여 DoR 생성을 사용하도록 설정합니다

### 변환 전 DoR 생성을 활성화하여 기본 템플릿 {#generate-document-of-record-using-cloud-configuration}을 사용하여 DoR을 생성합니다.

1. **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > 변환에 사용된 클라우드 구성의 속성 > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 선택합니다.

   ![클라우드 구성을 사용하여 기록 문서 생성](assets/generate_dor_cloud_config.gif)

1. **[!UICONTROL Save & Close]** 을 눌러 설정을 저장합니다.

1. [전환을 실행합니다](../help/convert-existing-forms-to-adaptive-forms.md). 이러한 지침의 1단계에서 편집한 클라우드 구성을 사용해야 합니다.
변환된 적응형 양식 제출 시 DoR은 기본 템플릿을 사용하여 자동으로 생성됩니다.

### 전환 후 적응형 양식 속성을 편집하여 DoR 생성 {#edit-adaptive-form-properties-generate-document-of-record} 을 사용하도록 설정

소스 양식을 적응형 양식으로 전환하기 전에 DoR 생성을 활성화하지 않은 경우 전환 후에도 계속 그렇게 할 수 있습니다.

1. [비대화형 ](../help/convert-existing-forms-to-adaptive-forms.md) PDF 양식에서 전환을 실행하여 적응형 양식을 생성합니다.

1. **[!UICONTROL output]** 폴더에서 적응형 양식을 선택하고 **[!UICONTROL Properties]** 을 누릅니다.

1. **[!UICONTROL Form Model]** 탭에서 **[!UICONTROL Document of Record Template Configuration]** 섹션을 확장하고 **[!UICONTROL Generate Document of Record]**&#x200B;를 선택합니다.

   ![기록 문서 생성](assets/generate_dor_af_properties.png)

1. **[!UICONTROL Save & Close]** 을 눌러 설정을 저장합니다.

변환된 적응형 양식 제출 시 DoR은 기본 템플릿을 사용하여 자동으로 생성됩니다. 다른 DoR 템플릿을 변환된 적응형 양식과 연결하려면 **[!UICONTROL Associate form template as the Document of Record template]** 옵션을 선택할 수 있습니다.

## Acro Forms 또는 XFA 기반 PDF forms에 대한 레코드 문서 생성 {#generate-document-of-record-acroform-xfaform}

Acro Form이나 XFA 기반 PDF 양식을 Automated forms conversion 서비스의 소스 양식으로 사용하는 경우 다음을 수행할 수 있습니다.

* 적응형 양식 변환 전에 DoR 생성을 활성화하여 소스 양식을 템플릿으로 사용하여 DoR을 생성합니다.

* 적응형 양식 변환 후 적응형 양식 속성을 편집하거나 기본 템플릿, 소스 양식을 템플릿으로 사용하거나 기타 양식 템플릿을 사용하여 DoR 생성을 사용하도록 설정합니다

### 변환 전 DoR 생성을 활성화하여 소스 양식 서식 파일 {#use-input-form-as-template-to-generate-document-of-record} 을 사용하여 DoR을 생성합니다.

1. **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > 변환에 사용된 클라우드 구성의 속성 > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 선택합니다.

1. **[!UICONTROL Save & Close]** 을 눌러 설정을 저장합니다.

1. [전환을 실행합니다](../help/convert-existing-forms-to-adaptive-forms.md). 이러한 지침의 1단계에서 편집한 클라우드 구성을 사용해야 합니다.
변환 서비스는 Acro 양식 또는 XFA 기반 PDF 양식을 DoR 템플릿으로 변환된 적응형 양식에 자동으로 연결합니다.
적응형 양식 속성을 열어 **[!UICONTROL Form Model]** 탭의 **[!UICONTROL Document of Record Template Configuration]** 섹션에서 DoR 템플릿을 볼 수 있습니다.

   ![적응형 양식 속성을 편집하여 레코드 문서 생성](assets/generate_dor_af_properties_xdp_acro.png)

   변환된 적응형 양식 제출 시 DoR은 소스 양식 템플릿을 사용하여 자동으로 생성됩니다.

### 전환 후 적응형 양식 속성을 편집하여 DoR 생성 {#edit-adaptive-form-properties-to-generate-document-of-record} 을 사용하도록 설정

1. [비대화형 ](../help/convert-existing-forms-to-adaptive-forms.md) PDF 양식에서 전환을 실행하여 적응형 양식을 생성합니다.

1. **[!UICONTROL output]** 폴더에서 적응형 양식을 선택하고 **[!UICONTROL Properties]** 을 누릅니다.

1. **[!UICONTROL Form Model]** 탭에서 **[!UICONTROL Document of Record Template Configuration]** 섹션을 확장하고 **[!UICONTROL Generate Document of Record]** 를 선택하여 기본 템플릿을 사용하여 DoR 생성을 활성화합니다.
**[!UICONTROL Associate form template as the Document of Record template]** 옵션을 선택하고 템플릿을 선택하여 소스 양식 서식 파일 또는 기타 양식 서식 파일을 사용하여 DoR 생성을 활성화할 수도 있습니다.

1. **[!UICONTROL Save & Close]** 을 눌러 설정을 저장합니다.
