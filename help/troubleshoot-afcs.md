---
title: '자동화된 양식 변환 서비스 문제 해결 '
seo-title: 'AFCS(Automated Forms Conversion Service) 문제 해결 '
description: '일반적인 AFCS 문제 및 해당 솔루션 '
seo-description: 일반적인 AFCS 문제 및 해당 솔루션
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: e905833e5b58c05aac612e3a8139eb7fb60ef4bf

---


# 자동화된 양식 변환 서비스 문제 해결


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## 일반적인 오류 {#commonerrors}

| 오류 | 예 |
|--- |--- |
| **오류** 메시지 <br> 액세스 토큰 헤더를 사용할 수 없습니다. <br><br>**이유&#x200B;**관리자가 여러 IMS 구성 또는 IMS 구성을 만든 경우 Adobe<br>Cloud의 ACS 서비스에 연결할 수 없습니다.<br><br>**해상도** 구성이 여러 개인 경우 모든 구성을 삭제하고 새 구성을 <br> [](configure-service.md#obtainpubliccertificates)만듭니다. <br> 단일 구성이 있는 경우 연결을 **[!UICONTROL Health Check]** 확인하는 [데 사용합니다](configure-service.md#createintegrationoption). | ![액세스 토큰 헤더를 사용할 수 없습니다.](assets/invalid-ims-configuration.png) |
| **오류** 메시지 <br> 서비스에 연결할 수 없습니다.  <br><br>**Automated **Forms Conversion Service<br>클라우드 서비스에 잘못된 서비스 URL이나 서비스 URL이 언급되지 않은 이유<br><br>**Automated** Forms <br> Conversion Service Cloud [](configure-service.md#configure-the-cloud-service) 서비스의 Correct Service URL. | ![서비스에 연결할 수 없습니다.](assets/wrong-endpoint-configured.png) |
| **오류** 메시지 <br> 서비스에서 양식을 변환하지 못했습니다.  <br><br>**Reason **<br>Network connectivity issues at your end, the service is down due to scheduled maintenance or on Adobe Cloud.<br><br>**문제 해결** 최종 <br> 시 네트워크 연결 문제를 해결하고 https://status.adobe.com/에서 서비스 상태를 확인하여 계획된 또는 예상치 못한 서비스 중단이 있는지 확인하십시오. | ![서비스에 연결할 수 없습니다.](assets/service-failure.png) |
| **오류 메시지** 페이지 수가 <br> 15개를 초과합니다.  <br><br>**이유&#x200B;**소스 양식의 길이가<br>15페이지를 넘습니다.<br><br>**해상도** Adobe Acrobat을 사용하여 15페이지 이상의 양식을 분할할 수 있습니다 <br> . 양식의 페이지 수를 15개 미만으로 가져옵니다. | ![서비스에 연결할 수 없습니다.](assets/number-of-pages.png) |
| **오류** 메시지 <br> 파일 수가 15개를 초과합니다.  <br><br>**이유&#x200B;**폴더에는<br>15개 이상의 양식이 포함되어 있습니다.<br><br>**해상도** 폴더의 양식 수를 15개 이하로 가져옵니다 <br> . 폴더의 총 페이지 수를 50개 미만으로 가져옵니다. 폴더 크기를 10MB 이하로 가져옵니다. 양식을 하위 폴더에 보관하지 마십시오. 원본 양식을 8-15개의 양식으로 구성할 수 있습니다. | ![서비스에 연결할 수 없습니다.](assets/number-of-pages.png) |
| **오류** 메시지 <br> 소스 파일 형식은 지원되지 않습니다.  <br><br>**이유&#x200B;**소스 양식이 포함된 폴더에 지원되지 않는 파일이 있습니다<br>.<br><br>**해결** . <br> 서비스는 .xdp 및 .pdf 파일만 지원합니다. 폴더에서 다른 확장자가 있는 파일을 제거하고 변환을 실행합니다. | ![서비스에 연결할 수 없습니다.](assets/unsupported-file-formats.png) |
| **오류 메시지** 스캔한 <br> 양식은 지원되지 않습니다.  <br><br>**이유&#x200B;**PDF 양식에는<br>양식의 스캔한 이미지만 포함되어 있으며 컨텐츠 구조는 포함되어 있지 않습니다.<br><br>**해상도** 서비스는 <br> 스캔한 양식이나 양식의 이미지를 즉시 사용 가능한 양식으로 변환하는 것을 지원하지 않습니다. 그러나 Adobe Acrobat을 사용하면 양식의 이미지를 PDF 양식으로 변환할 수 있습니다. 그런 다음 서비스를 사용하여 PDF 양식을 적응형 양식으로 변환합니다. Acrobat에서 변환하려면 항상 양식의 고품질 이미지를 사용하십시오. 전환의 품질을 향상시킵니다. | ![서비스에 연결할 수 없습니다.](assets/scanned-forms-error.png) |
| **오류 메시지** 암호화된 PDF <br> 양식은 지원되지 않습니다.  <br><br>**이유&#x200B;**폴더에는<br>암호화된 PDF 양식이 포함되어 있습니다.<br><br>**해상도** <br> 서비스에서 암호화된 PDF 양식을 적응형 양식으로 변환할 수 없습니다. 암호화를 제거하고 암호화되지 않은 양식을 업로드하고 변환을 실행합니다. | ![서비스에 연결할 수 없습니다.](assets/secured-pdf-form.png) |
| **오류 메시지** 메타 모델 <br> JSON 스키마를 구문 분석할 수 없습니다.  <br><br>**이유&#x200B;**<br>서비스에 제공된 JSON 스키마 형식이 제대로 지정되지 않았거나, 잘못된 문자를 포함하거나, 구성 요소를 매핑하기 위해 잘못된 구문을 사용합니다.<br><br>**해상도** JSON <br> 파일의 형식을 확인합니다. 모든 온라인 JSON 유효성 검사기를 사용하여 스키마의 서식 및 구조를 확인할 수 있습니다. 메타 모델 [구문에 대한 자세한 내용은 기본 메타 모델](extending-the-default-meta-model.md) 아티클 확장을 참조하십시오. | ![서비스에 연결할 수 없습니다.](assets/invalid-meta-model-schema.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->