---
title: Root CA certificate doesn't appear
description: The root CA certificate configured for the Wired or Wireless Network policies does not appear in the GPO settings report if its subject contains only one name.
ms.date: 09/25/2020
author: Deland-Han 
ms.author: delhan
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika, milanmil
ms.prod-support-area-path: Certificates and public key infrastructure (PKI)
ms.technology: windows-server-security
---
# Certificate used by Wired or Wireless Network policies is missing in GPO settings report

This article provides a solution to an issue that certificate used by Wired or Wireless Network policies is missing in GPO settings report.

_Applies to:_ &nbsp; Windows 10 - all editions, Windows Server 2016, Windows Server 2019, Windows Server 2012 R2  
_Original KB number:_ &nbsp; 4047738

## Symptoms

Consider the following scenario:

- You configure one of the following policies of a group policy object (GPO) to use the **Microsoft: Smart Card or other certificate** authentication method:

  - Wired Network (IEEE 802.3)
  - Wireless Network (IEEE 802.11)
- You specify a root certification authority (CA) certificate to be used by the authentication.
- The certificate has a single subject name.

In this scenario, the certificate is missing in the GPO settings report.

Example settings and screenshots:

You set the following CA certificates to be used by the authentication:

- The first certificate has multiple subject names:

    CN = Contoso OneAD Root CA  
    DC = contoso  
    DC = com  

    :::image type="content" source="./media/root-ca-certificate-doesnt-appear/certificate-multiple-subject-names.png" alt-text="The first certificate has multiple subject names.":::

- The second certificate has a single subject name:

    CN = Contoso OneAD Root CA2

    :::image type="content" source="./media/root-ca-certificate-doesnt-appear/certificate-single-subject-name.png" alt-text="The second certificate has a single subject name.":::

In this example, the GPO settings report displays only the first certificate. The second certificate is missing.

:::image type="content" source="./media/root-ca-certificate-doesnt-appear/second-certificate-missing.png" alt-text="Certificate with multiple subject names are missing.":::  

## Cause

The issue occurs because of a code defect in Windows.

## Status

This issue affects only the GPO settings report. The certificate is successfully used by the authentication.
