---
title: OLE au format MFC | Microsoft Docs
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
ms.openlocfilehash: e43484e5f30191c604f43a2280a8deab6eddd93c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434945"
---
# <a name="ole-in-mfc"></a>Intégration du format OLE au format MFC

Ces articles expliquent les principes fondamentaux de la programmation OLE à l’aide de MFC. MFC fournit le moyen le plus simple pour écrire des programmes qui utilisent OLE :

- Pour utiliser OLE visual Édition (dans l’activation sur place).

- Pour fonctionner en tant que conteneurs OLE ou serveurs.

- Pour implémenter la fonctionnalité de glisser-déplacer.

- Pour travailler avec les données de date et d’heure.

- Pour gérer les données d’état de la bibliothèque MFC modules, y compris exporté des points d’entrée DLL (fonction), les points d’entrée interface OLE/COM et les points d’entrée de procédure de fenêtre.

Vous pouvez également utiliser [Automation](../mfc/automation.md).

> [!NOTE]
>  Le terme QU'OLE indique les technologies associées à la liaison et incorporation, y compris les conteneurs OLE, serveurs OLE, les éléments OLE, l’activation sur place (ou modification visuelle), les dispositifs de suivi, glisser -déplacer et fusion de menus. Le terme actif s’applique à l’objet COM (Component Model) et les objets basés sur COM tels que les contrôles ActiveX. OLE Automation est désormais appelée Automation.

## <a name="in-this-section"></a>Dans cette section

[Arrière-plan OLE](../mfc/ole-background.md)<br/>
Décrit la technologie OLE et fournit des informations conceptuelles sur son fonctionnement.

[Activation](../mfc/activation-cpp.md)<br/>
Décrit le rôle de l’activation dans l’édition des éléments OLE.

[Conteneurs](../mfc/containers.md)<br/>
Fournit des liens vers l’utilisation de conteneurs dans OLE.

[Objets de données et Sources de données](../mfc/data-objects-and-data-sources-ole.md)<br/>
Fournit des liens vers des rubriques décrivant l’utilisation de la `COleDataObject` et `COleDataSource` classes.

[Glisser-déposer](../mfc/drag-and-drop-ole.md)<br/>
Décrit l’utilisation de copier et coller avec OLE.

[Menus et ressources OLE](../mfc/menus-and-resources-ole.md)<br/>
Explique l’utilisation des menus et des ressources dans les applications de document OLE MFC.

[Inscription](../mfc/registration.md)<br/>
Traite l’initialisation et l’installation du serveur.

[Serveurs](../mfc/servers.md)<br/>
Décrit comment créer des OLE éléments (ou composants) pour une utilisation par les applications de conteneur.

[Dispositifs de suivi](../mfc/trackers.md)<br/>
Fournit des informations sur la `CRectTracker` classe, qui fournit une interface graphique pour permettre aux utilisateurs d’interagir avec les éléments clients OLE.

## <a name="related-sections"></a>Rubriques connexes

[Points de connexion](../mfc/connection-points.md)<br/>
Explique comment implémenter des points de connexion (anciennement appelé points de connexion OLE) à l’aide des classes MFC `CCmdTarget` et `CConnectionPoint`.

[Composants de conteneur/serveur COM](../mfc/containers-advanced-features.md)<br/>
Décrit les étapes nécessaires pour incorporer des fonctionnalités avancées facultatives dans les applications de conteneur existantes.

[Le modèle d’objet composant](/windows/desktop/com/the-component-object-model)<br/>
Décrit l’utilisation d’OLE sans MFC.

## <a name="see-also"></a>Voir aussi

[Concepts](../mfc/mfc-concepts.md)

