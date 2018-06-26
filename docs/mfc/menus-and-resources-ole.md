---
title: Menus et ressources (OLE) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cae180ca71b89732e073b9039483b8b46366a42a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929632"
---
# <a name="menus-and-resources-ole"></a>Menus et ressources (OLE)
Ce groupe d’articles explique l’utilisation des menus et des ressources dans les applications de document OLE MFC.  
  
 Édition visuelle OLE impose des exigences supplémentaires dans le menu et autres ressources fournies par les applications de document OLE, car il existe un nombre de modes de conteneur dans lequel les deux et les applications serveur (composant) peuvent être démarrées et utilisées. Par exemple, une application de serveur complet peut s’exécuter dans un des trois modes suivants :  
  
-   En mode autonome.  
  
-   En place, pour modifier un élément dans le contexte d’un conteneur.  
  
-   Ouvert pour modification d’un élément en dehors du contexte de son conteneur, souvent dans une fenêtre distincte.  
  
 Cela nécessite trois dispositions de menus séparées, une pour chaque mode possible de l’application. Tables d’accélérateurs sont également nécessaires pour chaque nouveau mode. Une application conteneur peut ou ne peut pas prendre en charge l’activation sur place ; Dans ce cas, il a besoin d’une nouvelle structure de menu et associées des tables d’accélérateurs.  
  
 L’activation sur place nécessite que les applications conteneur et serveur doivent négocier pour l’espace de barre de menu, barre d’outils et l’état. Toutes les ressources doivent être conçues avec cela à l’esprit. L’article [Menus et ressources : fusion de menus](../mfc/menus-and-resources-menu-merging.md) aborde ce sujet en détail.  
  
 En raison de ces problèmes, les applications de document OLE créées avec l’Assistant application peuvent avoir jusqu'à quatre de menus et ressources de la table d’accélérateurs. Ceux-ci sont utilisés pour les raisons suivantes :  
  
|Nom de la ressource|Utilisez|  
|-------------------|---------|  
|IDR_MAINFRAME|Utilisé dans une application MDI si aucun fichier n’est ouverte, ou dans une application SDI, quelle que soit les fichiers ouverts. Il s’agit du menu standard utilisé dans les applications non-OLE.|  
|IDR_\<projet > TYPE|Utilisé dans une application MDI si les fichiers sont ouverts. Utilisé lors de l’exécution d’une application autonome. Il s’agit du menu standard utilisé dans les applications non-OLE.|  
|IDR_\<projet > TYPE_SRVR_IP|Utilisé par le serveur ou le conteneur lorsqu’un objet est ouvert en place.|  
|IDR_\<projet > TYPE_SRVR_EMB|Utilisé par une application serveur si un objet est ouvert sans utiliser l’activation sur place.|  
  
 Chacun de ces noms de ressource représente un menu et, en règle générale, une table d’accélérateurs. Un modèle similaire doit être utilisé dans les applications MFC qui ne sont pas créées avec l’Assistant application.  
  
 Les articles suivants traitent des conteneurs, les serveurs et la fusion de menus nécessaires pour implémenter l’activation sur place :  
  
-   [Menus et ressources : ajouts de conteneurs](../mfc/menus-and-resources-container-additions.md)  
  
-   [Menus et ressources : ajouts de serveurs](../mfc/menus-and-resources-server-additions.md)  
  
-   [Menus et ressource : fusion de menus](../mfc/menus-and-resources-menu-merging.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLE](../mfc/ole-in-mfc.md)

