---
title: Classes Internet Win32 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.win32
dev_langs:
- C++
helpviewer_keywords:
- Internet classes [MFC]
- WinInet classes [MFC], classes
- Win32 [MFC], Internet classes
- Windows API [MFC], Internet classes
ms.assetid: b49601d5-3025-4068-9408-316b54ee4375
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1b4adb3de5c6ec57b9f6bc2c48385916c3e5076
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445696"
---
# <a name="win32-internet-classes"></a>Classes Internet Win32

MFC encapsule l’Internet Win32 (WinInet) et la technologie ActiveX pour faciliter la programmation Internet.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).


[CInternetSession](../mfc/reference/cinternetsession-class.md)<br/>
Crée et initialise une ou plusieurs sessions Internet simultanées et, si nécessaire, décrit la connexion à un serveur proxy.

[CInternetConnection](../mfc/reference/cinternetconnection-class.md)<br/>
Gère votre connexion à un serveur Internet.

[CInternetFile](../mfc/reference/cinternetfile-class.md)<br/>
Cette classe et ses classes dérivées autorisent l’accès aux fichiers sur des systèmes distants qui utilisent des protocoles Internet.

[Objet CHttpConnection](../mfc/reference/chttpconnection-class.md)<br/>
Gère votre connexion à un serveur HTTP.

[CHttpFile](../mfc/reference/chttpfile-class.md)<br/>
Fournit les fonctionnalités pour rechercher et lire des fichiers sur un serveur HTTP.

[CGopherFile](../mfc/reference/cgopherfile-class.md)<br/>
Fournit les fonctionnalités permettant de rechercher et de lire des fichiers sur un serveur Gopher.

[CFtpConnection](../mfc/reference/cftpconnection-class.md)<br/>
Gère votre connexion à un serveur FTP.

[Objet CGopherConnection](../mfc/reference/cgopherconnection-class.md)<br/>
Gère votre connexion à un serveur gopher.

[CFileFind](../mfc/reference/cfilefind-class.md)<br/>
Effectue des locaux et des recherches de fichiers Internet.

[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)<br/>
Contribue à la recherche des fichiers Internet sur les serveurs FTP.

[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)<br/>
Contribue à la recherche des fichiers Internet sur les serveurs Gopher.

[Objet CGopherLocator](../mfc/reference/cgopherlocator-class.md)<br/>
Obtient un localisateur Gopher d'un serveur Gopher, détermine le type du localisateur et rend le localisateur accessible à `CGopherFileFind`.

[CInternetException](../mfc/reference/cinternetexception-class.md)<br/>
Représente une condition d'exception liée à une opération Internet.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

