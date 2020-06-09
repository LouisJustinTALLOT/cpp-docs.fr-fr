---
title: Menus et ressources (OLE)
ms.date: 11/04/2016
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
ms.openlocfilehash: e705f28476df7b594f9648aee8317759211c66c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626208"
---
# <a name="menus-and-resources-ole"></a>Menus et ressources (OLE)

Ce groupe d’articles explique l’utilisation des menus et des ressources dans les applications de document OLE MFC.

L’édition visuelle OLE impose des exigences supplémentaires dans le menu et d’autres ressources fournies par les applications de document OLE, car il existe un certain nombre de modes dans lesquels les applications de conteneur et de serveur (composant) peuvent être démarrées et utilisées. Par exemple, une application de serveur complet peut s’exécuter dans l’un de ces trois modes :

- Autonome.

- Sur place, pour la modification d’un élément dans le contexte d’un conteneur.

- Ouvre, pour la modification d’un élément en dehors du contexte de son conteneur, souvent dans une fenêtre séparée.

Cela nécessite trois dispositions de menu distinctes, une pour chaque mode possible de l’application. Les tables d’accélérateurs sont également nécessaires pour chaque nouveau mode. Une application conteneur peut ou non prendre en charge l’activation sur place ; Si c’est le cas, il a besoin d’une nouvelle structure de menu et de tables d’accélérateur associées.

L’activation sur place exige que le conteneur et les applications serveur négocient pour l’espace de menu, de barre d’outils et de barre d’État. Toutes les ressources doivent être conçues avec cela à l’esprit. Les [menus et les ressources](menus-and-resources-menu-merging.md) de l’article : la fusion de menus couvre ce sujet en détail.

En raison de ces problèmes, les applications de document OLE créées avec l’Assistant application peuvent avoir jusqu’à quatre ressources de table d’accélérateur et de menus distincts. Ils sont utilisés pour les raisons suivantes :

|Nom de la ressource|Utilisation|
|-------------------|---------|
|IDR_MAINFRAME|Utilisé dans une application MDI si aucun fichier n’est ouvert ou dans une application SDI, quels que soient les fichiers ouverts. Il s’agit du menu standard utilisé dans les applications non-OLE.|
|TYPE de IDR_ \<project>|Utilisé dans une application MDI si des fichiers sont ouverts. Utilisé lorsqu’une application s’exécute en mode autonome. Il s’agit du menu standard utilisé dans les applications non-OLE.|
|IDR_ \<project> TYPE_SRVR_IP|Utilisé par le serveur ou le conteneur lorsqu’un objet est ouvert sur place.|
|IDR_ \<project> TYPE_SRVR_EMB|Utilisé par une application serveur si un objet est ouvert sans utiliser l’activation sur place.|

Chacun de ces noms de ressources représente un menu et, généralement, une table d’accélérateurs. Un schéma similaire doit être utilisé dans les applications MFC qui ne sont pas créées avec l’Assistant Application.

Les articles suivants traitent des rubriques relatives aux conteneurs, aux serveurs et à la fusion de menus nécessaire pour implémenter l’activation sur place :

- [Menus et ressources : ajouts de conteneurs](menus-and-resources-container-additions.md)

- [Menus et ressources : ajouts de serveurs](menus-and-resources-server-additions.md)

- [Menus et ressource : fusion de menus](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Voir aussi

[OLE](ole-in-mfc.md)
