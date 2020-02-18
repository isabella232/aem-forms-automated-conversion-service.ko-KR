---
title: 소개
description: '인쇄 양식을 적응형 양식으로 신속하게 변환 '
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# 소개 {#introduction-to-automated-forms-conversion-service}

자동화된 양식 변환 서비스를 사용하면 PDF 양식을 적응형 양식으로 자동 변환하여 데이터 캡처 경험을 디지털화하고 현대화할 수 있습니다. Adobe Sensei 기반의 이 서비스는 PDF 양식을 장치 친화적인 반응형 및 HTML5 기반의 적응형 양식으로 자동 변환합니다. PDF Forms 및 XFA에 대한 기존 투자를 활용하는 동시에 전환 중에 적절한 유효성 검사, 스타일 지정 및 레이아웃을 적응형 양식 필드에 적용합니다. 이 서비스는 다음과 같은 도움을 줍니다.

* 인쇄 양식을 적응형 양식으로 변환하는 데 필요한 수작업 절감
* 변환 중 패턴 및 적절한 유효성 검사 적용
* 변환 중 기록 문서 생성
* 일반적으로 발생하는 필드를 재사용 가능한 양식 조각으로 그룹화
* 변환 중 Adobe Analytics 사용

![간단합니다. 우리는 단지 우리에게 소스 양식을 제공하고 모든 것을 우리에게 맡기기만 하면 됩니다. 최적의 양식을 제공합니다. 물론, 당신은 당신의 만족감에 대한 결과물을 계속 기록할 것이다. ](assets/pdf-to-adaptive-form-gitx50.gif)

## 온보딩 {#onboarding}

이 서비스는 AEM 6.5 Forms 온프레미스 고객 및 Adobe Managed Service 엔터프라이즈 고객에게 무료로 제공됩니다. Adobe 세일즈 팀 또는 Adobe 담당자에게 문의하여 서비스에 대한 액세스 권한을 요청할 수 있습니다.

Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 관리자로 지정된 사람에게 필요한 권한을 제공합니다. 관리자는 해당 서비스에 연결할 조직의 AEM Forms 개발자(사용자)에게 액세스 권한을 부여할 수 있습니다. 자세한 [내용은 자동화된 양식 변환 서비스](configure-service.md) 구성을 참조하십시오.

## 지원되는 PDF 양식 및 언어 {#supported-languages-and-pdf-forms}

이 서비스는 비대화형 PDF 양식, AcroForms로 만든 양식, AEM Forms 또는 Adobe LiveCycle을 사용하여 만든 XFA 기반 양식을 지원합니다.

이 서비스는 영어 양식만 응용 양식으로 변환할 수 있습니다. AEM 번역 워크플로우를 [사용하여 생성된 적응형 양식을 다른 언어로 번역할 수](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)있습니다.

## 전환 워크플로우 {#conversion-workflow}

자동화된 양식 전환 서비스는 Adobe Cloud에서 실행됩니다. AEM 인스턴스를 서비스에 연결하고, 양식을 AEM 인스턴스에 업로드하고, 변환을 시작합니다. 전체 전환 프로세스는 다음과 같습니다.

![워크플로우](assets/conversion-workflow.png)

### 1.환경 설정 {#set-up-the-environment}

자동화된 양식 전환 서비스는 Adobe Cloud에서 실행됩니다. [조직의 Adobe I/O 계정을 구성하고 로컬 AEM 인스턴스를](configure-service.md) Adobe Cloud에서 실행되는 전환 서비스에 연결합니다.

### 2.PDF 양식을 적응형 양식으로 변환 {#use-the-conversion-service}

AEM Forms 환경이 구성된 후 PDF 양식을 적응형 양식으로 변환하려면 PDF 양식을 [AEM 인스턴스로](convert-existing-forms-to-adaptive-forms.md) 업로드하고 변환을 [](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)시작합니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 보안 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 암호화된 양식을 변환하지 않습니다.
* 스캔한 양식, 컬러, 영어 이외의 언어 및 채워진 양식을 업로드하지 마십시오. 이러한 양식은 지원되지 않습니다.
* 파일 이름에 공백이 있는 PDF 양식을 업로드하지 마십시오.
* PDF 포트폴리오를 업로드하지 [마십시오](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html). 서비스는 PDF 포트폴리오를 적응형 양식으로 변환하지 않습니다.
* 모범 사례 및 고려 사항 [](styles-and-pattern-considerations-and-best-practices.md) 문서에 설명된 PDF 양식을 변경합니다.
* 알려진 문제 [문서를](known-issues.md) 참조하여 문제를 방지하십시오.

### 3.변환된 양식 검토 {#review-converted-forms}

실제 양식에는 AI/ML 기반 감지 로직에 의해 정확하게 캡처되지 않을 수 있는 필드 레이아웃, 이름 지정 또는 암시적 제안 측면에서 복잡한 데이터 캡처 요구 사항이 있을 수 있습니다. 자동 변환이 완료되면 검토 및 수정 [편집기를](review-correct-ui-edited.md) 사용하여 전환된 양식을 검토하고 필요한 업데이트를 수행하고 원하는 경험에 가까운 향상된 출력을 생성할 수 있습니다. 필요한 변경 작업을 수행한 후 변환을 위해 양식을 다시 보냅니다.

자동화된 전환에 소요되는 시간은 입력 양식 크기, 양식의 복잡성, 서비스 처리 큐의 대출 등 다양한 요인에 따라 달라집니다. 사용자는 폴더/파일의 상태 표시기를 통해 정기적으로 진행 상황을 통보 받습니다. 변환이 완료되면 구성된 이메일 주소로도 이메일 알림을 보냅니다.
