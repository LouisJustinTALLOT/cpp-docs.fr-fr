---
title: Serveurs de documents actifs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc207541bda3084db6bc8ab3896f46761587169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340162"
---
# <a name="active-document-servers"></a>Serveurs de documents actifs
Les serveurs de documents actifs tels que les documents Word, Excel ou PowerPoint hébergent les documents d'autres types d'application appelés documents actifs. Contrairement aux objets incorporés OLE (qui sont simplement affichés dans la page d'un autre document), les documents actifs fournissent l'interface complète et complètent des fonctionnalités natives de l'application serveur qui les crée. Les utilisateurs peuvent créer des documents en utilisant la pleine puissance de leurs applications favorites (s'ils ont activé les documents actifs), mais peuvent traiter le projet résultant comme une entité unique.  
  
 Les documents actifs peuvent avoir plusieurs pages et sont toujours actifs sur place. Documents actifs contrôlent une partie de l’interface utilisateur, fusionnant leurs menus avec les **fichier** et **aide** menus du conteneur. Ils occupent la zone de modification entière du conteneur et contrôlent les vues et la mise en page d'imprimante (marges, pieds de page, etc.).  
  
 MFC implémente des serveurs de documents actifs avec les interfaces de document/vue, les tables de dispatch de commandes, l'impression, la gestion des menus et la gestion du Registre. Les exigences de programmation spécifiques sont décrites dans [documents actifs](../mfc/active-documents.md).  
  
 MFC prend en charge les documents actifs avec la [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) classe, dérivée de [CCmdTarget](../mfc/reference/ccmdtarget-class.md), et [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md), dérivée de [ COleServerItem](../mfc/reference/coleserveritem-class.md). MFC prend en charge les conteneurs de documents actifs avec la [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) classe, dérivée de [COleClientItem](../mfc/reference/coleclientitem-class.md).  
  
 `CDocObjectServer` mappe les interfaces de document actif et initialise et active un document actif. MFC fournit également des macros pour gérer le routage des commandes des documents actifs. Pour utiliser des documents actifs dans votre application, incluez AfxDocOb.h dans votre fichier StdAfx.h.  
  
 Un serveur MFC normal installe sa propre classe dérivée `COleServerItem`. L’Assistant Application MFC génère cette classe pour vous si vous sélectionnez le **mini-serveur** ou **serveur complet** case à cocher pour permettre à votre serveur d’applications de prise en charge des documents composés. Si vous sélectionnez également le **serveur de documents actifs** case à cocher, l’Assistant Application MFC génère une classe dérivée de `CDocObjectServerItem` à la place.  
  
 La classe `COleDocObjectItem` permet à un conteneur OLE de devenir un conteneur de documents actifs. Vous pouvez utiliser l’Assistant Application MFC pour créer un conteneur de documents actifs en sélectionnant le **conteneur de documents actifs** case à cocher dans la page de prise en charge des documents composés de l’Assistant Application MFC. Pour plus d’informations, consultez [création d’une Application conteneur de documents actifs](../mfc/creating-an-active-document-container-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Documents actifs (contenance)](../mfc/active-document-containment.md)

