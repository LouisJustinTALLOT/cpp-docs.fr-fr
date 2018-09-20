---
title: Choix de conception d’application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11941323f90d8eadbf8acdb0431f51afad1d1e0c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397869"
---
# <a name="application-design-choices"></a>Choix en matière de conception d'applications

Cet article décrit certains des problèmes de conception à prendre en compte lors de la programmation pour Internet.

Les sujets abordés dans cet article sont les suivantes :

- [Intranet et Internet](#_core_intranet_versus_internet)

- [Application cliente ou serveur](#_core_client_or_server_application)

- [](#_core_the_web_page)

- [Navigateur ou une Application autonome](#_core_browser_or_standalone)

- [COM sur Internet](#_core_com_on_the_internet)

- [Services de téléchargement de données client](#_core_client_data_download_services)

Si vous êtes prêt à commencer à écrire votre programme maintenant, consultez [écriture d’Applications MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a> Intranet et Internet

De nombreuses applications s’exécutent sur Internet et sont accessibles à toute personne disposant d’un navigateur et l’accès à Internet. Les entreprises mettent en place des intranets, qui sont des réseaux d’entreprise à l’aide de protocoles TCP/IP et les navigateurs Web. Intranets offrent une source centrale facilement extensible pour les informations de l’entreprise. Ils peuvent être utilisés pour la mise à niveau des logiciels pour la fourniture de rapports et, pour le support technique et pour obtenir des informations. Le tableau suivant compare les fonctionnalités d’Internet et intranet.

|Internet|Intranet|
|--------------|--------------|
|Faible bande passante|Bande passante élevée|
|Problèmes de sécurité des données et des systèmes|Contrôle d’accès aux données et systèmes|
|Contrôle de contenu minimal|Contrôle de contenu élevé|

##  <a name="_core_client_or_server_application"></a> Application cliente ou serveur

Votre application peut s’exécuter sur un ordinateur client ou sur un ordinateur serveur. Votre application peut également être stockée sur un serveur, puis téléchargée sur Internet et s’exécutent sur un ordinateur client. Pour télécharger les fichiers, les classes WinInet MFC sont utilisés pour les applications clientes. MFC et les classes de monikers asynchrones sont utilisés pour télécharger des fichiers et contrôler les propriétés. Classes de contrôles ActiveX et les documents actifs sont utilisées pour les applications clientes et pour les applications qui sont téléchargées à partir du serveur pour s’exécuter sur un client.

##  <a name="_core_the_web_page"></a> La Page Web : Contrôles ActiveX HTML, les Documents actifs,

Microsoft propose plusieurs manières de fournir un contenu sur une page Web. Pages Web peuvent utiliser standard HTML ou extensions, telles que la balise object, pour fournir du contenu dynamique tel que des contrôles ActiveX.

Navigateurs Web affichent généralement des pages HTML. Documents actifs peuvent également afficher des données de votre application dans l’interface pointer-cliquer simple d’un navigateur prenant en charge COM. Votre serveur de document actif peut afficher votre document plein cadre dans la zone client entière, avec ses propres menus et les barres d’outils.

Contrôles ActiveX que vous écrivez peuvent être téléchargés à partir du serveur de façon asynchrone et affichés sur une page Web. Vous pouvez utiliser un langage de script comme VBScript pour effectuer la validation côté client avant d’envoyer des informations sur le serveur.

##  <a name="_core_browser_or_standalone"></a> Navigateur ou une Application autonome

Vous pouvez écrire des contrôles ActiveX qui sont incorporés dans une page HTML et les serveurs de documents actifs qui sont affichés dans un navigateur. Vous pouvez écrire des pages HTML contenant un bouton pour envoyer une demande pour exécuter votre application ISAPI sur un serveur Web. Vous pouvez écrire une application autonome qui utilise des protocoles Internet pour télécharger des fichiers et afficher les informations à votre utilisateur, sans jamais à l’aide d’une application de navigateur.

##  <a name="_core_com_on_the_internet"></a> COM sur Internet

Contrôles ActiveX, les documents actifs et les monikers asynchrones utilisent les technologies COM (Component Object Model).

Contrôles ActiveX fournissent un contenu dynamique à des documents et des pages sur les sites Internet. Avec COM, vous pouvez créer des contrôles ActiveX et des documents plein écran à l’aide de documents actifs.

Monikers asynchrones fournissent des fonctionnalités pour permettre un contrôle s’exécuter correctement dans un environnement Internet, y compris un incrémentielle ou progressive signifie pour télécharger des données. Contrôles doivent également fonctionnent bien avec d’autres contrôles qui peuvent également récupérer leurs données de façon asynchrone en même temps.

##  <a name="_core_client_data_download_services"></a> Services de téléchargement de données client

Deux ensembles d’API qui vous aideront à transférer des données à votre client sont WinInet et des monikers asynchrones. Si vous avez .gif volumineux et les fichiers .avi et les contrôles ActiveX sur votre page HTML, vous pouvez augmenter la réactivité à l’utilisateur en téléchargeant en mode asynchrone, soit à l’aide de monikers asynchrones ou de façon asynchrone à l’aide de WinInet.

Une tâche courante sur Internet est transfert de données. Si vous utilisez déjà la technologie Active (par exemple, si vous avez un contrôle ActiveX), vous pouvez utiliser des monikers asynchrones pour restituer progressivement les données au cours du téléchargement. Vous pouvez utiliser WinInet pour transférer des données à l’aide des protocoles Internet courants tels que HTTP, FTP et gopher. Les deux méthodes fournissent l’indépendance de protocole et fournissent une couche abstraite à l’aide de WinSock et TCP/IP. Vous pouvez toujours utiliser [WinSock](../mfc/windows-sockets-in-mfc.md) directement.

Le tableau suivant résume plusieurs façons d’utiliser MFC pour transférer des données sur Internet.

|Utiliser ce protocole|Dans ces conditions|À l’aide de ces classes|
|-----------------------|----------------------------|-------------------------|
|[Internet téléchargement à l’aide de Monikers asynchrones](../mfc/asynchronous-monikers-on-the-internet.md)|Pour le transfert asynchrone à l’aide de COM, les contrôles ActiveX et n’importe quel protocole Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pour les protocoles Internet pour HTTP, FTP et gopher. Données peuvent être transférées de façon synchrone ou asynchrone et sont stockées dans un cache de l’échelle du système.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)et bien plus encore.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Pour une efficacité maximale et le contrôle. Nécessite la compréhension des protocoles TCP/IP et des sockets.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)

