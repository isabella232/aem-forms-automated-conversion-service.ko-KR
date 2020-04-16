---
title: '자동화된 양식 변환 서비스 문제 해결 '
seo-title: 'AFCS(Automated Forms Conversion Service) 문제 해결 '
description: '일반적인 AFCS 문제 및 해당 솔루션 '
seo-description: 일반적인 AFCS 문제 및 해당 솔루션
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 4b9f3f4fe3b3901cb99c9374ff40e8f49855237f

---


# 자동화된 양식 변환 서비스 문제 해결


이 문서에서는 자동화된 양식 변환 서비스 프로덕션 환경에서 발생할 수 있는 설치, 구성 및 관리 문제에 대한 정보를 제공합니다. 또한 일반적인 오류 메시지에 대한 기본 문제 해결 단계 및 설명을 제공합니다.

## 일반적인 오류 {#commonerrors}

| 오류 | 예 |
|--- |--- |
| **오류** 메시지 <br> 액세스 토큰 헤더를 사용할 수 없습니다. <br><br>**이유&#x200B;**관리자가 여러 IMS 구성 또는 IMS 구성을 만든 경우 Adobe<br>Cloud의 ACS 서비스에 연결할 수 없습니다.<br><br>**해상도** 구성이 여러 개인 경우 모든 구성을 삭제하고 새 구성을 <br> [](configure-service.md#obtainpubliccertificates)만듭니다. <br> 단일 구성이 있는 경우 연결을 **[!UICONTROL Health Check]** 확인하는 [데 사용합니다](configure-service.md#createintegrationoption). | ![액세스 토큰 헤더를 사용할 수 없습니다.](assets/invalid-ims-configuration.png) |
| **오류** 메시지 <br> 서비스에 연결할 수 없습니다.  <br><br>**Automated **Forms Conversion Service<br>클라우드 서비스에 잘못된 서비스 URL이나 서비스 URL이 언급되지 않은 이유<br><br>**Automated** Forms <br> Conversion Service Cloud [](configure-service.md#configure-the-cloud-service) 서비스의 Correct Service URL. | ![서비스에 연결할 수 없습니다.](assets/wrong-endpoint-configured.png) |
| **오류** 메시지 <br> 서비스에서 양식을 변환하지 못했습니다.  <br><br>**Adobe **Cloud에서<br>예약된 유지 관리 또는 중단으로 인해 네트워크 연결 문제가 종료되었거나 서비스가 다운된 원인<br><br>**문제 해결** 최종 <br> 시 네트워크 연결 문제를 해결하고 https://status.adobe.com/에서 서비스 상태를 확인하여 계획된 서비스 또는 예상치 못한 서비스 중단을 확인하십시오. | ![서비스에 연결할 수 없습니다.](assets/service-failure.png) |
| **오류 메시지** 페이지 수가 <br> 15개를 초과합니다.  <br><br>**이유&#x200B;**소스 XDP 및 PDF 양식이 포함된 폴더에 15개 이상의 파일이 있습니다<br>.<br><br>**해상도** 폴더의 양식 수를 15개 이하로 가져옵니다 <br> . 폴더의 총 페이지 수를 50개 미만으로 가져옵니다. 폴더 크기를 10MB 이하로 가져옵니다. 양식을 하위 폴더에 보관하지 마십시오. 소스 문서를 8-15개의 문서로 일괄 구성할 수 있습니다. | ![서비스에 연결할 수 없습니다.](assets/number-of-pages.png) |
| **오류** 메시지 <br> 소스 파일 형식은 지원되지 않습니다.  <br><br>**이유&#x200B;**소스 양식이 포함된 폴더에 지원되지 않는 파일이 있습니다<br>.<br><br>**해결** . <br> 서비스는 .xdp 및 .pdf 파일만 지원합니다. 폴더에서 다른 확장자가 있는 파일을 제거하고 변환을 실행합니다. | ![서비스에 연결할 수 없습니다.](assets/unsupported-file-formats.png) |
| **오류 메시지** 스캔한 <br> 양식은 지원되지 않습니다.  <br><br>**이유&#x200B;**<br>PDF 양식에는 양식의 스캔한 이미지만 포함되어 있으며 컨텐츠 구조는 포함되어 있지 않습니다.<br><br>**해상도** 서비스는 <br> 스캔한 양식이나 양식의 이미지를 즉시 사용 가능한 양식으로 변환하는 것을 지원하지 않습니다. 그러나 Adobe Acrobat을 사용하면 양식의 이미지를 PDF 양식으로 변환할 수 있습니다. 그런 다음 서비스를 사용하여 PDF 양식을 적응형 양식으로 변환합니다. Acrobat에서 변환하려면 항상 양식의 고품질 이미지를 사용하십시오. 전환의 품질을 향상시킵니다. | ![서비스에 연결할 수 없습니다.](assets/scanned-forms-error.png) |