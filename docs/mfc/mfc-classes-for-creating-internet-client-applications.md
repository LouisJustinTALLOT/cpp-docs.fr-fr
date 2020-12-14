---
description: 'En savoir plus sur : classes MFC pour la création d’applications clientes Internet'
title: Classes MFC pour la création d'applications clientes Internet
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: c68110182b01d9c425090a926ee1e352ca3d3bdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280675"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>Classes MFC pour la création d'applications clientes Internet

MFC fournit les classes et fonctions globales suivantes pour l’écriture d’applications clientes Internet. La mise en retrait indique qu’une classe est dérivée de la classe sans mise en retrait au-dessus de celle-ci. `CGopherFile` et `CHttpFile` dérivent de `CInternetFile` , par exemple. Ces classes et fonctions globales sont déclarées dans AFXINET. H, except `CFileFind` , qui est déclaré dans AFX. H.

## <a name="classes"></a>Classes

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>Fonctions globales

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Conditions préalables pour les classes clientes Internet](prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet à l’aide de classes WinInet MFC](writing-an-internet-client-application-using-mfc-wininet-classes.md)
