---
title: Base de programmation Internet MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6896daddc0eb900f9e2a29497eb2dd8a1dc78446
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255607"
---
# <a name="mfc-internet-programming-basics"></a>Éléments fondamentaux relatifs à la programmation Internet MFC
Microsoft fournit plusieurs API pour la programmation d’applications clientes et serveur. Nombre de nouvelles applications sont écrites pour Internet et technologies, fonctionnalités de navigateur et modification des options de sécurité, les nouveaux types d’applications seront écrit. Les navigateurs s’exécutent sur les ordinateurs clients, en fournissant l’accès à Internet et l’affichage des pages HTML qui contiennent du texte, des graphiques, des contrôles ActiveX et des documents. Serveurs fournissent des services gopher, HTTP et FTP et exécutent des applications d’extension de serveur à l’aide de CGI. Votre application personnalisée peut récupérer des informations et fournir des données sur Internet.  
  
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
  
-   [Documents actifs sur Internet](../mfc/active-documents-on-the-internet.md)  
  
-   [Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)  
  
-   [Choix en matière de conception d’applications](../mfc/application-design-choices.md)  
  
-   [Écriture d’applications MFC](../mfc/writing-mfc-applications.md)  
  
-   [Test des applications Internet](../mfc/testing-internet-applications.md)  
  
-   [Sécurité Internet](../mfc/internet-security-cpp.md)  
  
-   [Prise en charge d’ATL pour les contrôles DHTML](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> Pour plus d’informations, les Sites Web  
 Pour plus d’informations sur les technologies Microsoft Internet, consultez le [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) site Web. (Liens peuvent changer sans préavis.)  
  
 Ce site Web pour les développeurs contient des informations sur l’utilisation des outils de développement Microsoft et les technologies et les récits supérieur sur conférences récentes et à venir. À partir de cette page, vous pouvez accéder à de nombreux sites de développeurs connexes, y compris .NET, les centres de développement XML. Vous pouvez également télécharger des kits de développement logiciel bêta et des exemples.  
  
 Le [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125) publie des spécifications pour HTML, HTTP, CGI et autres technologies World Wide Web.  
  
##  <a name="_core_more_internet_help"></a> Plus d’aide d’Internet  
 La section OLE du Kit de développement Windows contient des informations supplémentaires sur la programmation OLE. Cette information fournit des détails sur l’utilisation des fonctions Win32 WinInet directement, plutôt que via les classes MFC. Il contient également des informations générales sur les technologies Internet.  
  
## <a name="see-also"></a>Voir aussi  



