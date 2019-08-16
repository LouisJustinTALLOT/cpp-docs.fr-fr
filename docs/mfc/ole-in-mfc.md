---
title: Intégration du format OLE au format MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 2668d35c24e9d95440a96c5b3eda1fab7bbf3891
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507997"
---
# <a name="ole-in-mfc"></a>Intégration du format OLE au format MFC

Ces articles expliquent les principes de base de la programmation OLE à l’aide de MFC. MFC offre le moyen le plus simple d’écrire des programmes qui utilisent OLE:

- Pour utiliser la modification visuelle OLE (activation sur place).

- Pour travailler en tant que conteneurs OLE ou serveurs.

- Pour implémenter la fonctionnalité de glisser-déplacer.

- Pour utiliser des données de date et d’heure.

- Pour gérer les données d’état des modules MFC, y compris les points d’entrée de fonction DLL exportés, les points d’entrée de l’interface OLE/COM et les points d’entrée de la procédure de fenêtre.

Vous pouvez également utiliser [Automation](../mfc/automation.md).

> [!NOTE]
>  Le terme OLE désigne les technologies associées à la liaison et à l’incorporation, y compris les conteneurs OLE, les serveurs OLE, les éléments OLE, l’activation sur place (ou l’édition visuelle), les traceurs, le glisser-déplacer et la fusion de menus. Le terme actif s’applique aux objets COM (Component Object Model) et COM, tels que les contrôles ActiveX. OLE Automation est maintenant appelé Automation.

## <a name="in-this-section"></a>Dans cette section

[Arrière-plan OLE](../mfc/ole-background.md)<br/>
Décrit OLE et fournit des informations conceptuelles sur son fonctionnement.

[Activation](../mfc/activation-cpp.md)<br/>
Décrit le rôle de l’activation dans la modification des éléments OLE.

[Conteneurs](../mfc/containers.md)<br/>
Fournit des liens vers l’utilisation de conteneurs dans OLE.

[Objets de données et sources de données](../mfc/data-objects-and-data-sources-ole.md)<br/>
Fournit des liens vers des rubriques qui traitent `COleDataObject` de `COleDataSource` l’utilisation des classes et.

[Glisser-déposer](../mfc/drag-and-drop-ole.md)<br/>
Traite de l’utilisation de la copie et du collage avec OLE.

[Menus et ressources OLE](../mfc/menus-and-resources-ole.md)<br/>
Explique l’utilisation des menus et des ressources dans les applications de document OLE MFC.

[Inscription](../mfc/registration.md)<br/>
Traite de l’installation et de l’initialisation du serveur.

[Serveurs](../mfc/servers.md)<br/>
Décrit comment créer des éléments OLE (ou composants) pour une utilisation par les applications de conteneur.

[Dispositifs de suivi](../mfc/trackers.md)<br/>
Fournit des informations sur `CRectTracker` la classe, qui fournit une interface graphique pour permettre aux utilisateurs d’interagir avec les éléments du client OLE.

## <a name="related-sections"></a>Rubriques connexes

[Points de connexion](../mfc/connection-points.md)<br/>
Explique comment implémenter des points de connexion (anciennement appelés points de connexion OLE) à `CCmdTarget` l' `CConnectionPoint`aide des classes MFC et.

[Composants COM conteneur/serveur](../mfc/containers-advanced-features.md)<br/>
Décrit les étapes nécessaires pour incorporer des fonctionnalités avancées facultatives dans les applications de conteneur existantes.

[COM (Component Object Model)](/windows/win32/com/the-component-object-model)<br/>
Décrit l’utilisation d’OLE sans MFC.

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)
