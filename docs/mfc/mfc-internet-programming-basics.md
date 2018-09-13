---
title: Notions de programmation Internet MFC | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 980822792c3be4bc9c4de93baa20d4b3decb5af9
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535156"
---
# <a name="mfc-internet-programming-basics"></a>Éléments fondamentaux relatifs à la programmation Internet MFC

Microsoft fournit de nombreuses API pour la programmation d’applications clientes et serveur. Nombre de nouvelles applications sont écrites pour Internet, et en tant que les technologies, les fonctionnalités du navigateur et modification des options de sécurité, les nouveaux types d’applications seront écrit. Les navigateurs s’exécutent sur les ordinateurs clients, fournissant un accès à Internet et l’affichage des pages HTML contenant du texte, des graphiques, des contrôles ActiveX et des documents. Les serveurs fournissent FTP, HTTP, services et gopher et exécuter des applications d’extension de serveur à l’aide de CGI. Votre application personnalisée peut récupérer des informations et fournir des données sur Internet.  

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](activex-controls.md).
  
 ![Applications clientes et serveur](../mfc/media/vc38bq1.gif "vc38bq1")  
  
 MFC fournit des classes qui prennent en charge la programmation Internet. Vous pouvez utiliser [COleControl](../mfc/reference/colecontrol-class.md) et [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) et les classes MFC pour écrire des contrôles ActiveX et les documents actifs associées. Vous pouvez utiliser les classes MFC telles que [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md), et [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) pour récupérer des fichiers et des informations à l’aide des protocoles Internet tels que FTP, HTTP et gopher.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Classes MFC liées à Internet](../mfc/internet-related-mfc-classes.md)  
  
-   [Informations Internet par rubrique](../mfc/internet-information-by-topic.md)  
  
-   [Informations Internet par tâche](../mfc/internet-information-by-task.md)  
  
-   [Technologie active sur Internet](../mfc/active-technology-on-the-internet.md)  
  
-   [Notions de base de WinInet](../mfc/wininet-basics.md)  
  
-   [HTML - Notions de base](../mfc/html-basics.md)  
  
## <a name="related-sections"></a>Rubriques connexes  
  
-   [Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)  
  
-   [Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)  
  
-   [Choix en matière de conception d’applications](../mfc/application-design-choices.md)  
  
-   [Écriture d’applications MFC](../mfc/writing-mfc-applications.md)  
  
-   [Test des applications Internet](../mfc/testing-internet-applications.md)  
  
-   [Sécurité Internet](../mfc/internet-security-cpp.md)  
  
-   [Prise en charge d’ATL pour les contrôles DHTML](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> Sites Web pour plus d’informations  
 Pour plus d’informations sur la technologie Internet de Microsoft, consultez le [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) site Web. (Liens peuvent changer sans préavis.)  
  
 Ce site Web pour les développeurs contient des informations sur l’utilisation des outils de développement Microsoft et des technologies et des témoignages sur les conférences récents et à venir. À partir de cette page, vous pouvez passer à de nombreux sites connexes pour les développeurs, y compris .NET, les centres de développement XML. Vous pouvez également télécharger des exemples et kits de développement logiciel bêta.  
  
 Le [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125) publie des spécifications pour HTML, HTTP, CGI et autres technologies du World Wide Web.  
  
##  <a name="_core_more_internet_help"></a> Mieux à Internet  
 La section OLE du kit SDK Windows contient des informations supplémentaires sur la programmation OLE. Ces informations fournissent des détails sur l’utilisation des fonctions Win32 WinInet directement, plutôt que via les classes MFC. Il contient également des informations générales sur les technologies Internet.  
  
## <a name="see-also"></a>Voir aussi  



