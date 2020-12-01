---
title: 자동 양식 전환 서비스 구성
description: automated forms conversion 서비스를 사용할 AEM 인스턴스 준비
translation-type: tm+mt
source-git-commit: 741ff89370a5215b70d90c49eea220171efe9339
workflow-type: tm+mt
source-wordcount: '2547'
ht-degree: 12%

---


# 자동 양식 전환 서비스 구성 {#about-this-help}

이 도움말은 AEM 관리자가 Automated forms conversion 서비스를 구성하여 PDF forms을 적응형 양식으로 변환하는 방법을 설명합니다. 이 도움말은 조직의 IT 및 AEM 관리자를 위한 것입니다. 제공된 정보는 이 도움말을 읽는 사람이 다음 기술을 잘 알고 있다는 가정을 기반으로 합니다.

* Adobe Experience Manager 및 AEM 패키지 설치, 구성 및 관리,

* Linux 및 Microsoft Windows 운영 체제 사용,

* SMTP 메일 서버 구성

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## 온보딩{#onboarding}

이 서비스는 AEM 6.4 Forms 및 AEM 6.5 Forms On-Premise 기간제 고객과 Adobe Managed Service 기업 고객에게 무료로 제공됩니다. Adobe 영업팀 또는 Adobe 담당자에게 문의하여 서비스 액세스 권한을 요청할 수 있습니다.

Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 책임자는 해당 서비스에 연결할 조직의 AEM Forms 개발자(사용자)에게 액세스 권한을 부여할 수 있습니다.

## 전제 조건 {#prerequisites}

automated forms conversion 서비스를 사용하려면 다음이 필요합니다.

* 조직에서 automated forms conversion 서비스를 사용할 수 있습니다.
* 전환 서비스에 대한 관리자 권한이 있는 Adobe ID 계정
* 최신 AEM 서비스 팩 AEM 6.4 또는 AEM 6.5 작성자 인스턴스 실행
* 양식-사용자 그룹에 속한 AEM 사용자(AEM 인스턴스)

## 환경 설정 {#setuptheservice}

서비스를 사용하기 전에 AEM 작성자 인스턴스를 준비하여 Adobe Cloud에서 실행되는 서비스에 연결합니다. 나열된 시퀀스에서 다음 단계를 수행하여 서비스에 대한 인스턴스를 준비합니다.

1. [AEM 6.4 또는 AEM 6.5 다운로드 및 설치](#aemquickstart)
1. [최신 AEM 서비스 팩 다운로드 및 설치](#servicepack)
1. [최신 AEM Forms 추가 기능 패키지 다운로드 및 설치](#downloadaemformsaddon)
1. (선택 사항) [최신 커넥터 패키지 다운로드 및 설치](#installConnectorPackage)
1. [사용자 정의 테마 및 템플릿 만들기](#referencepackage)

### AEM 6.4 또는 AEM 6.5 {#aemquickstart} 다운로드 및 설치


automated forms conversion 서비스는 AEM 작성자 인스턴스에서 실행됩니다. AEM 작성자 인스턴스를 설정하려면 AEM 6.4 또는 AEM 6.5가 필요합니다. AEM을 실행하지 않은 경우 다음 위치에서 다운로드하십시오.

* 기존 AEM 고객의 경우 [Adobe 라이선스 웹 사이트](http://licensing.adobe.com)에서 AEM 6.4 또는 AEM 6.5를 다운로드하십시오.

* Adobe 파트너인 경우 [Adobe 파트너 교육 프로그램](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q)을 사용하여 AEM 6.4 또는 AEM 6.5를 요청하십시오.

AEM을 다운로드한 후 AEM 작성자 인스턴스를 설정하는 방법은 [배포 및 유지 관리](https://helpx.adobe.com/kr/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall)를 참조하십시오.

### AEM 최신 서비스 팩 다운로드 및 설치 {#servicepack}

최신 AEM 서비스 팩 다운로드 및 설치. 자세한 내용은 또는 [AEM 6.4 서비스 팩 릴리스 노트](https://helpx.adobe.com/kr/experience-manager/6-4/release-notes/sp-release-notes.html) 또는 [AEM 6.5 서비스 팩 릴리스 노트](https://helpx.adobe.com/kr/experience-manager/6-5/release-notes/sp-release-notes.html)를 참조하십시오.

### AEM Forms 추가 기능 패키지 {#downloadaemformsaddon} 다운로드 및 설치

AEM 인스턴스에는 기본 양식 기능이 포함되어 있습니다. 전환 서비스에는 AEM Forms의 모든 기능이 필요합니다. AEM Forms의 모든 기능을 사용할 수 있도록 AEM Forms Add-on 패키지를 다운로드하고 설치하십시오. 전환 서비스를 설정하고 실행하려면 패키지가 필요합니다. 자세한 지침은 [데이터 캡처 기능 설치 및 구성을 참조하십시오.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Add-on 패키지를 설치한 후 반드시 설치 후 구성을 수행해야 합니다.


### (선택 사항) 커넥터 패키지 {#installConnectorPackage} 다운로드 및 설치

커넥터 패키지는 AFC-2020.03.1 릴리스에서 제공되는 [자동 검색 논리 섹션](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) 기능 및 향상된 기능에 대한 빠른 액세스를 제공합니다. AFC-2020.03.1로 전달되는 기능 및 개선이 필요하지 않은 경우 패키지를 설치하지 마십시오. AEM 패키지에서 [커넥터 패키지를 다운로드할 수 있습니다. share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).


### 사용자 정의 테마 및 템플릿 만들기 {#referencepackage}

[프로덕션 모드](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html)(nosamplecontent runmode)에서 AEM을 시작하는 경우 참조 패키지가 설치되지 않습니다. 참조 패키지에는 샘플 테마와 템플릿이 포함되어 있습니다. automated forms conversion 서비스를 사용하려면 PDF forms을 응용 양식으로 변환하려면 하나 이상의 테마와 템플릿이 필요합니다. 사용자 정의 테마 및 템플릿을 만들고 [서비스 구성](#configure-the-cloud-service)을 지정하여 서비스를 사용하기 전에 사용자 정의 템플릿과 테마를 사용하십시오.

## 서비스 구성 {#configure-the-service}

서비스를 구성하고 로컬 인스턴스를 Adobe Cloud에서 실행되는 서비스와 연결하기 전에 서비스에 연결하는 데 필요한 개인 및 권한에 대해 알아보십시오. 서비스는 두 가지 서로 다른 유형의 개인, 관리자 및 개발자를 사용합니다.

* **관리자**:관리자는 조직의 Adobe 소프트웨어 및 서비스를 관리할 책임이 있습니다. 관리자는 조직의 개발자에게 Adobe Cloud에서 실행되는 Automated forms conversion 서비스에 연결할 수 있는 액세스 권한을 부여합니다. 관리자가 조직에 대해 프로비저닝되면 관리자는 **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']** 제목으로 이메일을 수신합니다. 관리자의 경우, 앞서 언급한 제목이 있는 이메일이 포함된 사서함을 확인하고 [조직 개발자에게 액세스 권한 부여](#adduseranddevs)로 진행하십시오.

![관리자 액세스 권한 부여 이메일](assets/admin-console-adobe-io-access-grantedx75.png)

* **개발자**:개발자는 로컬 AEM Forms 작성자 인스턴스를 Adobe Cloud에서 실행되는 Automated forms conversion 서비스에 연결합니다. 관리자가 Automated forms conversion 서비스에 연결할 수 있는 권한을 개발자에게 부여하면, 이제 귀사에서 조직의 Adobe API 통합을 관리하기 위한 개발자 액세스 권한이 있는 이메일이 개발자에게 전송됩니다. 개발자인 경우, 전술한 제목이 있는 전자 메일이 있는지 확인하고 [Adobe Cloud의 Automated forms conversion 서비스에 로컬 AEM 인스턴스를 연결합니다.](#connectafcadobeio)

![개발자 액세스 권한 부여 이메일](assets/email-developer-accessx94.png)

### (관리자에게만 해당) 조직의 개발자에게 액세스 권한 부여 {#adduseranddevs}

Adobe이 조직에 대한 액세스를 활성화하고 관리자에게 필요한 권한을 제공하면 관리자는 Admin Console에 로그인하여(아래 세부 지침) 프로파일을 만들고 개발자를 프로필에 추가할 수 있습니다. 개발자는 Automated forms conversion 클라우드에서 로컬 AEM Forms 인스턴스를 Adobe 서비스에 연결할 수 있습니다.

개발자는 전환 서비스를 실행하도록 지정된 조직의 구성원이다. Adobe Automated forms conversion 서비스 프로필에 추가된 개발자만 Automated forms conversion 서비스를 사용할 수 있습니다. 아래 단계를 수행하여 프로파일을 만들고 여기에 개발자를 추가합니다. 조직의 개발자에게 필요한 액세스 권한을 부여하려면 하나 이상의 프로필이 필요합니다.

1. [Admin Console](https://adminconsole.adobe.com/)에 로그인합니다. automated forms conversion 서비스를 사용하여 로그인하려면 제공된 관리자의 **Adobe ID**&#x200B;을(를) 사용하십시오. 다른 ID 또는 Federated ID을 로그인에 사용하지 마십시오.
1. **[!UICONTROL Automated Forms Conversion]** 옵션을 클릭합니다.
1. **[!UICONTROL Products]** 탭에서 **[!UICONTROL New Profile]**&#x200B;을 클릭합니다.
1. 프로필에 대해 **[!UICONTROL Name]**, **[!UICONTROL Display Name]** 및 **[!UICONTROL Description]**&#x200B;를 지정합니다. 클릭 **[!UICONTROL Done]**. 프로필이 만들어집니다.

   ![새 프로필에 대한 세부 사항을 지정합니다.](assets/create-new-profile-details.png)

1. 프로필에 개발자 추가 개발자를 추가하려면:
   1. [Admin Console](https://adminconsole.adobe.com/enterprise)에서 개요 탭으로 이동합니다.
   1. 필요한 제품 카드에서 **[!UICONTROL Assign Developers]**&#x200B;을 클릭합니다.
   1. 개발자 이메일 주소와 이름(선택 사항)을 입력합니다.
   1. 제품 프로필을 선택합니다. 탭하기 **[!UICONTROL Save]**.

모든 사용자에 대해 위 단계를 반복합니다.  개발자 추가에 대한 자세한 내용은 [개발자 관리](https://helpx.adobe.com/enterprise/using/manage-developers.html)를 참조하십시오.

관리자가 개발자를 Adobe I/O 프로파일에 추가하면 개발자에게 이메일을 통해 알림을 제공합니다. 이메일을 받은 개발자는 Creative Cloud[에서 Automated forms conversion 서비스와 함께 로컬 AEM Forms 인스턴스를 연결할 수 있습니다.](#connectafcadobeio)

### (개발자만) 로컬 AEM Forms 인스턴스를 Adobe 클라우드 {#connectafcadobeio}의 Automated forms conversion 서비스에 연결

관리자가 개발자 액세스 권한을 제공하면 로컬 AEM Forms 인스턴스를 Adobe Cloud에서 실행되는 Automated forms conversion 서비스에 연결할 수 있습니다. 나열된 시퀀스에서 다음 단계를 수행하여 AEM Forms 인스턴스를 서비스에 연결합니다.

* [이메일 알림 구성](configure-service.md#configureemailnotification)
* [forms-users 그룹에 사용자 추가](#adduserstousergroup)
* [공용 인증서 받기](#obtainpubliccertificates)
* [Adobe 개발자 콘솔에서 서비스 API 구성](#createintegration)
* [클라우드 서비스 구성](configure-service.md#configure-the-cloud-service)

#### 이메일 알림 {#configureemailnotification} 구성

automated forms conversion 서비스는 일 CQ 메일 서비스를 사용하여 이메일 알림을 보냅니다. 이러한 이메일 알림에는 성공적인 전환이나 실패한 전환에 대한 정보가 포함되어 있습니다. 알림을 받지 않기로 선택한 경우 이 단계를 건너뜁니다. 다음 단계를 수행하여 CQ 일 메일 서비스를 구성합니다.

1. `http://localhost:4502/system/console/configMgr`의 AEM 구성 관리자로 이동
1. 일 CQ 메일 서비스 구성을 엽니다. **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** 및 **[!UICONTROL From address]** 필드의 값을 지정합니다. 클릭 **[!UICONTROL Save]**.

   이메일 서비스 공급자 또는 IT 관리자에게 문의하여 SMTP 서버의 호스트 이름 및 포트에 대한 정보를 확인할 수 있습니다. 보낸 사람 필드에서 유효한 이메일 주소를 사용할 수 있습니다. 예: notification@example.com 또는 donotreply@example.com.

1. **[!UICONTROL Day CQ Link Externalizer]** 구성을 엽니다. **[!UICONTROL Domains]** 필드에서 로컬, 작성자 및 게시 인스턴스의 실제 호스트 이름 또는 IP 주소 및 포트 번호를 지정합니다. 클릭 **[!UICONTROL Save]**.

#### Forms-users 그룹 {#adduserstousergroup}에 사용자 추가

서비스를 실행하도록 지정된 AEM 사용자의 프로필에 이메일 주소를 지정합니다. 사용자가 [forms user](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) 그룹의 구성원인지 확인합니다. 전환이 실행되는 사용자의 이메일 주소로 이메일이 전송됩니다. 사용자의 이메일 주소를 지정하고 사용자를 양식 사용자 그룹에 추가하려면:

1. AEM 관리자로 AEM Forms 작성자 인스턴스에 로그인합니다. 로컬 AEM 자격 증명을 사용하여 로그인합니다. Adobe ID을 사용하여 로그인하지 마십시오. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**&#x200B;을 누릅니다.

1. 전환 서비스를 실행하도록 지정된 사용자를 선택하고 **[!UICONTROL Properties]**&#x200B;을 누릅니다. 사용자 설정 편집 페이지가 열립니다.
1. **[!UICONTROL Email]** 필드에 이메일 주소를 지정하고 **[!UICONTROL Save]**&#x200B;을 누릅니다. 전환 성공 또는 실패 시 지정된 이메일 주소로 이메일이 전송됩니다.
1. **그룹** 탭을 누릅니다. 그룹 선택 탭에서 **forms-users** 그룹을 입력하고 선택합니다. **저장 및 닫기**&#x200B;를 누릅니다. 사용자가 이제 양식 사용자 그룹의 구성원입니다.

#### 공용 인증서 가져오기 {#obtainpubliccertificates}

공개 인증서를 사용하면 Adobe I/O에서 프로필을 인증할 수 있습니다.

1. AEM Forms 작성자 인스턴스에 로그인합니다. 다음으로 이동 **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. 탭하기 **[!UICONTROL Create]**. **[!UICONTROL Adobe IMS Technical Account Configuration]** 페이지가 나타납니다.

   ![Adobe IMS 기술 계정 구성 페이지](assets/adobe-ims-technical-account-configuration.png)

1. 클라우드 솔루션에서 **[!UICONTROL Automated Forms Conversion Service]**&#x200B;을 선택합니다.

1. **[!UICONTROL Create new certificate]** 확인란을 선택하고 별칭을 지정합니다. 별칭은 대화 상자의 이름으로 사용됩니다. 탭하기 **[!UICONTROL Create certificate]**. 대화 상자가 나타납니다. 클릭 **[!UICONTROL OK]**. 인증서가 만들어집니다.

1. **[!UICONTROL Download Public Key]**&#x200B;을(를) 누르고 컴퓨터에 *AEM-Adobe-IMS.crt* 인증서 파일을 저장합니다. 인증서 파일은 [Adobe 개발자 콘솔](#createintegration)에서 서비스 API를 구성하는 데 사용됩니다. 탭하기 **[!UICONTROL Next]**.

1. 다음을 지정합니다.

   * 제목:제목을 지정합니다.
   * 인증 서버:[https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   다른 필드는 비워 둡니다(나중에 제공). 페이지를 열어 두십시오.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Adobe 장치 콘솔 {#createintegration}에 서비스 API 구성

automated forms conversion 서비스를 사용하려면 프로젝트를 만들고 Adobe 개발자 콘솔의 프로젝트에 자동화된 Forms 구성 서비스 API를 추가하십시오. 통합은 API 키, 클라이언트 암호, 페이로드(JWT)를 생성합니다.

1. [https://console.adobe.io/](https://console.adobe.io/)에 로그인합니다. 관리자가 Adobe I/O 콘솔에 로그인하여 사용할 수 있도록 프로비저닝한 개발자 계정인 Adobe ID을 사용하십시오.
1. 오른쪽 상단 모서리에서 조직을 선택합니다. 조직을 모르는 경우에는 관리자에게 문의하십시오.
1. 탭하기 **[!UICONTROL Create new project]**. 새 프로젝트를 시작하는 화면이 나타납니다. 탭하기 **[!UICONTROL Add API]**. 계정에 대해 활성화된 모든 API 목록이 있는 화면이 나타납니다.
1. **[!UICONTROL Automated Forms Conversion service]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;을 누릅니다. API를 구성하는 화면이 나타납니다.
1. [!UICONTROL Upload your public key] 옵션을 선택하고 [공용 인증서 받기](#obtainpubliccertificates) 섹션에서 다운로드한 AEM-Adobe-IMS.crt 파일을 업로드하고 **[!UICONTROL Next]**&#x200B;을 누릅니다. [새 서비스 계정(JWT) 자격 증명 만들기] 옵션이 나타납니다. 탭하기 **[!UICONTROL Next]**.
1. 제품 프로필을 선택하고 **[!UICONTROL Save configured API]**&#x200B;을 누릅니다. [조직 개발자에게 액세스 권한을 부여하는 동안 만든 프로필을 선택합니다. ](#adduseranddevs) 선택할 프로필을 모르는 경우 관리자에게 문의하십시오.
1. 로컬 AEM 인스턴스를 Automated forms conversion 서비스에 연결하는 데 필요한 API 키, 클라이언트 암호 및 기타 정보를 보려면 **[!UICONTROL Service Account (JWT)]**&#x200B;을 누릅니다. 페이지의 정보는 로컬 컴퓨터에서 IMS 구성을 만드는 데 사용됩니다.

1. 로컬 인스턴스에서 IMS 구성 페이지를 엽니다. [공개 인증서 받기](#obtainpubliccertificates) 섹션의 끝에서 페이지를 열어 두었습니다.

   ![제목, API 키, 클라이언트 암호 및 페이로드 지정  ](assets/ims-configuration-details.png)

1. Adobe IMS 기술 페이지에서 API 키와 클라이언트 암호를 지정합니다. Adobe 개발자 콘솔 페이지의 서비스 계정(JWT)에 지정된 값을 사용합니다.

   >[!NOTE]
   >
   >
   >페이로드에 대해 Adobe 개발자 콘솔의 서비스 계정(JWT) 페이지의 JWT 생성 탭에 제공된 코드를 사용합니다.

1. 탭하기 **[!UICONTROL Save]**. IMS 구성이 생성됩니다.

   >[!CAUTION]
   >
   >하나의 IMS 구성만 만듭니다. 두 개 이상의 IMS 구성을 만들지 마십시오.

1. IMS 구성을 선택하고 **[!UICONTROL Check Health]**&#x200B;을 누릅니다. 대화 상자가 나타납니다. 탭하기 **[!UICONTROL Check]**. 연결에 성공하면 *토큰이 검색되었습니다*&#x200B;라는 메시지가 나타납니다.

   ![성공적으로 연결되면 검색된 토큰이 표시됩니다.  ](assets/health-check.png)

   <br/> <br/>

#### 클라우드 서비스 {#configure-the-cloud-service} 구성

AEM 인스턴스를 전환 서비스에 연결하는 클라우드 서비스 구성을 만듭니다. 또한 전환용 템플릿, 테마 및 양식 조각을 지정할 수 있습니다. 각 양식 세트에 대해 별도의 클라우드 서비스 구성을 만들 수 있습니다. 예를 들어 영업 부서 양식에 대해 별도의 구성을 사용하고 고객 지원 양식에 대해 별도의 구성을 설정할 수 있습니다. 클라우드 서비스 구성을 만들려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**&#x200B;을 누릅니다.
1. **[!UICONTROL Global]** 폴더를 누르고 **[!UICONTROL Create]**&#x200B;을 누릅니다. automated forms conversion 구성을 만드는 페이지가 나타납니다. 전역 폴더에 구성이 만들어집니다. 이미 존재하는 다른 폴더에 구성을 만들거나 구성에 대한 새 폴더를 만들 수도 있습니다.

1. **[!UICONTROL Create Automated Forms Conversion Configuration]** 페이지에서 다음 필드에 대한 값을 지정하고 **[!UICONTROL Next]**&#x200B;을 누릅니다.

   | 필드 | 설명 |
   |--- |--- |
   | 제목 | 구성에 대한 고유 제목입니다. 전환이 시작되는 데 사용되는 UI에 제목이 표시됩니다. |
   | 이름 | 구성에 대한 고유 이름입니다. 구성은 지정된 이름으로 CRX-Repository에 저장됩니다. 이름은 제목과 같을 수 있습니다. |
   | 축소판 위치 | 구성에 대한 축소판의 위치입니다. |
   | 서비스 URL | Adobe 클라우드 Automated forms conversion 서비스의 URL입니다. `https://aemformsconversion.adobe.io/` URL을 사용합니다. |
   | 템플릿 | 변환된 양식에 적용할 기본 템플릿입니다. 변환을 시작하기 전에 항상 다른 템플릿을 지정할 수 있습니다. 템플릿에는 적응형 양식의 기본 구조와 초기 컨텐츠가 포함되어 있습니다. 즉시 제공되는 템플릿에서 템플릿을 선택할 수 있습니다. 사용자 지정 템플릿을 만들 수도 있습니다. |
   | 테마 | 변환된 양식에 적용할 기본 테마입니다. 변환을 시작하기 전에 항상 다른 테마를 지정할 수 있습니다.  아이콘을 클릭하여 특별한 방식으로 제공되는 테마를 선택할 수 있습니다. 사용자 정의 테마를 만들 수도 있습니다. |
   | 기존 조각 | 기존 조각 위치(있는 경우). |
   | 사용자 지정 메타 모델 | 사용자 지정 메타 모델의 .schema.json 파일 경로입니다. |



1. **[!UICONTROL Create Automated Forms Conversion Configuration]** 페이지의 **[!UICONTROL Advanced]** 탭에서 다음 필드의 값을 지정합니다.

   <table>
   <thead>
   <tr>
   <th>필드</th>
   <th>설명</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >기록 문서 생성</td>
   <td>변환된 양식에 대해 기록 문서를 자동으로 생성하려면 이 옵션을 선택합니다. 이 옵션은 XFA 기반 양식(XDP 및 PDF forms)에만 적용됩니다. 이 옵션을 활성화하면 양식을 제출한 후 고객이 나중에 참조할 수 있도록 양식에 입력한 정보를 인쇄 또는 문서 형식으로 기록하도록 할 수 있습니다. 이를 기록 문서라고 합니다.</td>
   </tr>
   <tr>
   <td>Analytics 활성화</td>
   <td>변환된 모든 양식에서 Adobe Analytics을 활성화하려면 옵션을 선택합니다. 옵션을 사용하기 전에 AEM Forms 인스턴스에 대해 Adobe Analytics이 활성화되어 있는지 확인합니다.</td>
   </tr>
   </tbody>
   </table>

   * 소스가 확장명이 .XDP인 XFA 기반 양식일 경우 출력 DOR이 XFA 레이아웃을 유지하면 변환 서비스는 즉시 사용 가능한 템플릿을 사용하여 다른 XFA 기반 양식에 대한 DOR를 생성합니다.
   * XFA 양식이 제출되면 양식의 제출 데이터가 XML 요소 또는 속성으로 저장됩니다. 예, `<Amount currency="USD"> 10.00 </Amount>`. 통화가 속성 및 통화 금액으로 저장되고 10.00은 요소로 저장됩니다. 적응형 양식의 제출 데이터에는 특성이 없으며 요소만 있습니다. 따라서 XFA 기반 양식이 적응형 양식으로 변환되면 적응형 양식 제출 데이터에는 각 해당 속성에 대한 요소가 포함됩니다. 예,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. 탭하기 **[!UICONTROL Create]**. 클라우드 구성이 만들어집니다. AEM Forms 인스턴스를 사용하여 기존 양식을 적응형 양식으로 변환할 수 있습니다.
