---
title: Choix en matière de conception d'applications
ms.date: 09/12/2019
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
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374630"
---
# <a name="application-design-choices"></a>Choix en matière de conception d'applications

Cet article traite de certaines des questions de conception à considérer lors de la programmation pour l’Internet.

Les sujets abordés dans cet article sont les suivants :

- [Intranet contre Internet](#_core_intranet_versus_internet)

- [Application client ou serveur](#_core_client_or_server_application)

- [La page Web](#_core_the_web_page)

- [Navigateur ou application autonome](#_core_browser_or_standalone)

- [COM sur Internet](#_core_com_on_the_internet)

- [Services de téléchargement de données des clients](#_core_client_data_download_services)

Si vous êtes prêt à commencer à écrire votre programme dès maintenant, voir [Écrire des applications MFC](../mfc/writing-mfc-applications.md).

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>Intranet contre Internet

De nombreuses applications s’exécutent sur Internet et sont accessibles à toute personne ayant un navigateur et un accès Internet. Les entreprises mettent également en œuvre des intranets, qui sont des réseaux à l’échelle de l’entreprise utilisant des protocoles TCP/IP et des navigateurs Web. Intranets offre une source centrale facilement accessible à niveau pour les informations à l’échelle de l’entreprise. Ils peuvent être utilisés pour la mise à niveau des logiciels, pour la livraison et la compilation des enquêtes, pour le soutien à la clientèle, et pour la diffusion de l’information. Le tableau suivant compare les fonctionnalités d’Internet et d’intranets.

|Internet|Intranet|
|--------------|--------------|
|Bande passante faible|Bande passante élevée|
|Sécurité réduite des données et des systèmes|Accès contrôlé aux données et aux systèmes|
|Contrôle minimal du contenu|Contrôle élevé du contenu|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>Application client ou serveur

Votre application peut s’exécuter sur un ordinateur client ou sur un ordinateur serveur. Votre application peut également être stockée sur un serveur, puis téléchargée sur Internet et exécutée sur un ordinateur client. Les cours MFC WinInet sont utilisés pour les applications client pour télécharger des fichiers. Les classes de MFC et de moniker asynchrone sont utilisées pour télécharger des fichiers et contrôler les propriétés. Les classes pour les contrôles ActiveX et les documents actifs sont utilisées pour les applications client et pour les applications qui sont téléchargées à partir du serveur pour s’exécuter sur un client.

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>La page Web : HTML, Documents actifs, contrôles ActiveX

Microsoft offre plusieurs façons de fournir du contenu sur une page Web. Les pages Web peuvent utiliser des extensions HTML ou HTML standard, telles que l’étiquette d’objet, pour fournir du contenu dynamique tel que les contrôles ActiveX.

Les navigateurs Web affichent généralement des pages HTML. Les documents actifs peuvent également afficher les données de votre application dans l’interface simple point-and-click d’un navigateur compatible COM. Votre serveur de documents actifs peut afficher votre document, plein cadre dans l’ensemble du client, avec ses propres menus et barres d’outils.

Les contrôles ActiveX que vous écrivez peuvent être téléchargés asynchronement à partir du serveur et affichés sur une page Web. Vous pouvez utiliser un langage de script tel que VBScript pour effectuer la validation côté client avant d’envoyer des informations au serveur.

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>Navigateur ou application autonome

Vous pouvez écrire des contrôles ActiveX qui sont intégrés dans une page HTML et des serveurs de documents actifs qui sont consultés dans un navigateur. Vous pouvez écrire des pages HTML qui contiennent un bouton pour soumettre une demande d’exécution de votre application ISAPI sur un serveur Web. Vous pouvez écrire une application autonome qui utilise des protocoles Internet pour télécharger des fichiers et afficher les informations à votre utilisateur, sans jamais utiliser une application de navigateur.

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>COM sur Internet

Les contrôles ActiveX, les documents actifs et les surnoms asynchrones utilisent tous les technologies COM (Component Object Model).

Les contrôles ActiveX fournissent du contenu dynamique aux documents et aux pages sur les sites Internet. Avec COM, vous pouvez créer des contrôles ActiveX et des documents à cadre complet à l’aide de documents Active.

Les surnoms asynchrones fournissent des fonctionnalités pour permettre à un contrôle de bien fonctionner dans un environnement Internet, y compris un moyen progressif ou progressif de télécharger des données. Les contrôles doivent également bien fonctionner avec d’autres contrôles qui peuvent également être récupérer leurs données asynchronement en même temps.

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>Services de téléchargement de données des clients

Deux ensembles d’API qui aideront à transférer des données à votre client sont WinInet et surnoms asynchrones. Si vous avez de grands fichiers .gif et .avi et des contrôles ActiveX sur votre page HTML, vous pouvez augmenter la réactivité à l’utilisateur en téléchargeant asynchronement, soit en utilisant des surnoms asynchrones ou en utilisant WinInet asynchrone.

Une tâche commune sur Internet est le transfert de données. Si vous utilisez déjà la technologie Active (par exemple, si vous avez un contrôle ActiveX), vous pouvez utiliser des surnoms asynchrones pour rendre progressivement les données au fur et à mesure qu’elles sont téléchargées. Vous pouvez utiliser WinInet pour transférer des données à l’aide de protocoles Internet courants comme HTTP, FTP et gopher. Les deux méthodes fournissent l’indépendance du protocole, et fournissent une couche abstraite à l’utilisation de WinSock et TCP/IP. Vous pouvez toujours utiliser [WinSock](../mfc/windows-sockets-in-mfc.md) directement.

Le tableau suivant résume plusieurs façons d’utiliser MFC pour transférer des données sur Internet.

|Utiliser ce protocole|Dans ces conditions|Utilisation de ces classes|
|-----------------------|----------------------------|-------------------------|
|[Téléchargement sur Internet à l’aide de monikers asynchrones](../mfc/asynchronous-monikers-on-the-internet.md)|Pour le transfert asynchrone à l’aide de COM, de contrôles ActiveX et de tout protocole Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pour les protocoles Internet pour HTTP, FTP et gopher. Les données peuvent être transférées de manière synchrone ou asynchrone et stockées dans un cache à l’échelle du système.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md), et bien d’autres.|
|[Winsock](../mfc/windows-sockets-in-mfc.md)|Pour un maximum d’efficacité et de contrôle. Nécessite une compréhension des prises et des protocoles TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC Internet Programming Basics](../mfc/mfc-internet-programming-basics.md)<br/>
[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)
