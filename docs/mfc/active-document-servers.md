---
title: Serveurs de documents actifs
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 58f2a63a8c640e6ae31640af680894763603e1d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619137"
---
# <a name="active-document-servers"></a>Serveurs de documents actifs

Les serveurs de documents actifs tels que les documents Word, Excel ou PowerPoint hébergent les documents d'autres types d'application appelés documents actifs. Contrairement aux objets incorporés OLE (qui sont simplement affichés dans la page d'un autre document), les documents actifs fournissent l'interface complète et complètent des fonctionnalités natives de l'application serveur qui les crée. Les utilisateurs peuvent créer des documents en utilisant la pleine puissance de leurs applications favorites (s'ils ont activé les documents actifs), mais peuvent traiter le projet résultant comme une entité unique.

Les documents actifs peuvent avoir plusieurs pages et sont toujours actifs sur place. Les documents actifs contrôlent une partie de l’interface utilisateur, en fusionnant leurs menus avec les menus **fichier** et **aide** du conteneur. Ils occupent la zone de modification entière du conteneur et contrôlent les vues et la mise en page d'imprimante (marges, pieds de page, etc.).

MFC implémente des serveurs de documents actifs avec les interfaces de document/vue, les tables de dispatch de commandes, l'impression, la gestion des menus et la gestion du Registre. Des exigences spécifiques en matière de programmation sont décrites dans [documents actifs](active-documents.md).

MFC prend en charge les documents actifs avec la classe [CDocObjectServer](reference/cdocobjectserver-class.md) , dérivée de [CCmdTarget](reference/ccmdtarget-class.md)et [CDocObjectServerItem](reference/cdocobjectserveritem-class.md), dérivée de [COleServerItem](reference/coleserveritem-class.md). MFC prend en charge les conteneurs de documents actifs avec la classe [COleDocObjectItem](reference/coledocobjectitem-class.md) , dérivée de [COleClientItem](reference/coleclientitem-class.md).

`CDocObjectServer` mappe les interfaces de document actif et initialise et active un document actif. MFC fournit également des macros pour gérer le routage des commandes des documents actifs. Pour utiliser des documents actifs dans votre application, incluez AfxDocOb.h dans votre fichier StdAfx.h.

Un serveur MFC normal installe sa propre classe dérivée `COleServerItem`. L’Assistant Application MFC génère cette classe pour vous si vous activez la case à cocher **mini-serveur** ou **serveur complet** pour permettre la prise en charge des documents composés de votre serveur d’applications. Si vous activez également la case à cocher **serveur de documents actifs** , l’Assistant Application MFC génère une classe dérivée de à la `CDocObjectServerItem` place.

La classe `COleDocObjectItem` permet à un conteneur OLE de devenir un conteneur de documents actifs. Vous pouvez utiliser l’Assistant Application MFC pour créer un conteneur de documents actifs en activant la case à cocher **conteneur de documents actifs** dans la page prise en charge des documents composés de l’Assistant Application MFC. Pour plus d’informations, consultez [création d’une application de conteneur de documents actifs](creating-an-active-document-container-application.md).

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](active-document-containment.md)
