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
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366286"
---
# <a name="mfc-internet-programming-basics"></a>Éléments fondamentaux relatifs à la programmation Internet MFC

Microsoft fournit de nombreuses API pour la programmation à la fois des applications client et serveur. De nombreuses nouvelles applications sont en cours d’écriture pour l’Internet, et que les technologies, les capacités du navigateur et les options de sécurité changent, de nouveaux types d’applications seront écrits. Les navigateurs s’exécutent sur les ordinateurs des clients, donnant accès au World Wide Web et affichant des pages HTML qui contiennent du texte, des graphiques, des contrôles ActiveX et des documents. Les serveurs fournissent des services FTP, HTTP et gopher, et exécutent des applications d’extension de serveur à l’aide de CGI. Votre application personnalisée peut récupérer des informations et fournir des données sur Internet.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations, voir [ActiveX Controls](activex-controls.md).

![Applications client et serveur](../mfc/media/vc38bq1.gif "Applications client et serveur")

MFC offre des cours qui prennent en charge la programmation Internet. Vous pouvez utiliser [COleControl](../mfc/reference/colecontrol-class.md) et [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) et les classes MFC connexes pour écrire des contrôles ActiveX et des documents actifs. Vous pouvez utiliser des classes MFC telles que [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md)et [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) pour récupérer des fichiers et des informations à l’aide de protocoles Internet tels que FTP, HTTP et gopher.

## <a name="in-this-section"></a>Dans cette section

- [Classes MFC liées à Internet](../mfc/internet-related-mfc-classes.md)

- [Informations sur Internet par sujet](../mfc/internet-information-by-topic.md)

- [Informations Internet par tâche](../mfc/internet-information-by-task.md)

- [Technologie active sur Internet](../mfc/active-technology-on-the-internet.md)

- [WinInet Basics](../mfc/wininet-basics.md)

- [HTML - Notions de base](../mfc/html-basics.md)

## <a name="related-sections"></a>Sections connexes

- [Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)

- [Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)

- [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)

- [Choix en matière de conception d’applications](../mfc/application-design-choices.md)

- [Écriture d’applications MFC](../mfc/writing-mfc-applications.md)

- [Test des applications Internet](../mfc/testing-internet-applications.md)

- [Sécurité Internet](../mfc/internet-security-cpp.md)

- [Prise en charge ATL pour les contrôles DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Sites Web pour plus d’informations

Pour plus d’informations sur la technologie Internet Microsoft, consultez le site Web du [Réseau des développeurs Microsoft (MSDN).](https://go.microsoft.com/fwlink/p/?linkid=56322) (Les liens peuvent changer sans préavis.)

Ce site Web pour les développeurs contient des informations sur l’utilisation d’outils et de technologies de développement Microsoft, et des histoires de haut niveau sur les conférences récentes et à venir. De cette page, vous pouvez sauter à de nombreux sites de développeurs connexes, y compris le .NET, et XML Developer Centers. Vous pouvez également télécharger des SDK bêta et des échantillons.

Le [World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) publie des spécifications pour HTML, HTTP, CGI et d’autres technologies World Wide Web.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Plus d’aide Internet

La section OLE du Windows SDK contient des informations supplémentaires sur la programmation OLE. Ces informations fournissent des détails sur l’utilisation des fonctions Win32 WinInet directement, plutôt que par le biais des classes MFC. Il contient également des informations d’aperçu sur les technologies Internet.
