---
title: '자동화된 양식 변환 서비스 문제 해결 '
seo-title: 'AFCS(Automated Forms Conversion Service) 문제 해결 '
description: '일반적인 AFCS 문제 및 해당 솔루션 '
seo-description: 일반적인 AFCS 문제 및 해당 솔루션
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: ccf30bc990c1a7cdb261332403668af6f35aeb9e

---


# 자동화된 양식 변환 서비스 문제 해결


이 문서에서는 자동화된 양식 변환 서비스 프로덕션 환경에서 발생할 수 있는 설치, 구성 및 관리 문제에 대한 정보를 제공합니다. 또한 일반적인 오류 메시지에 대한 기본 문제 해결 단계 및 설명을 제공합니다.

## 일반적인 오류 {#commonerrors}

| 오류 | 예 |
|--- |--- |
| **오류** 메시지 <br> 액세스 토큰 헤더를 사용할 수 없습니다. <br><br>**이유&#x200B;**관리자가 여러 IMS 구성 또는 IMS 구성을 만든 경우 Adobe<br>Cloud의 ACS 서비스에 연결할 수 없습니다.<br><br>**해상도** 구성이 여러 개인 경우 모든 구성을 삭제하고 새 구성을 <br> [](configure-service.md#obtainpubliccertificates)만듭니다. <br> 단일 구성이 있는 경우 연결을 **[!UICONTROL Health Check]** 확인하는 [데 사용합니다](configure-service.md#createintegrationoption). | ![액세스 토큰 헤더를 사용할 수 없습니다.](assets/invalid-ims-configuration.png) |
| **오류** 메시지 <br> 서비스에 연결할 수 없습니다.  <br><br>**Automated **Forms Conversion Service<br>클라우드 서비스에 잘못된 서비스 URL이나 서비스 URL이 언급되지 않은 이유<br><br>**Automated** Forms <br> Conversion Service Cloud [](configure-service.md#configure-the-cloud-service) 서비스의 Correct Service URL. | ![서비스에 연결할 수 없습니다.](assets/wrong-endpoint-configured.png) |
| **오류** 메시지 <br> 서비스에서 양식을 변환하지 못했습니다.  <br><br>**Adobe **Cloud에서<br>예약된 유지 관리 또는 중단으로 인해 네트워크 연결 문제가 종료되었거나 서비스가 다운된 원인<br><br>**해결책** <br> 네트워크 연결 문제를 해결하고 https://status.adobe.com/#에서 서비스 상태를 확인하여 계획된 또는 예상치 못한 서비스 중단이 있는지 확인하십시오. | ![서비스에 연결할 수 없습니다.](assets/service-failure.png) |
