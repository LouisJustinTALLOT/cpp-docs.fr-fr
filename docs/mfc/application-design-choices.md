---
title: Choix de conception d’application | Documents Microsoft
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
ms.openlocfilehash: 76a49d2ecfc79e35da55d1393cf3880b15fba7d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347758"
---
# <a name="application-design-choices"></a>Choix en matière de conception d'applications
Cet article décrit certains des problèmes de conception à prendre en compte lors de la programmation pour Internet.  
  
 Les rubriques abordées dans cet article sont les suivantes :  
  
-   [Intranet et Internet](#_core_intranet_versus_internet)  
  
-   [Application cliente ou serveur](#_core_client_or_server_application)  
  
-   [](#_core_the_web_page)  
  
-   [Navigateur ou Application autonome](#_core_browser_or_standalone)  
  
-   [COM sur Internet](#_core_com_on_the_internet)  
  
-   [Services de téléchargement de données client](#_core_client_data_download_services)  
  
 Si vous êtes prêt à commencer à écrire votre programme maintenant, consultez [écriture d’Applications MFC](../mfc/writing-mfc-applications.md).  
  
##  <a name="_core_intranet_versus_internet"></a> Intranet et Internet  
 De nombreuses applications s’exécutent sur Internet et sont accessibles à toute personne disposant d’un navigateur et l’accès à Internet. Les entreprises mettent en place des intranets, qui sont des réseaux d’entreprise à l’aide des protocoles TCP/IP et les navigateurs Web. Intranets offrent une source de mise à niveau aisée et centrale pour les informations de l’entreprise. Ils peuvent être utilisés pour la mise à niveau logicielles, pour la fourniture de rapports et, pour le support technique et pour obtenir des informations. Le tableau suivant compare les fonctionnalités d’Internet et intranet.  
  
|Internet|Intranet|  
|--------------|--------------|  
|Faible bande passante|Bande passante élevée|  
|Sécurité réduite de données et systèmes|Accès contrôlé aux données et les systèmes|  
|Contrôle de contenu minimal|Contrôle de contenu élevé|  
  
##  <a name="_core_client_or_server_application"></a> Application cliente ou serveur  
 Votre application peut s’exécuter sur un ordinateur client ou sur un serveur. Votre application peut également être stockée sur un serveur et puis téléchargée sur Internet et exécutez sur un ordinateur client. Classes WinInet MFC sont utilisées pour les applications clientes pour télécharger les fichiers. MFC et les classes de monikers asynchrones sont utilisés pour télécharger les fichiers et les propriétés du contrôle. Classes de contrôles ActiveX et les documents actifs sont utilisées pour les applications clientes et les applications qui sont téléchargées à partir du serveur pour s’exécuter sur un client.  
  
##  <a name="_core_the_web_page"></a> La Page Web : Contrôles ActiveX HTML, les Documents actifs,  
 Microsoft propose plusieurs manières de fournir un contenu sur une page Web. Pages Web peuvent utiliser standard HTML ou extensions, telles que la balise object, pour fournir du contenu dynamique tel que des contrôles ActiveX.  
  
 Navigateurs Web affichent généralement des pages HTML. Documents actifs peuvent également afficher des données de votre application dans l’interface pointer-cliquer simple d’un navigateur compatible COM. Votre serveur de documents actifs peut afficher votre document plein cadre dans la zone cliente dans son intégralité, avec ses propres menus et les barres d’outils.  
  
 Vous écrivez des contrôles ActiveX peuvent être téléchargés de façon asynchrone à partir du serveur et affichées sur une page Web. Vous pouvez utiliser un langage de script tel que VBScript pour effectuer la validation côté client avant d’envoyer des informations sur le serveur.  
  
##  <a name="_core_browser_or_standalone"></a> Navigateur ou Application autonome  
 Vous pouvez écrire des contrôles ActiveX qui sont incorporés dans une page HTML et les serveurs de documents actifs qui sont affichés dans un navigateur. Vous pouvez écrire des pages HTML contenant un bouton pour envoyer une demande pour exécuter votre application ISAPI sur un serveur Web. Vous pouvez écrire une application autonome qui utilise des protocoles Internet pour télécharger des fichiers et afficher les informations pour les utilisateurs, sans passer par une application de navigateur.  
  
##  <a name="_core_com_on_the_internet"></a> COM sur Internet  
 Contrôles ActiveX, les documents actifs et les monikers asynchrones utilisent les technologies COM (Component Object Model).  
  
 Contrôles ActiveX fournissent un contenu dynamique aux documents et pages sur des sites Internet. Avec COM, vous pouvez créer des contrôles ActiveX et des documents plein écran à l’aide de documents actifs.  
  
 Les monikers asynchrones fournissent des fonctionnalités permettant d’activer un contrôle de s’exécuter correctement dans un environnement Internet, y compris un incrémentielle ou progressive signifie pour télécharger des données. Contrôles doivent également fonctionnent correctement avec les autres contrôles qui peuvent également récupérer des leurs données de façon asynchrone en même temps.  
  
##  <a name="_core_client_data_download_services"></a> Services de téléchargement de données client  
 Deux ensembles d’API permettant de transférer des données vers votre client sont WinInet et les monikers asynchrones. Si vous avez .gif volumineux et des fichiers .avi et des contrôles ActiveX sur votre page HTML, vous pouvez augmenter le temps de réponse à l’utilisateur en téléchargeant en mode asynchrone, par l’utilisation de monikers asynchrones ou à l’aide WinInet de façon asynchrone.  
  
 Une tâche courante sur Internet est transfert de données. Si vous utilisez déjà la technologie Active (par exemple, si vous avez un contrôle ActiveX), vous pouvez utiliser des monikers asynchrones pour restituer progressivement les données au cours du téléchargement. Vous pouvez utiliser WinInet pour transférer des données à l’aide des protocoles Internet courants tels que HTTP, FTP et gopher. Les deux méthodes fournissent l’indépendance du protocole et fournissent une couche d’abstraction pour à l’aide de WinSock et TCP/IP. Vous pouvez toujours utiliser [WinSock](../mfc/windows-sockets-in-mfc.md) directement.  
  
 Le tableau suivant résume les façons de l’utilisation de MFC pour transférer des données sur Internet.  
  
|Utilisez ce protocole|Dans ces conditions.|À l’aide de ces classes.|  
|-----------------------|----------------------------|-------------------------|  
|[Internet téléchargement à l’aide de Monikers asynchrones](../mfc/asynchronous-monikers-on-the-internet.md)|Pour le transfert asynchrone à l’aide de COM, les contrôles ActiveX et n’importe quel protocole Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Pour les protocoles Internet pour HTTP, FTP et gopher. Données peuvent être transférées de façon synchrone ou asynchrone et sont stockées dans un cache à l’échelle du système.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)et bien plus encore.|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Pour une efficacité maximale et le contrôle. Nécessite la compréhension de sockets et les protocoles TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Base de programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)

