---
title: 전환된 양식 검토 및 수정
seo-title: 전환된 양식 검토 및 수정
description: 자동화된 Forms 전환 서비스에서 변환된 적응형 양식을 검토하고 수정합니다.
seo-description: 자동화된 Forms 전환 서비스에서 변환된 적응형 양식 검토 및 수정
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

AEM Forms 자동 Forms 변환 서비스는 입력 PDF 문서의 필드, 컨텐츠 및 레이아웃을 식별하고 PDF 문서를 적응형 양식으로 변환합니다. 출력 적응형 양식에는 필드가 누락되거나 잘못 변환될 수 있습니다. 검토 및 수정 편집기를 사용하여 식별된 필드를 향상시키고 적응형 양식을 재생성하여 원하는 경험에 보다 가깝게 출력할 수 있습니다. 첫 번째 변환 후 편집기에서 입력 PDF 문서를 열어 다음을 수행할 수 있습니다.

* 전환 중에 식별된 모든 필드 및 컨텐츠 보기
* 전환 중 누락된 필드 및 컨텐츠 식별
* 필드 유형을 확인하고 필요한 경우 필드 유형을 변경합니다.
* 식별된 표 확인, 열 크기 조정, 셀 내용 수정
* 잘못 식별된 필드 제거

필요한 변경 작업을 수행한 후 PDF forms을 전환 서비스로 다시 보냅니다. 성공적으로 변환하면 적응형 양식 및 스키마를 비롯한 업데이트된 에셋이 AEM Forms 인스턴스로 다운로드됩니다. 원하는 경험이 이루어질 때까지 프로세스를 반복할 수 있습니다. ![](assets/stages-of-form-2.gif)

검토 및 올바른 편집기를 사용하려면 Google Chrome, Mozilla FireFox 또는 Microsoft Edge 브라우저가 필요합니다. 편집기는 Internet Explorer를 지원하지 않습니다.

## 검토 및 수정 편집기 시작 {#welcome-to-review-and-correct-editor}

검토 및 수정 편집기는 사용하기 쉬운 인터페이스를 제공합니다. 다음과 같은 구성 요소가 있습니다.

* 컨텐츠 브라우저:컨텐츠 브라우저를 사용하여 요소의 위치를 변경할 수 있습니다. 컨텐츠 브라우저를 사용하면 양식 개체를 드래그하여 놓고 위치를 변경할 수 있습니다. 예를 들어 텍스트 상자 앞에서 표를 이동하는 경우 출력 적응형 양식의 탭 순서를 그에 따라 변경합니다.
* 속성 브라우저:선택한 필드의 속성이 표시됩니다. 속성을 수정할 수도 있습니다.
* 도구 모음:도구 모음은 편집기의 상단에 있습니다. 여기에는 필드를 추가, 수정, 그룹, 그룹 해제 및 삭제하는 도구가 표시됩니다.
* 속성 열기:속성 열기 옵션이 ![](assets/properties.png) 아이콘을 탭하면 나타납니다. 속성 열기를 클릭하여 양식 속성을 열고 추가 옵션을 볼 수 있습니다.
* 필터 단추:필터 단추 ![](assets/toggle_eye.png) 는 편집기의 상단에 있습니다. 텍스트, 필드, 선택 그룹, 패널 또는 모든 구성 요소만 표시하도록 필드를 필터링할 수 있습니다.
* 저장 단추:이 **[!UICONTROL Save]** 단추는 편집기의 오른쪽 위 모서리에 있습니다. [저장] 단추 옆의 화살표를 사용하여 변환을 위해 양식을 보내는 옵션을 볼 수도 있습니다.

* PDF 양식:편집기에 소스 PDF 문서가 표시되고 식별된 필드와 함께 오버레이됩니다. 도구 모음의 도구를 사용하여 필드를 수정할 수 있습니다.
* 페이지:소스 양식에는 여러 페이지가 있을 수 있습니다. 편집기는 오른쪽 위 모서리에 페이지 사이를 탐색하는 단추를 제공합니다.

![UI 검토 및 수정](assets/reviewcorrectui.png)

**A.** Content Browser **** B. **Properties Browser** C. **Toolbar.D.** **** **** **** Button Properties Button E.Filter Button F.Save G.Overlayed PDF verified fields

변환 서비스가 첫 번째 성공 후 식별된 필드와 구성 요소가 포함된 소스 PDF 문서를 오버레이합니다. 이러한 필드 또는 구성 요소 유형은 다음과 같습니다.텍스트, 필드, 패널, 선택 그룹 및 표:

* 텍스트:소스 PDF 문서의 일반 텍스트 예를 들어, 위에 표시된 이미지의 대출 신청 텍스트.
* 필드:값 또는 입력 상자와 연결된 텍스트 또는 아이콘 레이블의 조합입니다. 예를 들어 이미지 위의 [이름] 필드 이름이 있습니다. 텍스트 레이블과 입력 상자가 있습니다. 필드는 텍스트, 숫자, 드롭다운, 날짜, 이메일, 전화 번호, 서명, 통화 및 암호 데이터 유형을 지원합니다.
* 패널:컨텐츠 및 구성 요소의 논리적 수집 예를 들어, 위의 이미지에서 개인 1 및 개인 2 패널의 개인 세부 사항.
* 선택 그룹:객관식 옵션과 관련된 텍스트 조합:확인란 및 라디오 단추. 예를 들어 위의 이미지에서 혼인 상태 및 기존 고객.\
   선택 그룹 캡션 및 해당 객관식 옵션에 따라 전환 서비스는 선택 그룹을 단일 선택 라디오 단추 또는 다중 선택 확인란으로 자동 변환합니다. 예를 들어 선택 그룹 **캡션 또는 객관식 옵션을** 선택하여 하나의 옵션인 **예** 또 **는 아니요**&#x200B;중 하나만 선택할 수 있는 경우 전환 서비스는 선택 그룹을 자동으로 단일 선택 라디오 단추로 변환합니다. 마찬가지로, 적용되는 **항목 모두** 선택 **또는 선택 그룹 캡션이나** 객관식 옵션을 사용하여 여러옵션을 선택할 수 있는 경우 전환 서비스는 자동으로 선택 그룹을 다중 선택 확인란으로 변환합니다.

* 표:열과 행으로 표현되는 정보가 포함된 2d 표. 표에 행이나 열을 추가하거나 제거할 수 있습니다.

## 전환 검토 시작 {#start-reviewing-a-conversion}

변환 서비스가 첫 번째 성공 후 식별된 필드와 구성 요소가 포함된 소스 PDF 문서를 오버레이합니다. 식별된 필드를 개선하고 적응형 양식을 재생성하여 원하는 경험에 보다 가깝게 출력할 수 있습니다. 첫 번째 전환 성공 후에만 전환 검토를 시작할 수 있습니다.

### Before you start {#before-you-start}

* 검토 및 수정 편집기는 조각을 지원하지 않습니다. 변환 중에 [조각 **추출] 옵션을 활성화한 전환을 검토하는 데 편집기를** 사용하지 마십시오. 이러한 변환에 [적응형 양식 편집기를](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) 사용할 수 있습니다.

* 검토 및 수정 편집기에는 실행 취소 작업이 없습니다. 저장 단추를 사용하면 변경 사항을 영구적으로 저장할 수 있습니다.

### 검토 시작 {#start-the-review}

전환 검토를 시작하려면 변환에 사용된 소스 PDF 문서를 선택하고 전환 **검토를 선택합니다**. 검토 및 수정 편집기가 새 탭에서 열립니다. 전환 검토를 시작할 수 있습니다. 다른 문제를 수정하기 전에 다음 기본 검사를 수행하십시오.

![](assets/usingreviewandcorrecteditor.png)

1. **모든 필드의 유형 확인**:전환 서비스는 필드에 잘못된 유형을 할당할 수 있습니다. 예를 들어 휴대폰 필드에 전화를 입력하는 대신 문자 텍스트가 할당됩니다. 필드를 마우스로 가리키면 필드 유형을 찾을 수 있습니다.

   필드 유형을 변경하려면 필드를 선택하고 속성 브라우저를 열고 **[!UICONTROL Type]** 드롭다운에서 값을 선택한 다음 을 누릅니다 **[!UICONTROL Save]**. 유형이 변경되었습니다.

   ![](assets/check-typex75.gif)

1. **추가 패널**&#x200B;제거:전환 서비스는 추가 패널을 생성할 수 있습니다. 예를 들어 상위 패널에 추가 하위 패널이 포함되어 있고 빈 공간이 패널로 변환되고 확인란이 패널로 변환됩니다. 모든 패널의 경계를 검토하고 추가 패널을 제거합니다. 필터 ![](assets/toggle_eye.png) 단추 또는 컨텐츠 브라우저를 사용하여 모든 패널을 볼 수 있습니다.

   패널을 삭제하거나 그룹 해제할 수 있습니다. 삭제 옵션을 사용하면 패널의 하위 필드 또는 구성 요소도 삭제됩니다.

   * 패널을 삭제하려면 패널을 선택하고 도구 모음에서 삭제 ![](assets/delete-icon.png) 아이콘을 누릅니다. 확인 대화 상자에서 을 누릅니다 **[!UICONTROL Confirm]**. 을 눌러 변경 사항 **[!UICONTROL Save]** 을 저장합니다.

   * 패널의 그룹을 해제하려면 패널을 선택하고 도구 모음에서 그룹 해제 아이콘을 누릅니다. 패널은 그룹화되지 않고 그룹화되지 않은 패널의 하위 필드는 상위 필드에 조정됩니다. **[!UICONTROL Save]**를 눌러 변경 사항을 저장합니다.

1. **논리 텍스트 그룹을 만듭니다**.확인된 텍스트를 완벽과 정확성에 대해 검증합니다. 또한 텍스트가 올바른 패널이나 그룹에 논리적으로 배치됩니다. 예를 들어, 여러 열 레이아웃에서는 한 논리 그룹 중 하나의 텍스트를 다른 그룹에 배치합니다.

   * 텍스트의 완벽성과 정확성을 검토하려면 필터 ![](assets/toggle_eye.png) 단추를 사용하여 텍스트만 보고 각 텍스트를 클릭하고 유효성을 확인합니다. 맞춤법, 오타 또는 문법 문제가 있는 경우 이를 수정합니다.

   * 양식에 텍스트를 추가하려면 + 단추를 누르고 누릅니다 **[!UICONTROL Text]**. 상자를 그리고 속성 브라우저를 열고 텍스트를 입력하여 컨텐트 상자에 추가합니다.

1. **테이블 검토:** 표의 모든 테두리가 식별되는지 확인합니다. 또한 셀의 컨텐츠가 올바르게 식별되는지 확인합니다.

   * 누락된 테두리를 식별하려면 **[!UICONTROL Add Column]** 또는 **[!UICONTROL Add Row]** 옵션을 사용합니다.

   * 추가 테두리를 제거하려면 **[!UICONTROL Delete Column]** 또는 **[!UICONTROL Delete Row]** 옵션을 사용합니다.

필요한 변경 작업을 수행한 후 **[!UICONTROL Save & Convert]** 단추를 눌러 PDF forms을 전환 서비스로 재전송합니다. 각 필드는 해당 응용 필드 구성 요소로 변환됩니다. 변환 후 적응형 양식 및 스키마를 비롯한 업데이트된 에셋이 AEM Forms 인스턴스로 다운로드됩니다. 양식의 복잡도에 따라 서비스 전환이 완료되는 데 시간이 걸릴 수 있습니다.

![저장 및 변환](assets/save-and-convert.png)

기본 확인을 수행한 후 양식을 검토하여 조직에 관련된 문제를 수정할 수 있습니다. 이러한 문제는 누락된 필드 추가 등과 관련이 있을 수 있습니다. [검토 및 [수정 편집기 도구](review-correct-ui-edited.md#use-the-review-and-correct-editor-tools) 사용] 섹션을 통해 편집자가 이러한 문제를 해결하기 위해 제공하는 모든 도구에 대해 알아볼 수 있습니다.

또한 거의 모든 양식에서 발생하는 동일한 문제를 인식하고 이러한 패턴을 Adobe에 보고할 수도 있습니다. 원하는 경험을 얻을 때까지 검토 및 수정 편집기를 사용합니다.

## 검토 및 수정 편집기 도구 사용 {#use-the-review-and-correct-editor-tools}

검토 및 수정 편집기를 사용하여 다음을 수행할 수 있습니다.

* [양식에 구성 요소 추가](review-correct-ui-edited.md#add-a-component-to-the-form)
* [표 추가 또는 편집](review-correct-ui-edited.md)
* [구성 요소 유형 변경](review-correct-ui-edited.md#change-type-a-component)

* [패널 만들기 또는 제거](review-correct-ui-edited.md#create-or-remove-a-panel)
* [패널 또는 구성 요소 삭제](review-correct-ui-edited.md#delete-a-panel-or-component)
* [구성 요소의 속성 설정](review-correct-ui-edited.md#set-properties-of-a-component)
* [변환을 위해 양식 보내기](review-correct-ui-edited.md#send-a-form-for-conversion)

### 양식에 구성 요소 추가 {#add-a-component-to-the-form}

변환 서비스에서 인쇄 양식의 일부 구성 요소를 찾지 못할 수 있습니다. 예를 들어 양식의 **생년월일** 구성 요소에서는 전환 중에 식별되지 않습니다. You can use the **+** tool to help identify such components. 이 툴을 사용하면 텍스트, 필드, 선택 그룹, 표 및 패널 구성 요소를 추가할 수 있습니다.

![](assets/add-component.gif)

양식에 구성 요소를 추가하려면 탭 **[!UICONTROL +]** 을 누른 후 탭합니다 **[!UICONTROL Field]**. 필드의 레이블과 입력 상자를 포함하는 상자를 그립니다. 예를 들어 위의 예제 이미지는 필드 구성 요소를 사용하여 **생년월일** 레이블 및 그 아래에 있는 값 상자를 양식에 추가합니다. 상자를 그릴 때 전환 서비스는 필드의 유형을 식별합니다. 필요한 경우 속성 브라우저에서 필드 유형을 변경할 수 있습니다. 구성 요소를 만든 후 속성 브라우저를 열고 구성 요소의 속성을 설정합니다.

단추를 **[!UICONTROL Save]** **[!UICONTROL Save & Convert]** 눌러 수정 내용을 저장하거나 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### 표 추가 또는 편집 {#addedittable}

변환은 테이블 셀의 일부 셀, 경계 또는 내용을 식별하지 못하게 할 수 있습니다. 예를 들어 표의 행은 식별되지 않습니다. 검토 및 수정 편집기를 사용하여 이러한 항목을 식별할 수 있습니다. 테이블에 대해 다음 작업을 수행할 수 있습니다.

* 테이블을 선택하려면 표의 셀을 클릭합니다.
* 이름, 제목 또는 문자와 같은 셀의 속성을 수정하려면 셀을 두 번 클릭합니다. 셀을 두 번 클릭하여 컨텐츠를 수정하고 필요한 필드를 표시하고 다른 속성을 선택할 수도 있습니다.
* 양식에 완전히 식별되지 않았거나 새 테이블을 추가/식별하려면 **[!UICONTROL +]** 도구를 사용합니다.
* 표의 셀 또는 행 크기를 조정하려면 표의 빈 영역을 한 번 클릭하고 행 또는 열 경계를 마우스로 가리키면 커서 포인터가 변경되면 경계를 선택하고 이동합니다. 크기 조정 후 을 클릭하여 변경 사항 **[!UICONTROL Done]** 을 적용합니다. 키를 눌러 크기 조정 내용을 취소할 수 있습니다. **[!UICONTROL ESC]**

* 행이나 열을 추가하거나 삭제하려면 표 행에서 셀을 선택하고 **[!UICONTROL Add Row]**&#x200B;메뉴에서 **[!UICONTROL Add Column]**, **[!UICONTROL Delete Row]**, **[!UICONTROL Delete Column]** 또는 ![](assets/table_18x18.png) 옵션을선택합니다.

* 셀을 표로 분할하려면 **[!UICONTROL Spilt Vertical]** 메뉴에서 **[!UICONTROL Split Horizontal]** 또는 ![](assets/table_18x18.png) 옵션을 선택합니다.

* 표의 셀을 병합하려면 병합할 셀을 선택하고 표 메뉴에서 **[!UICONTROL Merge Cells]** 옵션을 ![](assets/table_18x18.png) 선택합니다.

### 구성 요소 유형 변경 {#change-type-a-component}

전환 서비스는 일부 잘못된 유형의 필드를 만들 수 있습니다. 예를 들어 다음 이미지에서 **성별** 필드가 **텍스트** 필드로 잘못 식별됩니다. 또한 레이블의 내용이 잘못되었습니다. 필드는 선택 필드 유형이어야 하며 레이블은 성별이어야 합니다. 구성 요소의 유형을 변경하고 해당 레이블을 수정하려면:

변환할 필드를 선택하고 필드 유형 ![](assets/smock_shuffle_18_n.svg) 을 누른 후 누릅니다. 필드가 선택한 필드 유형으로 변환됩니다. 필드는 다음 표에 나열된 유형으로만 변환할 수 있습니다. 패널 구성 요소는 그룹화만 해제할 수 있고 변형되지 않습니다.

| **구성 요소** | **전환 대상** |
|---|---|
| 텍스트 | 필드 또는 선택 그룹 |
| 필드 | 텍스트 또는 선택 그룹 |
| 선택 그룹 | 텍스트 또는 패널 |

변환된 후 속성 브라우저를 열고 레이블을 지정하고 필요한 기타 속성을 지정합니다. 단추를 눌러 수정 내용을 저장하거나 저장 및 변환 단추를 사용하여 PDF forms을 전환 서비스로 재전송합니다. **[!UICONTROL Save]**

### 패널 만들기 또는 제거 {#create-or-remove-a-panel}

변환 서비스는 관련 구성 요소 및 인쇄 양식의 내용을 패널로 취합합니다. 예를 들어 양식에 이름, 플롯 번호, 영역, 구, 시, 주, 우편 번호, 국가 등의 필드가 있는 주소 패널이 있을 수 있습니다. 이러한 필드는 하나의 패널로 그룹화됩니다. 양식에 여러 패널이 있을 수 있습니다.

전환 서비스는 구성 요소가 다른 구성 요소와 관련이 없는 패널을 만들거나 상대 구성 요소를 패널 밖으로 내보낼 수 있습니다. 그룹 또는 그룹 해제 도구를 사용하여 이러한 패널을 수정할 수 있습니다.

* 패널을 제거하려면 패널을 선택하고 그룹 해제 ![를 누릅니다](assets/ungroupX18.png). 패널이 제거되고 패널의 하위 구성 요소가 상위 구성 요소로 이동됩니다. 구성 요소 [삭제](review-correct-ui-edited.md#delete-a-panel-or-component) 옵션을 사용하여 패널과 해당 하위 패널을 삭제할 수도 있습니다.

* 패널을 만들려면 Ctrl 키(Windows 또는 Linux의 경우) 또는 Control 키(Mac의 경우)를 사용하여 관련 구성 요소를 선택하고 ![그룹을 눌러](assets/group.jpg) 패널을 만듭니다. 속성 브라우저를 열고 패널의 속성을 지정합니다.

단추를 **[!UICONTROL Save]** **[!UICONTROL Save & Convert]** 눌러 수정 내용을 저장하거나 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### 패널 또는 구성 요소 삭제 {#delete-a-panel-or-component}

전환 서비스는 일부 잘못된 패널이나 구성 요소를 식별할 수 있습니다. 이러한 패널의 대부분의 구성 요소는 관련이 없습니다. 이러한 패널이나 구성 요소를 삭제할 수 있습니다.

패널이나 구성 요소를 삭제하려면 패널 또는 구성 요소를 선택하고 삭제 ![](assets/delete-icon.png) 아이콘을 누릅니다. 확인 대화 상자에서 을 누릅니다 **[!UICONTROL Confirm]**. 선택한 패널 또는 구성 요소가 삭제됩니다. 패널을 삭제하면 패널의 모든 하위 구성 요소도 삭제됩니다. Ctrl 키(Windows 또는 Linux의 경우) 또는 Control 키(Mac의 경우)를 사용하여 여러 구성 요소나 패널을 선택할 수 있습니다.

### 구성 요소의 속성 설정 {#set-properties-of-a-component}

양식의 모든 구성 요소에는 이름, 제목, 유형 등의 속성 세트가 있습니다. 구성 요소의 속성을 설정하려면 구성 요소를 선택하고 속성 브라우저를 누릅니다. 선택한 구성 요소의 속성이 표시됩니다. 속성을 변경하거나 설정합니다.

단추를 **[!UICONTROL Save]** **[!UICONTROL Save & Convert]** 눌러 수정 내용을 저장하거나 단추를 사용하여 PDF forms을 전환 서비스로 다시 전송합니다.

### 변환을 위해 양식 보내기 {#send-a-form-for-conversion}

검토 및 수정 편집기에서 필요한 모든 변경 사항을 만들었으면 양식을 다시 변환하여 사용할 수 있습니다. 변환을 위해 양식을 전송하려면 을 누릅니다 **[!UICONTROL Save & Convert]**. 소스 문서 **[!UICONTROL Sent for conversion label]** 가 포함된 폴더에 적용되고 업데이트된 소스 양식이 Adobe I/O에서 실행되는 전환 서비스로 업로드됩니다.

양식의 복잡도에 따라 변환 서비스에서 양식을 변환하는 데 시간이 걸릴 수 있습니다. 변환이 완료되면 변환된 응용 양식과 관련 에셋이 컴퓨터에 다운로드됩니다. 변환이 완료된 후 편집기에서 양식을 검토하고 필요한 경우 [적응형 양식 편집기에서](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) 적응형 양식을 열어 최종 수정 사항을 확인할 수 있습니다.

적응형 양식 편집기에서 양식을 업데이트한 후 변환을 위해 양식을 다시 보내는 경우 적응형 양식의 모든 변경 사항이 손실됩니다. 전환 성공 후에만 리뷰로 양식을 열고 편집기를 수정할 수 있습니다.

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
