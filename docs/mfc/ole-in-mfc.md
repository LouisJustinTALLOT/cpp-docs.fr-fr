---
title: OLE dans MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef23f0b7e031c6866b7792bca61c5e4d5bd470da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353626"
---
# <a name="ole-in-mfc"></a>Intégration du format OLE au format MFC
Ces articles expliquent les principes fondamentaux de la programmation OLE à l’aide de MFC. MFC fournit le moyen le plus simple pour écrire des programmes qui utilisent OLE :  
  
-   Pour utiliser OLE visual Édition (activation en place).  
  
-   En tant que conteneurs OLE ou serveurs.  
  
-   Pour implémenter la fonctionnalité de glisser-déplacer.  
  
-   Pour utiliser les données de date et d’heure.  
  
-   Pour gérer les données d’état de MFC modules, y compris exportés des points d’entrée DLL (fonction), les points d’entrée interface OLE/COM et les points d’entrée de procédure de fenêtre.  
  
 Vous pouvez également utiliser [Automation](../mfc/automation.md).  
  
> [!NOTE]
>  Le terme QU'OLE indique les technologies associées à la liaison et incorporation, y compris les conteneurs OLE, les serveurs OLE, OLE (éléments), l’activation sur place (ou édition visuelle), dispositifs de suivi, glisser -déplacer et la fusion de menus. Le terme Active s’applique pour le modèle COM (Component Object) et les objets basés sur COM tels que les contrôles ActiveX. OLE Automation est désormais appelée Automation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Arrière-plan OLE](../mfc/ole-background.md)  
 Décrit la technologie OLE et fournit des informations conceptuelles sur son fonctionnement.  
  
 [Activation](../mfc/activation-cpp.md)  
 Décrit le rôle de l’activation dans l’édition des éléments OLE.  
  
 [Conteneurs](../mfc/containers.md)  
 Fournit des liens à l’aide de conteneurs dans OLE.  
  
 [Objets de données et Sources de données](../mfc/data-objects-and-data-sources-ole.md)  
 Fournit des liens vers des rubriques traitant de l’utilisation de la `COleDataObject` et `COleDataSource` classes.  
  
 [Glisser-déposer](../mfc/drag-and-drop-ole.md)  
 Décrit l’utilisation de copier et coller avec OLE.  
  
 [Menus et ressources OLE](../mfc/menus-and-resources-ole.md)  
 Explique l’utilisation des menus et des ressources dans les applications de document OLE MFC.  
  
 [Inscription](../mfc/registration.md)  
 Traite l’initialisation et l’installation du serveur.  
  
 [Serveurs](../mfc/servers.md)  
 Décrit comment créer des OLE éléments (ou composants) pour une utilisation par les applications de conteneur.  
  
 [Dispositifs de suivi](../mfc/trackers.md)  
 Fournit des informations sur la `CRectTracker` classe, qui fournit une interface graphique pour permettre aux utilisateurs d’interagir avec les éléments clients OLE.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Points de connexion](../mfc/connection-points.md)  
 Explique comment implémenter des points de connexion (anciennement appelé points de connexion OLE) à l’aide des classes MFC `CCmdTarget` et `CConnectionPoint`.  
  
 [Composants de conteneur/serveur COM.](../mfc/containers-advanced-features.md)  
 Décrit les étapes nécessaires pour intégrer des fonctionnalités avancées optionnelles dans les applications conteneur existant.  
  
 [Le modèle d’objet composant](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 Décrit l’utilisation d’OLE sans MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../mfc/mfc-concepts.md)

