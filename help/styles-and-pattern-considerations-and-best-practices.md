---
title: '모범 사례 및 고려 사항 '
seo-title: '모범 사례 및 고려 사항 '
description: automated forms conversion 서비스에 대한 모범 사례 및 고려 사항
seo-description: automated forms conversion 서비스가 식별하기 어려운 소스 PDF forms의 스타일 및 패턴 목록
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: e2298422e0af9b1c678e7604be3efb6da377d7dd
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 2%

---


# 모범 사례 및 알려진 복잡한 패턴 {#Best-practices-and-considerations2}

이 문서에서는 양식 관리자, 작성자 및 개발자가 [!DNL Automated Forms Conversion service] 작업 시 활용할 수 있는 지침과 권장 사항을 제공합니다. 또한 소스 양식 준비에서부터 자동화된 전환을 위한 추가 노력이 필요한 복잡한 패턴을 수정하는 등 모범 사례에 대해 살펴봅니다. 이러한 우수 사례를 통칭하여 [!DNL Automated Forms Conversion service]의 전체 성능 및 출력에 기여합니다.

## 모범 사례

전환 서비스는 AEM [!DNL Forms] 인스턴스에서 사용할 수 있는 PDF forms을 적응형 양식으로 변환합니다. 아래 나와 있는 모범 사례는 전환 속도와 정확도를 개선하는 데 도움이 됩니다. 또한 이러한 우수 사례는 전환 활동 후 체류 시간을 줄이는 데 도움이 됩니다.

### 소스를 업로드하기 전에

필요에 따라 모든 PDF forms을 한 번에 또는 단계적으로 업로드할 수 있습니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 한 폴더에 있는 양식 수를 15개 미만으로 유지하고 폴더의 총 페이지 수를 50개 미만으로 유지합니다.
* 폴더 크기를 10MB 이하로 유지합니다. 하위 폴더에 양식을 보관하지 마십시오.
* 양식의 페이지 수를 15개 미만으로 유지합니다.
* 소스 문서를 8-15개의 문서로 일괄 구성할 수 있습니다. 일반적인 적응형 양식 조각으로 소스 양식을 한 번에 보관할 수 있습니다.
* 보호된 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 보호된 양식을 변환하지 않습니다.
* [PDF Portfolio](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)을(를) 업로드하지 마십시오. 서비스는 PDF Portfolio을 적응형 양식으로 변환하지 않습니다.
* 스캔한 양식, 영어 이외의 언어 및 채워진 양식을 업로드하지 마십시오. 이러한 양식은 지원되지 않습니다.
* 파일 이름에 공백이 포함된 소스 양식을 업로드하지 마십시오. 양식을 업로드하기 전에 파일 이름에서 공간을 제거합니다.

변환을 위해 XDP 양식을 사용하는 경우 소스 XPD 양식을 업로드하기 전에 다음 단계를 수행하십시오.

* XDP 양식을 분석하고 시각적 문제를 수정합니다. 소스 문서에서 의도된 컨트롤과 구조를 사용하는지 확인합니다. 예를 들어 소스 양식에는 단일 선택 항목에 대한 라디오 단추 대신 확인란이 있을 수 있습니다. 원하는 구성 요소가 포함된 적응형 양식을 만들려면 확인란을 라디오 단추로 변경합니다.
* [변환을 시작하기 전에 XDP ](http://www.adobe.com/go/learn_aemforms_designer_65) 형식에 바인딩을 추가합니다. 소스 XDP 양식에서 바인딩을 사용할 수 있으면 서비스는 변환 중 해당 적응형 양식 필드에 바인딩을 자동으로 적용합니다. 바인딩을 수동으로 적용하는 데 필요한 시간을 저장합니다.
* [XDP ](https://helpx.adobe.com/sign/using/text-tag.html) 파일에 Adobe Sign 태그를 추가합니다. 서비스는 Adobe Sign 태그를 해당 적응형 양식 필드로 자동으로 변환합니다. 적응형 Forms은 제한된 수의 Adobe Sign 필드를 지원합니다. 지원되는 전체 필드 목록은 적응형 양식](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) 설명서에서 [Adobe Sign 사용을 참조하십시오.
* 가능한 경우 XDP 문서의 복잡한 표를 간단한 테이블로 변환할 수 있습니다. 표 셀의 양식 필드, 불규칙한 크기 셀, 행 또는 열 스팬 셀, 병합된 셀, 부분 테두리 또는 보이지 않는 테두리가 있는 표는 복잡한 표로 간주됩니다. 위에 언급된 항목 중 하나가 있는 테이블은 복잡한 테이블로 간주됩니다.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### 전환을 시작하기 전에

* 적응형 양식 템플릿을 만듭니다. 템플릿을 사용하면 조직 또는 부서의 양식에 동일한 구조를 지정할 수 있습니다.
* 적응형 양식 템플릿에서 머리글과 바닥글을 지정합니다. 이 서비스는 소스 문서의 머리글 바닥글을 무시하고 적응형 양식 템플릿에 지정된 머리글-바닥글을 사용합니다.
* 적응형 양식 테마 만들기 테마는 조직 또는 부서의 형식에 균일한 모양과 느낌을 제공합니다.
* 데이터 소스에서 저장하고 검색할 양식 데이터 모델을 구성합니다. 양식 데이터 모델에 대한 읽기 및 쓰기 서비스를 만들고 구성합니다.
* 응용 양식 조각을 만들고 응용 양식 조각을 사용하도록 서비스를 구성합니다.
* 비즈니스 프로세스 자동화가 필요한 양식에 대한 일반적인 워크플로우 모델을 준비할 수 있습니다.
* 필요한 경우 Adobe Analytics 구성


## 복잡한 패턴 파악

AEM [!DNL Forms Automated Conversion service]은(는) 인공 지능과 기계 학습 알고리즘을 사용하여 소스 양식의 레이아웃과 필드를 파악합니다. 모든 머신 러닝 서비스는 소스 데이터를 지속적으로 학습하여 모든 이탈률을 바탕으로 향상된 출력을 제작합니다. 이러한 서비스는 인간처럼 경험을 통해 배운다.

[!DNL Automated Forms Conversion service] 다양한 형태로 교육됩니다. 소스 양식의 필드를 손쉽게 식별하고 적응형 양식을 만듭니다. 그러나 PDF forms에는 사람의 눈에는 쉽게 보이기는 하지만 서비스에 대해서는 이해하기 어려운 분야와 스타일이 있다. 서비스는 일부 필드 또는 스타일에 적용 가능한 필드 유형이나 패널과 다르게 지정할 수 있습니다. 이러한 모든 필드 및 스타일 패턴이 아래에 나열됩니다.

서비스는 소스 데이터를 계속 학습하면서 이러한 패턴에 올바른 필드나 패널을 식별하고 할당합니다. 당분간은 [검토 및 수정](review-correct-ui-edited.md) 편집기를 사용하여 이러한 문제를 수정할 수 있습니다. 문제를 수정하거나 더 읽기 전에 [적응형 양식 구성 요소](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)에 익숙해지십시오.

### 일반 패턴 {#general}

| 패턴 | 예 |
|--- |--- |
| **PatternService** <br>는 채워진 PDF forms을 적응형 양식으로 변환하지 않습니다. <br><br>**** <br>해상도빈 적응형 양식을 사용합니다. | ![채워진 양식](assets/best-practice-filled-forms.png) |
| **PatternService** <br>는 덴스 양식의 텍스트와 필드를 인식하지 못할 수 있습니다. <br><br>**** <br> 해상도변환을 시작하기 전에 덴스 양식의 텍스트와 필드 사이의 너비를 늘립니다. |  |
| **PatternService** <br>는 스캔한 양식을 지원하지 않습니다. <br><br>**** <br>해상도스캔한 양식을 사용하지 마십시오. | ![스캔한 양식](assets/scanned-forms.png) |
| **PatternService** <br>는 이미지 내의 이미지와 텍스트를 추출하지 않습니다. <br><br>**** <br> 해상도변환된 양식에 이미지나 텍스트를 수동으로 추가할 수 있습니다. | ![텍스트 양식이 있는 이미지](assets/best-practice-image-with-text.png) |
| **** <br>점선 또는 비투명 경계와 테두리가 있는 PatternTables는 변환되지 않습니다. <br><br>**** <br>해상도명확한 경계와 테두리가 명확한 표를 사용합니다. 지원. | ![테이블 양식 지우기 안 함](assets/best-practice-table-dotted-non-clear.png) |
| **PatternAdaptive** <br> 양식은 상자 밖으로 세로 텍스트를 지원하지 않습니다. 따라서 이 서비스는 세로 텍스트를 해당 적응형 Forms 텍스트로 변환하지 않습니다. <br><br>**** <br> 해상도필요한 경우 적응형 양식 편집기를 사용하여 세로 텍스트를 추가합니다. | ![테이블 양식 지우기 안 함](assets/vertical-text.png) |



### 선택 그룹 {#choice-group}

| 패턴 | 해상도 |
|--- |--- |
| **상자 또는 원이 아닌 모양이 있는** <br> PatternChoice 그룹 옵션은 해당 적응형 양식 구성 요소로 변환되지 않습니다. <br><br>**** <br> 해상도선택 옵션 모양을 상자 또는 원으로 변경하거나 검토 및 수정 편집기를 사용하여 모양을 식별합니다. | ![Choice Fileds  ](assets/best-practice-choice-group-options.png) |

### 양식 필드 {#form-fields}

| 패턴 | 해상도 |
|--- |--- |
| **PatternService** <br> 는 테두리를 지우지 않고 필드를 식별하지 않습니다. <br><br>**** <br> 해결 방법검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다. | ![경계를 비명확하게 하는 필드](assets/best-practice-fields-without-clear-borders.png) |
| **PatternService** <br> 는 양식의 맨 아래 또는 오른쪽에 캡션이 있는 일부 선택 그룹 양식 필드를 식별할 수 없습니다. <br><br>**해결** <br> 방법검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다 | ![Choice Fileds](assets/best-practice-caption-bottom-right.png) |
| **PatternService** <br> 는 서로 매우 가깝게 배치되거나 테두리가 명확하지 않은 일부 양식 필드에 잘못된 유형을 병합하거나 할당합니다. <br><br>**** <br> 해결 방법검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다. | ![Choice Fileds](assets/best-practice-placed-very-near.png) |
| **PatternService** <br> 는 멀리 있는 캡션 또는 캡션과 입력 필드 사이에 점선이 있는 필드를 인식하지 못할 수 있습니다. <br><br>**** <br> 해결명확한 경계가 있는 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 해결할 수 있습니다. | ![멀리 떨어진 필드 또는 자막 필드 사이의 점선](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### 목록 {#lists}

| 패턴 | 해상도 |
|--- |--- |
| **양식** <br>필드가 포함된 목록은 병합되거나 해당 적응형 양식 구성 요소로 변환되지 않습니다. <br><br>**** <br>해결 방법경계가 분명한 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 해결하십시오. | ![선택 그룹이 포함된 목록](assets/best-practice-lists-containing-form-fields.png) |
| **PatternService** <br>는 몇 개의 중첩된 목록 중 확인되지 않은 ResolutionReview  <br><br>**** <br> 및 Correct 편집기를 사용하여 이러한 문제를 수정할 수 있습니다. | ![선택 그룹이 포함된 목록](assets/best-practice-nested-lists.png) |
| **PatternService는 선택 그룹이 포함된 일부 목록을 다른 ResolutionReview 및 Correct** <br>   <br><br>**** <br> 편집기를 사용하여 이러한 문제를 수정합니다. | ![선택 그룹이 포함된 목록](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
