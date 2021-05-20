---
title: '모범 사례 및 고려 사항 '
description: 게시 안 함
seo-description: 게시 안 함
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
source-git-commit: b2d29c22a275f2dc6a82593cf5e441c8da0bba13
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 4%

---


# 모범 사례 및 고려 사항 {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

AEM Forms 자동 변환 서비스는 PDF 양식을 적응형 양식으로 변환합니다. 이 서비스는 인공 지능과 기계 학습 알고리즘을 사용하여 소스 양식의 레이아웃과 필드를 파악합니다. 모든 기계 학습 서비스는 소스 데이터로부터 지속적으로 학습하고 이탈할 때마다 향상된 결과물을 생성합니다. 이런 서비스는 인간처럼 경험에서 배운다.

automated forms conversion 서비스는 다양한 형태로 교육됩니다. 소스 양식의 필드를 쉽게 식별하고 적응형 양식을 만듭니다. 하지만, PDF forms의 몇몇 분야와 스타일이 있는데, 그것은 사람의 눈에는 쉽게 보이기는 하지만 서비스에 대해서는 이해하기 어렵다. 이 서비스는 적용 가능한 필드 유형이나 패널과 다른 다른 유형을 일부 필드나 스타일에 할당할 수 있습니다. 이러한 모든 필드 및 스타일 패턴은 아래에 나와 있습니다.

서비스는 소스 데이터에서 계속 학습할 수 있도록 이러한 패턴에 올바른 필드 또는 패널을 식별하고 지정하기 시작합니다. 당분간 [검토 및 수정](review-correct-ui-edited.md) 편집기를 사용하여 이러한 문제를 해결할 수 있습니다. 문제 해결 또는 추가 읽기를 시작하기 전에 [적응형 양식 구성 요소](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)에 익숙해지십시오.

## 일반 {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">알려진 패턴 및 해상도</td> 
   <td width="70%">예</td> 
  </tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 채워진 PDF forms을 적응형 양식으로 전환하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>빈 적응형 양식을 사용합니다.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스가 치밀한 양식의 텍스트와 필드를 인식하지 못할 수 있습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>변환을 시작하기 전에 치밀한 양식의 텍스트와 필드 간의 너비를 늘립니다.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스가 스캔한 양식을 지원하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>스캔한 양식을 사용하지 마십시오. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 이미지 내에서 이미지와 텍스트를 추출하지 않습니다. </p> <p> </p> <p><strong>해상도</strong></p> <p>변환된 양식에 이미지나 텍스트를 수동으로 추가합니다.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>점선 또는 비투명 경계와 테두리가 있는 표는 변환되지 않습니다.</p> <p><strong>해상도</strong></p> <p>명확한 경계와 테두리가 있는 표를 사용합니다. 지원됨.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## 선택 그룹 {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">패턴</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>상자나 원이 아닌 셰이프가 있는 선택 그룹 옵션은 해당 적응형 양식 구성 요소로 변환되지 않습니다. </p> <p> </p> <p><strong>해상도</strong></p> <p>선택 옵션 셰이프를 상자 또는 원으로 변경하거나 검토 및 수정 편집기를 사용하여 셰이프를 식별합니다.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## 양식 필드 {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">패턴</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>패턴</strong></p> <p>서비스는 테두리가 지워지지 않은 필드를 식별하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 맨 아래 또는 오른쪽 식별되지 않은 위치에 캡션이 있는 일부 양식 필드를 남깁니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스가 서로 매우 가까운 위치에 배치되거나 테두리가 없는 일부 양식 필드에 잘못된 형식을 병합하거나 할당합니다. </p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스에서 멀리 있는 캡션 또는 캡션과 입력 필드 사이에 점선이 있는 필드를 인식하지 못할 수 있습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>명확한 경계로 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 해결하십시오.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## 목록 {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">패턴</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>양식 필드가 포함된 목록은 병합되거나 해당 적응형 양식 구성 요소로 변환되지 않습니다</p> <p><strong>해상도</strong></p> <p>명확한 경계로 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 해결하십시오.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 중첩된 목록 몇 개를 식별되지 않은 상태로 둘 수 있습니다</p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 문제를 수정합니다.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 선택 그룹이 포함된 일부 목록을 서로 병합합니다</p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 문제를 수정합니다.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

