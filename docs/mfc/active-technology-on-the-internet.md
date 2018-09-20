---
title: Technologie active sur Internet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet applications [MFC], Active technology
ms.assetid: 6f782aa1-5c2f-47a2-9e63-ddd0829d5a08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db0c93070fe8373cdd4494419ce1b71bf4068b14
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395116"
---
# <a name="active-technology-on-the-internet"></a>Technologie active sur Internet

Technologie active est une plateforme ouverte qui permet aux développeurs de créer des applications pour Internet, ou pour le réseau interne d’une société, appelé intranet et du contenu passionnant et dynamiques. Les principales technologies fournies par Microsoft pour la programmation Internet sont décrites ci-dessous.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).

## <a name="activex-controls"></a>Contrôles ActiveX

Contrôles ActiveX (anciennement contrôles OLE) sont des objets qui peuvent être insérées dans les pages Web ou toute autre application qui est un conteneur de contrôles ActiveX. Exemples incluent les boutons, les téléscripteurs et les contrôles chart. Pour plus d’informations, consultez [contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md).

## <a name="internet-data-download-services"></a>Services de téléchargement de données d’Internet

Données peuvent être téléchargées via Internet à l’aide de protocoles communs : HTTP, FTP et gopher. Les classes WinInet MFC facilitent le transfert de données à l’aide des protocoles HTTP, FTP et gopher en faisant abstraction les protocoles TCP/IP et WinSock. Les classes de moniker asynchrone de MFC fournissent un moyen pour télécharger des fichiers sans blocage et de restituer les objets volumineux de manière asynchrone. Pour plus d’informations, consultez [extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="active-scripts"></a>Scripts actifs

VBScript et autres langages de script connectent des contrôles et ajoutent des fonctionnalités interactives aux pages Web. Écriture de scripts déplace le traitement à partir du serveur au client. Par exemple, entrées de formulaire peuvent être validées sur le client, puis envoyées au serveur.

## <a name="html-extensions"></a>Extensions HTML

Les extensions HTML, telles que la balise object, ont été ajoutées pour prendre en charge les contrôles et les scripts.

## <a name="see-also"></a>Voir aussi

[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)<br/>
[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

