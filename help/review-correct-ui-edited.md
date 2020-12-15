---
title: 전환된 양식 검토 및 수정
seo-title: 전환된 양식 검토 및 수정
description: automated forms conversion 서비스에서 변환된 적응형 양식을 검토하고 수정합니다.
seo-description: automated forms conversion 서비스에서 변환된 적응형 양식을 검토하고 수정합니다.
uuid: 5a0a6d24-dff6-4732-b607-24848b07b26d
topic-tags: forms
discoiquuid: f45ab2d7-5234-42d6-aeb6-b2cb1a7ce3c2
translation-type: tm+mt
source-git-commit: 3c12751cad2b3c04ad66a98ac17f20f648530d0f
workflow-type: tm+mt
source-wordcount: '2536'
ht-degree: 0%

---


# 전환된 양식 검토 및 수정{#review-and-correct-converted-forms}

AEM Forms Automated forms conversion 서비스는 입력 PDF 문서의 필드, 내용 및 레이아웃을 식별하며 PDF 문서를 적응형 양식으로 변환합니다. 출력 적응형 양식에는 몇 개의 필드가 누락되거나 잘못 변환될 수 있습니다. 검토 및 수정 편집기를 사용하여 식별된 필드를 향상시키고 적응형 양식을 다시 생성하여 원하는 경험에 가까운 출력물을 얻을 수 있습니다. 첫 번째 변환 후 편집기에서 입력 PDF 문서를 열어 다음 작업을 수행할 수 있습니다.

* 전환 중에 식별된 모든 필드 및 컨텐츠 보기
* 전환 중 누락된 필드 및 컨텐츠 식별
* 필드 유형을 확인하고 필요한 경우 필드 유형을 변경합니다.
* 식별된 표 확인, 열 크기 조정 및 셀 내용 수정
* 잘못 식별된 필드 제거

필요한 변경 작업을 수행한 후 PDF forms을 전환 서비스로 다시 전송합니다. 성공적으로 변환하면 적응형 양식 및 스키마를 비롯한 업데이트된 에셋이 AEM Forms 인스턴스로 다운로드됩니다. 원하는 경험이 달성될 때까지 프로세스를 반복할 수 있습니다.![](assets/stages-of-form-2.gif)

검토 및 올바른 편집기를 사용하려면 Google Chrome, Mozilla FireFox 또는 Microsoft Edge 브라우저가 필요합니다. 편집기는 Internet Explorer를 지원하지 않습니다.

## {#welcome-to-review-and-correct-editor} 검토 및 올바른 편집기에 오신 것을 환영합니다.

검토 및 수정 편집기는 사용하기 쉬운 인터페이스를 제공합니다. 여기에는 다음 구성 요소가 있습니다.

* 컨텐츠 브라우저:컨텐츠 브라우저를 사용하여 요소의 위치를 변경할 수 있습니다. 컨텐츠 브라우저를 사용하면 양식 객체를 드래그 앤 드롭하여 위치를 변경할 수 있습니다. 예를 들어 텍스트 상자 앞에 표를 이동하는 경우 출력 적응형 양식의 탭 순서를 그에 따라 변경합니다.
* 속성 브라우저:선택한 필드의 속성이 표시됩니다. 속성을 수정할 수도 있습니다.
* 도구 모음:도구 모음은 편집기의 상단에 있습니다. 여기에는 필드를 추가, 수정, 그룹화, 그룹 해제 및 삭제하는 도구가 표시됩니다.
* 속성 열기:속성 열기 옵션이 ![](assets/properties.png) 아이콘을 누를 때 나타납니다. 속성 열기를 클릭하여 양식 속성을 열고 추가 옵션을 볼 수 있습니다.
* 필터 단추:필터 단추 ![](assets/toggle_eye.png)는 편집기의 맨 위에 있습니다. 텍스트, 필드, 선택 그룹, 패널 또는 모든 구성 요소만 표시하도록 필드를 필터링할 수 있습니다.
* 저장 단추:**[!UICONTROL Save]** 단추는 편집기의 오른쪽 위 모서리에 있습니다. [저장] 단추 옆의 화살표를 사용하여 변환할 양식을 보내는 옵션을 볼 수도 있습니다.

* PDF 양식:편집기에 소스 PDF 문서가 표시되고 식별된 필드가 포함된 오버레이가 표시됩니다. 도구 모음의 도구를 사용하여 필드를 수정할 수 있습니다.
* 페이지:소스 양식에는 여러 페이지가 있을 수 있습니다. 편집기에서는 오른쪽 위 모서리에 있는 단추를 사용하여 페이지 간을 탐색할 수 있습니다.

![UI 검토 및 수정](assets/reviewcorrectui.png)

**A.** 컨텐트 브라우저  **B.** 속성 브라우저  **C.** Toolbar  **C.** ToolbarD. ****   ****   **** PropertiesButtonE.F.F.ButtonSaveButton필드를 사용하여 오버레이된 PDF 양식

첫 번째 성공적인 변환 후 변환 서비스는 식별된 필드와 구성 요소가 포함된 소스 PDF 문서를 오버레이합니다. 이러한 필드 또는 구성 요소 유형은 다음과 같습니다.텍스트, 필드, 패널, 선택 그룹 및 표:

* 텍스트:소스 PDF 문서의 일반 텍스트입니다. 예를 들어, 위에 표시된 이미지의 대출 신청 텍스트가 여기에 표시됩니다.
* 필드:값 또는 입력 상자에 연결된 텍스트 또는 아이콘 레이블의 조합입니다. 예를 들어, 이미지 위의 [이름] 필드 이름입니다. 텍스트 레이블과 입력 상자가 있습니다. 필드는 텍스트, 숫자, 드롭다운, 날짜, 이메일, 전화 번호, 서명, 통화 및 암호 데이터 유형을 지원합니다.
* 패널:컨텐츠 및 구성 요소의 논리적 수집. 예를 들어, 위의 이미지에 있는 개인 1 및 개인 2 패널의 개인 세부 사항.
* 선택 그룹:객관식 옵션과 관련된 텍스트 조합:확인란 및 라디오 단추를 클릭합니다. 예를 들어 위의 이미지에서 결혼 상태 및 기존 고객을 들 수 있습니다.\
   선택 그룹 캡션 및 객관식 옵션에 따라 변환 서비스는 선택 그룹을 단일 선택 라디오 단추 또는 다중 선택 확인란으로 자동으로 변환합니다. 예를 들어 **선택 그룹 캡션이나 객관식 옵션을 사용하여 하나의 옵션인** Yes **또는** No **만 선택할 수 있는 경우 변환 서비스는 자동으로 선택 그룹을 단일 선택 라디오 단추로 변환합니다.** 마찬가지로 **선택 그룹 캡션 또는 객관식 옵션을 사용하여 선택 그룹 캡션으로서** 또는 **복수**&#x200B;를 적용하는 항목을 모두 선택하면 전환 서비스는 선택 그룹을 다중 선택 확인란으로 자동 변환합니다.

* 표:열과 행으로 표현되는 정보가 포함된 2d 표. 표에 행이나 열을 추가하거나 제거할 수 있습니다.

## 전환 {#start-reviewing-a-conversion} 검토 시작

첫 번째 성공적인 변환 후 변환 서비스는 식별된 필드와 구성 요소가 포함된 소스 PDF 문서를 오버레이합니다. 식별된 필드를 개선하거나 적응형 양식을 다시 생성하여 원하는 경험에 가까운 출력을 얻을 수 있습니다. 첫 번째 전환 성공 후에만 전환 검토를 시작할 수 있습니다.

### {#before-you-start}을(를) 시작하기 전에

* 검토 및 수정 편집기는 조각을 지원하지 않습니다. 변환 중에 **조각 추출** 옵션이 활성화된 전환을 검토하려면 편집기를 사용하지 마십시오. 이러한 변환에 [적응형 양식 편집기](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)를 사용할 수 있습니다.

* 검토 및 수정 편집기에는 실행 취소 작업이 없습니다. 저장 단추를 사용하면 변경 사항을 영구적으로 저장할 수 있습니다.

### {#start-the-review} 검토 시작

전환 검토를 시작하려면 변환에 사용된 소스 PDF 문서를 선택하고 **전환 검토**&#x200B;를 선택하고 탭합니다. 검토 및 수정 편집기가 새 탭에 열립니다. 전환 검토를 시작할 수 있습니다. 다른 문제를 수정하기 전에 다음 기본 검사를 수행하십시오.

![](assets/usingreviewandcorrecteditor.png)

1. **모든 필드의 유형 확인**:전환 서비스는 필드에 잘못된 유형을 할당할 수 있습니다. 예를 들어 휴대폰 필드에 전화를 입력하는 대신 문자 텍스트가 할당됩니다. 필드를 마우스로 가리키면 필드 유형을 찾을 수 있습니다.

   필드 유형을 변경하려면 필드를 선택하고 속성 브라우저를 열고 **[!UICONTROL Type]** 드롭다운에서 값을 선택한 다음 **[!UICONTROL Save]**&#x200B;을 누릅니다. 유형이 변경되었습니다.

   ![](assets/check-typex75.gif)

1. **추가 패널** 제거:전환 서비스는 추가 패널을 생성할 수 있습니다. 예를 들어 상위 패널에 추가 하위 패널이 포함되어 있고 빈 공간이 패널로 변환되고 확인란이 패널로 변환됩니다. 모든 패널의 경계를 검토하고 추가 패널을 제거합니다. 필터 ![](assets/toggle_eye.png) 단추 또는 내용 브라우저를 사용하여 모든 패널을 볼 수 있습니다.

   패널을 삭제하거나 그룹 해제하여 제거할 수 있습니다. 삭제 옵션을 사용하면 패널의 하위 필드 또는 구성 요소도 삭제됩니다.

   * 패널을 삭제하려면 패널을 선택하고 도구 모음에서 ![](assets/delete-icon.png) 삭제 아이콘을 누릅니다. 확인 대화 상자에서 **[!UICONTROL Confirm]**&#x200B;을(를) 누릅니다. **[!UICONTROL Save]**&#x200B;을 눌러 변경 내용을 저장합니다.

   * 패널의 그룹을 해제하려면 패널을 선택하고 도구 모음에서 그룹 해제 아이콘을 누릅니다. 패널은 그룹화되지 않고 그룹화되지 않은 패널의 하위 필드는 상위 필드에 조정됩니다. **[!UICONTROL Save]**을 눌러 변경 사항을 저장합니다.

1. **텍스트** 논리 그룹 만들기:식별된 텍스트를 완벽하고 정확한지 확인합니다. 또한 텍스트가 올바른 패널이나 그룹에 논리적으로 배치됩니다. 예를 들어 여러 열로 구성된 레이아웃에서는 하나의 논리 그룹 및 다른 그룹에 배치된 텍스트를 나타냅니다.

   * 텍스트의 완벽성과 정확성을 검토하려면 필터 ![](assets/toggle_eye.png) 단추를 사용하여 텍스트만 보고 각 텍스트를 클릭한 다음 유효성을 확인합니다. 맞춤법, 오타 또는 문법 문제가 있는 경우 수정합니다.

   * 양식에 텍스트를 추가하려면 + 단추를 누르고 **[!UICONTROL Text]**&#x200B;을 누릅니다. 상자를 그리고 속성 브라우저를 열고 [내용] 상자에 추가할 텍스트를 입력합니다.

1. **테이블 검토:** 표의 모든 테두리가 식별되는지 확인합니다. 또한 셀의 내용이 올바르게 식별되도록 하십시오.

   * 누락된 테두리를 식별하려면 **[!UICONTROL Add Column]** 또는 **[!UICONTROL Add Row]** 옵션을 사용합니다.

   * 추가 테두리를 제거하려면 **[!UICONTROL Delete Column]** 또는 **[!UICONTROL Delete Row]** 옵션을 사용합니다.

필요한 변경 작업을 수행한 후 **[!UICONTROL Save & Convert]** 단추를 눌러 PDF forms을 전환 서비스로 다시 전송합니다. 각 필드는 해당 적응형 필드 구성 요소로 변환됩니다. 변환 후 적응형 양식 및 스키마를 비롯한 업데이트된 에셋이 AEM Forms 인스턴스로 다운로드됩니다. 양식의 복잡도에 따라 서비스 전환이 완료되는 데 시간이 걸릴 수 있습니다.

![저장 및 변환](assets/save-and-convert.png)

기본 검사를 수행한 후 양식을 검토하여 조직에 관련된 문제를 수정할 수 있습니다. 이러한 문제는 누락된 필드 추가 등과 관련이 있을 수 있습니다. [검토 및 수정 편집기 도구 사용](review-correct-ui-edited.md#use-the-review-and-correct-editor-tools) 섹션을 보고 편집자가 이러한 문제를 해결하기 위해 제공하는 모든 도구에 대해 알 수 있습니다.

또한 거의 모든 양식에서 발생하는 동일한 문제를 인식하고 이러한 패턴을 Adobe에 보고할 수도 있습니다. 원하는 경험이 완성될 때까지 검토 및 수정 편집기를 사용합니다.

## 검토 및 올바른 편집기 도구 사용 {#use-the-review-and-correct-editor-tools}

검토 및 수정 편집기를 사용하여 다음 작업을 수행할 수 있습니다.

* [양식에 구성 요소 추가](review-correct-ui-edited.md#add-a-component-to-the-form)
* [표 추가 또는 편집](review-correct-ui-edited.md)
* [구성 요소 유형 변경](review-correct-ui-edited.md#change-type-a-component)

* [패널 만들기 또는 제거](review-correct-ui-edited.md#create-or-remove-a-panel)
* [패널 또는 구성 요소 삭제](review-correct-ui-edited.md#delete-a-panel-or-component)
* [구성 요소의 속성 설정](review-correct-ui-edited.md#set-properties-of-a-component)
* [변환을 위해 양식 보내기](review-correct-ui-edited.md#send-a-form-for-conversion)

### {#add-a-component-to-the-form} 양식에 구성 요소 추가

변환 서비스에서 인쇄 양식의 일부 구성 요소를 식별하지 못할 수 있습니다. 예를 들어 양식의 **생년월일** 구성 요소는 변환 중에 식별되지 않습니다. **+** 도구를 사용하여 이러한 구성 요소를 식별할 수 있습니다. 이 도구를 사용하여 텍스트, 필드, 선택 그룹, 표 및 패널 구성 요소를 추가할 수 있습니다.

![](assets/add-component.gif)

양식에 구성 요소를 추가하려면 **[!UICONTROL +]**&#x200B;을 누르고 **[!UICONTROL Field]**&#x200B;을 탭합니다. 필드의 레이블과 입력 상자를 포함하는 상자를 그립니다. 예를 들어 위의 예제 이미지는 필드 구성 요소를 사용하여 **생년월일** 레이블 및 그 아래의 값 상자를 양식에 추가합니다. 상자를 그릴 때 전환 서비스는 필드의 유형을 식별합니다. 필요한 경우 속성 브라우저에서 필드 유형을 변경할 수 있습니다. 구성 요소를 만든 후 속성 브라우저를 열고 구성 요소의 속성을 설정합니다.

**[!UICONTROL Save]** 단추를 눌러 수정 내용을 저장하거나 **[!UICONTROL Save & Convert]** 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### {#addedittable} 표 추가 또는 편집

변환은 테이블 셀의 일부 셀, 경계 또는 내용을 식별하지 못하게 할 수 있습니다. 예를 들어 표의 행은 식별되지 않습니다. 검토 및 수정 편집기를 사용하여 해당 항목을 식별할 수 있습니다. 테이블에 대해 다음 작업을 수행할 수 있습니다.

* 표를 선택하려면 표의 셀을 클릭합니다.
* 이름, 제목 또는 유형과 같은 셀의 속성을 수정하려면 셀을 두 번 클릭합니다. 셀을 두 번 클릭하여 컨텐츠를 수정하고 필요한 필드를 표시하고 다른 속성을 선택할 수도 있습니다.
* 완전히 식별되지 않았거나 새 테이블을 양식에 추가/식별하려면 **[!UICONTROL +]** 도구를 사용합니다.
* 표의 셀 또는 행 크기를 조정하려면 표의 빈 영역을 한 번 클릭하고 행 또는 열 경계를 마우스로 가리키면 커서 포인터가 바뀌면 경계를 선택하고 이동합니다. 크기를 변경한 후 **[!UICONTROL Done]**&#x200B;을 클릭하여 변경 내용을 적용합니다. **[!UICONTROL ESC]** 키를 눌러 크기 조정을 취소할 수 있습니다.

* 행 또는 열을 추가하거나 삭제하려면 표 행에서 셀을 선택하고 ![](assets/table_18x18.png) 메뉴에서 **[!UICONTROL Add Row]**, **[!UICONTROL Add Column]**, **[!UICONTROL Delete Row]** 또는 **[!UICONTROL Delete Column]** 옵션을 선택합니다.

* 셀을 표로 분할하려면 ![](assets/table_18x18.png) 메뉴에서 **[!UICONTROL Spilt Vertical]** 또는 **[!UICONTROL Split Horizontal]** 옵션을 선택합니다.

* 표의 셀을 병합하려면 병합할 셀을 선택하고 ![](assets/table_18x18.png) 표 메뉴에서 **[!UICONTROL Merge Cells]** 옵션을 선택합니다.

### 구성 요소 {#change-type-a-component} 유형 변경

전환 서비스는 일부 잘못된 유형의 필드를 만들 수 있습니다. 예를 들어, 다음 이미지에서 **성별** 필드가 **텍스트** 필드로 잘못 식별됩니다. 또한 레이블의 내용이 잘못되었습니다. 필드는 선택 필드 유형이어야 하며 레이블은 성별이어야 합니다. 구성 요소의 유형을 변경하고 레이블을 수정하려면:

변환할 필드를 선택하고 ![](assets/smock_shuffle_18_n.svg)을 누른 다음 필드 유형을 누릅니다. 필드가 선택한 필드 유형으로 변환됩니다. 필드는 다음 표에 나열된 유형으로만 변환할 수 있습니다. 패널 구성 요소는 변형되지 않고 그룹화만 해제할 수 있습니다.

| **구성 요소** | **변환 대상** |
|---|---|
| 텍스트 | 필드 또는 선택 그룹 |
| 필드 | 텍스트 또는 선택 그룹 |
| 선택 그룹 | 텍스트 또는 패널 |

변환된 후에는 속성 브라우저를 열고 레이블을 지정하고 기타 필요한 속성을 지정합니다. **[!UICONTROL Save]** 단추를 눌러 수정 내용을 저장하거나 저장 및 변환 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### 패널 {#create-or-remove-a-panel} 만들기 또는 제거

변환 서비스는 관련 구성 요소 및 인쇄 양식의 내용을 패널로 취합합니다. 예를 들어, 양식에 이름, 플롯 번호, 영역, 구, 시, 주, 우편 번호, 국가 등의 필드가 있는 주소 패널이 있을 수 있습니다. 이러한 필드는 하나의 패널로 그룹화됩니다. 양식에 여러 패널이 있을 수 있습니다.

변환 서비스는 구성 요소가 다른 구성 요소와 관계가 없거나 상대 구성 요소가 패널의 바깥쪽에 남게 하는 패널을 만들 수 있습니다. 그룹 또는 그룹 해제 도구를 사용하여 이러한 패널을 수정할 수 있습니다.

* 패널을 제거하려면 패널을 선택하고 그룹 해제 ![그룹 해제](assets/ungroupX18.png)를 누릅니다. 패널이 제거되고 패널의 하위 구성 요소가 상위 구성 요소로 이동됩니다. [구성 요소 삭제](review-correct-ui-edited.md#delete-a-panel-or-component) 옵션을 사용하여 패널 및 해당 하위 항목을 삭제할 수도 있습니다.

* 패널을 만들려면 Ctrl 키(Windows 또는 Linux의 경우) 또는 Control 키(Mac의 경우)를 사용하여 관련 구성 요소를 선택하고 ![group](assets/group.jpg)을 눌러 패널을 만듭니다. 속성 브라우저를 열고 패널의 속성을 지정합니다.

**[!UICONTROL Save]** 단추를 눌러 수정 내용을 저장하거나 **[!UICONTROL Save & Convert]** 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### 패널 또는 구성 요소 {#delete-a-panel-or-component} 삭제

전환 서비스는 일부 잘못된 패널이나 구성 요소를 식별할 수 있습니다. 이러한 패널의 구성 요소 대부분은 관련이 없습니다. 이러한 패널이나 구성 요소를 삭제할 수 있습니다.

패널이나 구성 요소를 삭제하려면 패널이나 구성 요소를 선택하고 ![](assets/delete-icon.png) 삭제 아이콘을 누릅니다. 확인 대화 상자에서 **[!UICONTROL Confirm]**&#x200B;을(를) 탭합니다. 선택한 패널 또는 구성 요소가 삭제됩니다. 패널을 삭제하면 패널의 모든 하위 패널도 삭제됩니다. Ctrl 키(Windows 또는 Linux의 경우) 또는 Control 키(Mac의 경우)를 사용하여 여러 구성 요소 또는 패널을 선택할 수 있습니다.

### 구성 요소 {#set-properties-of-a-component}의 속성 설정

양식의 모든 구성 요소에는 이름, 제목, 유형 등의 속성 세트가 있습니다. 구성 요소의 속성을 설정하려면 구성 요소를 선택하고 속성 브라우저를 누릅니다. 선택한 구성 요소의 속성이 표시됩니다. 속성을 변경하거나 설정합니다.

**[!UICONTROL Save]** 단추를 눌러 수정 내용을 저장하거나 **[!UICONTROL Save & Convert]** 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### 전환 양식 보내기 {#send-a-form-for-conversion}

검토 및 수정 편집기에서 필요한 모든 변경 사항을 만들었다면 변환할 양식을 다시 보낼 수 있습니다. 변환할 양식을 보내려면 **[!UICONTROL Save & Convert]**&#x200B;을(를) 누릅니다. **[!UICONTROL Sent for conversion label]**&#x200B;은 소스 문서가 포함된 폴더에 적용되며 업데이트된 소스 양식이 Adobe I/O에서 실행 중인 전환 서비스로 업로드됩니다.

양식의 복잡도에 따라 변환 서비스에서 양식을 변환하는 데 시간이 걸릴 수 있습니다. 변환이 완료되면 변환된 적응형 양식과 관련 에셋이 컴퓨터에 다운로드됩니다. 변환이 완료된 후 편집기에서 양식을 검토하고 필요한 경우 최종 수정 사항은 [적응형 양식 편집기](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)에서 열 수 있습니다.

적응형 양식 편집기에서 양식을 업데이트한 후 변환할 양식을 다시 전송하면 적응형 양식의 모든 변경 사항이 손실됩니다. 변환 성공 후에만 검토 및 올바른 편집기에서 양식을 열 수 있습니다.

<!--
Comment Type: draft

<h3>Open adaptive forms editor</h3>
-->

<!--
Comment Type: draft

<p>There can be instances where you require adaptive forms editor to make the changes like, applying a different theme to the form or fixing tables. Once you have made all the required changes in Review and Correct editor and converted the form, you can open your form in adaptive forms editor to make the final set of changes.</p>
<p>To open the form with adaptive forms editor, tap the <img src="assets/properties.png" /> icon, and tap <strong>Open Adaptive Form Editor</strong>. The form opens in adaptive form editor. </p>


## Previous {#previous}

[Use Automated Forms Conversion service](convert-existing-forms-to-adaptive-forms.md)
-->
