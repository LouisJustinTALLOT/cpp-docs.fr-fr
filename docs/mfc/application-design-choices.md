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
ms.openlocfilehash: b205599ed3bf33e84516120b1855482797b86c9b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924918"
---
# <a name="application-design-choices"></a>Choix en matière de conception d'applications

Cet article présente certains des problèmes de conception à prendre en compte lors de la programmation pour Internet.

Les sujets abordés dans cet article sont les suivants :

- [Intranet et Internet](#_core_intranet_versus_internet)

- [Application cliente ou serveur](#_core_client_or_server_application)

- [Page Web](#_core_the_web_page)

- [Navigateur ou application autonome](#_core_browser_or_standalone)

- [COM sur Internet](#_core_com_on_the_internet)

- [Services de téléchargement de données client](#_core_client_data_download_services)

Si vous êtes prêt à commencer à écrire votre programme maintenant, consultez [écriture d’applications MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a>Intranet et Internet

De nombreuses applications s’exécutent sur Internet et sont accessibles à toute personne disposant d’un navigateur et d’un accès à Internet. Les entreprises implémentent également des intranets, qui sont des réseaux à l’ensemble de l’entreprise utilisant des protocoles TCP/IP et des navigateurs Web. Les intranets offrent une source centrale et facile à mettre à niveau pour les informations de l’entreprise. Ils peuvent être utilisés pour la mise à niveau de logiciels, pour la remise et le classement des enquêtes, le support technique et la livraison d’informations. Le tableau suivant compare les fonctionnalités d’Internet et des intranets.

|Internet|Intranet|
|--------------|--------------|
|Faible bande passante|Bande passante élevée|
|Sécurité réduite des données et systèmes|Accès contrôlé aux données et aux systèmes|
|Contrôle minimal du contenu|Contrôle élevé du contenu|

##  <a name="_core_client_or_server_application"></a>Application cliente ou serveur

Votre application peut s’exécuter sur un ordinateur client ou sur un serveur. Votre application peut également être stockée sur un serveur, puis téléchargée sur Internet et exécutée sur un ordinateur client. Les classes WinInet MFC sont utilisées pour permettre aux applications clientes de télécharger des fichiers. Les classes de moniker MFC et asynchrones sont utilisées pour télécharger des fichiers et des propriétés de contrôle. Les classes pour les contrôles ActiveX et les documents actifs sont utilisées pour les applications clientes et pour les applications qui sont téléchargées à partir du serveur pour s’exécuter sur un client.

##  <a name="_core_the_web_page"></a>Page Web : HTML, documents actifs, contrôles ActiveX

Microsoft offre plusieurs moyens de fournir du contenu sur une page Web. Les pages Web peuvent utiliser des extensions HTML ou HTML standard, telles que la balise Object, pour fournir du contenu dynamique tel que des contrôles ActiveX.

Les navigateurs Web affichent généralement des pages HTML. Les documents actifs peuvent également afficher les données de votre application dans l’interface simple pointer-cliquer d’un navigateur prenant en charge COM. Votre serveur de documents actifs peut afficher votre document, en plein cadre dans la zone cliente entière, avec ses propres menus et barres d’outils.

Les contrôles ActiveX que vous écrivez peuvent être téléchargés de manière asynchrone à partir du serveur et affichés sur une page Web. Vous pouvez utiliser un langage de script tel que VBScript pour effectuer une validation côté client avant d’envoyer des informations au serveur.

##  <a name="_core_browser_or_standalone"></a>Navigateur ou application autonome

Vous pouvez écrire des contrôles ActiveX incorporés dans une page HTML et des serveurs de documents actifs qui sont affichés dans un navigateur. Vous pouvez écrire des pages HTML qui contiennent un bouton pour envoyer une demande d’exécution de votre application ISAPI sur un serveur Web. Vous pouvez écrire une application autonome qui utilise des protocoles Internet pour télécharger des fichiers et afficher les informations à l’utilisateur, sans jamais utiliser une application de navigateur.

##  <a name="_core_com_on_the_internet"></a>COM sur Internet

Les contrôles ActiveX, les documents actifs et les monikers asynchrones utilisent tous des technologies COM (Component Object Model).

Les contrôles ActiveX fournissent du contenu dynamique à des documents et des pages sur des sites Internet. Avec COM, vous pouvez créer des contrôles ActiveX et des documents de frame complet à l’aide de documents actifs.

Les monikers asynchrones fournissent des fonctionnalités qui permettent à un contrôle de fonctionner correctement dans un environnement Internet, notamment un moyen incrémentiel ou progressif de télécharger des données. Les contrôles doivent également fonctionner correctement avec d’autres contrôles qui peuvent également récupérer leurs données de manière asynchrone en même temps.

##  <a name="_core_client_data_download_services"></a>Services de téléchargement de données client

Les deux ensembles d’API qui vous aideront à transférer des données à votre client sont WinInet et les monikers asynchrones. Si vous avez des fichiers. gif et. avi volumineux et des contrôles ActiveX sur votre page HTML, vous pouvez augmenter la réactivité de l’utilisateur en le téléchargeant de manière asynchrone, soit en utilisant des monikers asynchrones, soit en utilisant WinInet de manière asynchrone.

Une tâche courante sur Internet consiste à transférer des données. Si vous utilisez déjà la technologie active (par exemple, si vous avez un contrôle ActiveX), vous pouvez utiliser des monikers asynchrones pour restituer progressivement les données au fur et à mesure de leur téléchargement. Vous pouvez utiliser WinInet pour transférer des données à l’aide de protocoles Internet courants tels que HTTP, FTP et Gopher. Les deux méthodes fournissent l’indépendance du protocole et fournissent une couche abstraite pour l’utilisation de WinSock et TCP/IP. Vous pouvez toujours utiliser [Winsock](../mfc/windows-sockets-in-mfc.md) directement.

Le tableau suivant résume plusieurs façons d’utiliser MFC pour transférer des données sur Internet.

|Utiliser ce protocole|Dans ces conditions|Utilisation de ces classes|
|-----------------------|----------------------------|-------------------------|
|[Téléchargement Internet à l’aide de monikers asynchrones](../mfc/asynchronous-monikers-on-the-internet.md)|Pour le transfert asynchrone à l’aide de COM, les contrôles ActiveX et tout protocole Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pour les protocoles Internet pour HTTP, FTP et Gopher. Les données peuvent être transférées de façon synchrone ou asynchrone et sont stockées dans un cache à l’ensemble du système.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)et bien plus encore.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Pour optimiser l’efficacité et le contrôle. Nécessite une compréhension des sockets et des protocoles TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Voir aussi

[Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)
