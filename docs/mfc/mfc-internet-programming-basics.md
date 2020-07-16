---
title: Éléments fondamentaux relatifs à la programmation Internet MFC
ms.date: 11/19/2018
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
ms.openlocfilehash: c9825cdcb5cb0963a4e0d3acdeb36dfee54b70fc
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405024"
---
# <a name="mfc-internet-programming-basics"></a>Éléments fondamentaux relatifs à la programmation Internet MFC

Microsoft fournit de nombreuses API pour la programmation d’applications client et serveur. De nombreuses nouvelles applications sont écrites pour Internet, et à mesure que les technologies, les fonctionnalités du navigateur et les options de sécurité changent, de nouveaux types d’applications sont écrits. Les navigateurs s’exécutent sur les ordinateurs clients, en fournissant un accès à la World Wide Web et en affichant des pages HTML qui contiennent du texte, des graphiques, des contrôles ActiveX et des documents. Les serveurs fournissent des services FTP, HTTP et Gopher, et exécutent des applications d’extension serveur à l’aide de CGI. Votre application personnalisée peut récupérer des informations et fournir des données sur Internet.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](activex-controls.md).

![Applications client et serveur](../mfc/media/vc38bq1.gif "Applications client et serveur")

MFC fournit des classes qui prennent en charge la programmation Internet. Vous pouvez utiliser [COleControl](reference/colecontrol-class.md) et [CDocObjectServer](reference/cdocobjectserver-class.md) et les classes MFC associées pour écrire des contrôles ActiveX et des documents actifs. Vous pouvez utiliser des classes MFC telles que [CInternetSession](reference/cinternetsession-class.md), [CFtpConnection](reference/cftpconnection-class.md)et [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) pour récupérer des fichiers et des informations à l’aide de protocoles Internet tels que FTP, http et Gopher.

## <a name="in-this-section"></a>Dans cette section

- [Classes MFC liées à Internet](internet-related-mfc-classes.md)

- [Informations Internet par rubrique](internet-information-by-topic.md)

- [Informations Internet par tâche](internet-information-by-task.md)

- [Technologie active sur Internet](active-technology-on-the-internet.md)

- [Concepts de base de WinInet](wininet-basics.md)

- [HTML - Notions de base](html-basics.md)

## <a name="related-sections"></a>Sections connexes

- [Contrôles ActiveX sur Internet](activex-controls-on-the-internet.md)

- [Monikers asynchrones sur Internet](asynchronous-monikers-on-the-internet.md)

- [Extension Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)

- [Tâches de programmation Internet MFC](mfc-internet-programming-tasks.md)

- [Choix en matière de conception d’applications](application-design-choices.md)

- [Écriture d’applications MFC](writing-mfc-applications.md)

- [Test des applications Internet](testing-internet-applications.md)

- [Sécurité Internet](internet-security-cpp.md)

- [Prise en charge ATL pour les contrôles DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="websites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Sites Web pour plus d’informations

Pour plus d’informations sur la technologie Microsoft Internet, consultez [Microsoft docs](https://docs.microsoft.com/).

Le [World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) publie des spécifications pour html, http, CGI et d’autres technologies World Wide Web.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Aide supplémentaire sur Internet

La section OLE de l’SDK Windows contient des informations supplémentaires sur la programmation OLE. Ces informations fournissent des détails sur l’utilisation directe des fonctions WinInet Win32, plutôt que par le biais des classes MFC. Elle contient également des informations générales sur les technologies Internet.
