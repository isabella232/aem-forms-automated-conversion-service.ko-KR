---
title: '모범 사례 및 고려 사항 '
seo-title: '모범 사례 및 고려 사항 '
description: 자동화된 양식 변환 서비스에 대한 모범 사례 및 고려 사항
seo-description: 자동화된 양식 변환 서비스가 식별하기 어려운 소스 PDF 양식의 스타일 및 패턴 목록
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: cab926fc408a1a680853ee557e36354938f7424a

---


# 모범 사례 및 알려진 복잡한 패턴 {#Best-practices-and-considerations2}

이 문서에서는 양식 관리자, 작성자 및 개발자가 자동화된 양식 변환 서비스를 사용할 때 얻을 수 있는 지침과 권장 사항을 제공합니다. 또한 소스 양식 준비에서부터 자동 변환을 위한 추가 노력이 필요한 복잡한 패턴 수정에 이르기까지 모범 사례에 대해 설명합니다. 이러한 모범 사례는 자동화된 양식 변환 서비스의 전반적인 성능 및 출력에 기여합니다.

## 우수 사례

전환 서비스는 AEM Forms 인스턴스에서 사용할 수 있는 PDF 양식을 적응형 양식으로 변환합니다. 아래 나열된 우수 사례는 전환 속도와 정확도를 개선하는 데 도움이 됩니다. 또한 이러한 우수 사례는 전환 활동 후 체류 시간을 줄이는 데 도움이 됩니다.

### 소스를 업로드하기 전에

필요에 따라 모든 PDF 양식을 한 번에 또는 단계별로 업로드할 수 있습니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 폴더의 양식 수는 15개 미만으로 유지하고 폴더의 총 페이지 수는 50개 미만으로 유지합니다.
* 폴더 크기를 10MB 이하로 유지합니다. 양식을 하위 폴더에 보관하지 마십시오.
* 양식의 페이지 수를 15개 미만으로 유지합니다.
* 소스 문서를 8-15개의 문서로 일괄 구성할 수 있습니다. 일반적인 적응형 양식 조각으로 소스 양식을 한 번에 보관할 수 있습니다.
* 보호된 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 보호된 양식을 변환하지 않습니다.
* Do not upload the [PDF Portfolios](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html). 서비스는 PDF 포트폴리오를 적응형 양식으로 변환하지 않습니다.
* 스캔한 양식, 컬러, 영어 이외의 언어 및 채워진 양식을 업로드하지 마십시오. 이러한 양식은 지원되지 않습니다.
* 파일 이름에 공백이 있는 소스 양식을 업로드하지 마십시오. 양식을 업로드하기 전에 파일 이름에서 공백을 제거합니다.

변환을 위해 XDP 양식을 사용하는 경우 소스 XPD 양식을 업로드하기 전에 다음 단계를 수행하십시오.

* XDP 양식을 분석하고 시각적 문제를 수정합니다. 소스 문서에서 의도한 컨트롤과 구조를 사용하는지 확인합니다. 예를 들어 소스 양식에는 단일 선택 항목에 대한 라디오 단추 대신 확인란이 있을 수 있습니다. 확인란을 라디오 단추로 변경하여 원하는 구성 요소가 있는 응용 양식을 만듭니다.
* [변환을 시작하기 전에 XDP 양식에](http://www.adobe.com/go/learn_aemforms_designer_65) 바인딩을 추가합니다. 소스 XDP 양식에서 바인딩을 사용할 수 있으면 서비스는 변환 중에 해당 적응형 양식 필드에 바인딩을 자동으로 적용합니다. 바인딩을 수동으로 적용하는 데 필요한 시간을 절약할 수 있습니다.
* [XDP 파일에 Adobe Sign 태그를](https://helpx.adobe.com/sign/using/text-tag.html) 추가합니다. 서비스는 Adobe Sign 태그를 해당 적응형 양식 필드로 자동 변환합니다. 적응형 양식은 제한된 수의 Adobe Sign 필드를 지원합니다. 지원되는 전체 필드 목록은 적응형 양식 [](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) 문서에서 Adobe Sign 사용을 참조하십시오.
* XDP 문서의 하위 양식을 사용하여 적응형 양식으로 패널을 만들 수 있습니다. 전환 중에 서비스는 각 하위 양식을 응용 양식 패널로 변환합니다.
* 가능한 경우 XDP 문서의 복잡한 표를 간단한 표로 변환할 수 있습니다.

### 전환을 시작하기 전에

* 적응형 양식 템플릿 만들기 템플릿은 조직 또는 부서의 양식에 동일한 구조를 지정하는 데 도움이 됩니다.
* 적응형 양식 템플릿에서 머리글과 바닥글을 지정합니다. 서비스는 소스 문서의 머리글 바닥글을 무시하고 응용 양식 템플릿에 지정된 머리글/바닥글을 사용합니다.
* 적응형 양식 테마 제작 테마는 조직 또는 부서의 양식을 균일한 모양과 느낌을 제공합니다.
* 데이터 소스에서 저장 및 검색하도록 양식 데이터 모델을 구성합니다. 양식 데이터 모델에 대한 읽기 및 쓰기 서비스를 만들고 구성합니다.
* 응용 양식 조각을 만들고 응용 양식 조각을 사용하도록 서비스를 구성합니다.
* 비즈니스 프로세스 자동화가 필요한 양식에 대한 일반적인 워크플로우 모델을 준비할 수 있습니다.
* 필요한 경우 Adobe Analytics 구성


## 복잡한 패턴 파악

AEM Forms 자동 전환 서비스는 인공 지능 및 머신 러닝 알고리즘을 사용하여 소스 양식의 레이아웃과 필드를 파악합니다. 모든 머신 러닝 서비스는 소스 데이터를 지속적으로 학습하고 모든 이탈을 통해 향상된 출력을 생성합니다. 이러한 서비스는 인간처럼 경험에서 배운다.

자동화된 양식 변환 서비스는 다양한 양식을 기반으로 교육됩니다. 소스 양식의 필드를 손쉽게 식별하고 적응형 양식을 만듭니다. 그러나 PDF 양식에는 사람의 눈으로 쉽게 볼 수 있지만 서비스를 이해하기 어려운 일부 필드와 스타일이 있습니다. 서비스는 일부 필드 또는 스타일에 적용 가능한 필드 유형이나 패널과 다르게 지정할 수 있습니다. 이러한 모든 필드 및 스타일 패턴은 아래에 나열되어 있습니다.

서비스는 소스 데이터를 계속 학습할 때 이러한 패턴에 올바른 필드나 패널을 찾아 지정하기 시작합니다. 당분간은 검토 및 수정 [편집기를 사용하여](review-correct-ui-edited.md) 이러한 문제를 수정할 수 있습니다. 문제를 수정하거나 더 자세히 읽기 전에 [적응형 양식 구성 요소에](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)익숙해지십시오.

### 일반 패턴 {#general}

| 패턴 | 예 |
|--- |--- |
| **Pattern** Service는 컬러 PDF 양식을 적응형 양식으로 변환하지 않습니다 <br> . <br><br>**해상도&#x200B;**흑백 또는 회색 음영 PDF 양식을 사용합니다<br>. | ![컬러 양식](assets/best-practice-coloured-forms.png) |
| **패턴** 서비스는 <br>채워진 PDF 양식을 적응형 양식으로 변환하지 않습니다. <br><br>**해상도&#x200B;**빈<br>적응형 양식을 사용합니다. | ![채워진 양식](assets/best-practice-filled-forms.png) |
| **패턴** 서비스는 <br>덴스 양식의 텍스트와 필드를 인식하지 못할 수 있습니다. <br><br>**해상도&#x200B;**<br>변환을 시작하기 전에 밀도가 높은 양식의 텍스트와 필드 사이의 너비를 늘립니다. |  |
| **패턴** 서비스는 <br>스캔한 양식을 지원하지 않습니다. <br><br>**해상도&#x200B;**<br>스캔한 양식을 사용하지 마십시오. | ![스캔한 양식](assets/scanned-forms.png) |
| **패턴** 서비스는 <br>이미지 내에서 이미지와 텍스트를 추출하지 않습니다. <br><br>**해상도&#x200B;**변환된<br>양식에 이미지 또는 텍스트를 수동으로 추가합니다. | ![텍스트 양식이 있는 이미지](assets/best-practice-image-with-text.png) |
| **점선** 또는 <br>비투명 경계와 테두리가 있는 패턴 테이블은 변환되지 않습니다. <br><br>**해상도&#x200B;**명확한<br>경계와 테두리가 있는 표를 사용합니다. 지원됨. | ![테이블 양식 지우기](assets/best-practice-table-dotted-non-clear.png) |
| **패턴** 적응형 양식은 <br> 상자 밖으로 세로 텍스트를 지원하지 않습니다. 따라서 서비스는 세로 텍스트를 해당 적응형 양식 텍스트로 변환하지 않습니다. <br><br>**해상도&#x200B;**<br>적응형 양식 편집기를 사용하여 필요한 경우 세로 텍스트를 추가합니다. | ![테이블 양식 지우기](assets/vertical-text.png) |



### 선택 그룹 {#choice-group}

| 패턴 | 해상도 |
|--- |--- |
| **상자** 또는 원이 아닌 모양이 있는 패턴 <br> 선택 그룹 옵션은 해당 적응형 양식 구성 요소로 변환되지 않습니다. <br><br>**해상도&#x200B;**<br>선택 옵션 모양을 상자 또는 원으로 변경하거나 검토 및 수정 편집기를 사용하여 모양을 식별합니다. | ![Choice 필드 ](assets/best-practice-choice-group-options.png) |

### 양식 필드 {#form-fields}

| 패턴 | 해상도 |
|--- |--- |
| **패턴** 서비스는 <br> 테두리를 지우지 않으면 필드를 식별하지 않습니다. <br><br>**해결&#x200B;**: 검토<br>및 수정 편집기를 사용하여 이러한 필드를 식별합니다. | ![불명확한 경계로 된 필드](assets/best-practice-fields-without-clear-borders.png) |
| **패턴** 서비스는 <br> 양식의 맨 아래 또는 오른쪽에 캡션이 있는 일부 선택 그룹 양식 필드를 식별하지 못할 수 있습니다. <br><br>**해결&#x200B;**: 검토<br>및 수정 편집기를 사용하여 해당 필드 식별 | ![Choice 필드](assets/best-practice-caption-bottom-right.png) |
| **Pattern** Service는 <br> 서로 매우 가깝게 배치되거나 경계가 명확하지 않은 일부 양식 필드에 잘못된 유형을 병합 또는 할당합니다. <br><br>**해결&#x200B;**: 검토<br>및 수정 편집기를 사용하여 이러한 필드를 식별합니다. | ![Choice 필드](assets/best-practice-placed-very-near.png) |
| **패턴** 서비스는 <br> 멀리 떨어져 있는 캡션이나 캡션과 입력 필드 사이에 있는 점선이 있는 필드를 인식하지 못할 수 있습니다. <br><br>**해결책&#x200B;**명확한 경계가 있는 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 수정할 수 있습니다<br>. | ![멀리 떨어진 필드 또는 자막 필드 사이의 점선](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### 목록 {#lists}

| 패턴 | 해상도 |
|--- |--- |
| **양식** 필드가 포함된 패턴 <br>목록은 병합되거나 해당 적응형 양식 구성 요소로 변환되지 않습니다. <br><br>**해상도&#x200B;**<br>명확한 경계가 있는 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 수정할 수 있습니다. | ![선택 그룹이 포함된 목록](assets/best-practice-lists-containing-form-fields.png) |
| **Pattern** Service는 <br>확인되지 않은 몇 개의 중첩된 목록을 <br><br>**남겨 두어서&#x200B;**이러한<br>문제를 수정할 수 있습니다. 검토 및 수정 편집기를 사용합니다. | ![선택 그룹이 포함된 목록](assets/best-practice-nested-lists.png) |
| **Pattern** Service는 선택 그룹이 포함된 일부 목록을 다른 Resolution <br> Use Review and Correct <br><br>**편집기와 결합하여&#x200B;**<br>이러한 문제를 수정합니다. | ![선택 그룹이 포함된 목록](assets/best-practice-check-box-in-table-cells.png) |

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
