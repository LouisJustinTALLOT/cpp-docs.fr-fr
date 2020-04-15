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
ms.openlocfilehash: 2594531df63bcd62cdaec44fbc3668ea68990922
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366895"
---
# <a name="ole-in-mfc"></a>Intégration du format OLE au format MFC

Ces articles expliquent les principes fondamentaux de la programmation OLE à l’aide de MFC. MFC fournit le moyen le plus simple d’écrire des programmes qui utilisent OLE:

- Pour utiliser l’édition visuelle OLE (activation sur place).

- Pour travailler comme conteneurs ou serveurs OLE.

- Pour implémenter la fonctionnalité de drag-and-drop.

- Pour travailler avec les données de date et d’heure.

- Gérer les données d’état des modules MFC, y compris les points d’entrée de fonction DLL exportés, les points d’entrée de l’interface OLE/COM et les points d’entrée de la procédure de fenêtre.

Vous pouvez également utiliser [Automation](../mfc/automation.md).

> [!NOTE]
> Le terme OLE désigne les technologies associées à la liaison et à l’intégration, y compris les conteneurs OLE, les serveurs OLE, les éléments OLE, l’activation sur place (ou l’édition visuelle), les trackers, la traînée et la baisse et la fusion des menus. Le terme Active s’applique au modèle d’objet composant (COM) et aux objets basés sur com, tels que les commandes ActiveX. OLE Automation s’appelle maintenant Automation.

## <a name="in-this-section"></a>Dans cette section

[Arrière-plan OLE](../mfc/ole-background.md)<br/>
Discute de l’OL et fournit des informations conceptuelles sur son fonctionnement.

[Activation](../mfc/activation-cpp.md)<br/>
Décrit le rôle de l’activation dans l’édition d’éléments OLE.

[Containers](../mfc/containers.md)<br/>
Fournit des liens vers l’utilisation de conteneurs dans OLE.

[Objets de données et sources de données](../mfc/data-objects-and-data-sources-ole.md)<br/>
Fournit des liens vers des `COleDataObject` `COleDataSource` sujets discutant de l’utilisation de la et des classes.

[Glisser-déposer](../mfc/drag-and-drop-ole.md)<br/>
Discute de l’utilisation de la copie et du coller avec OLE.

[Menus et ressources OLE](../mfc/menus-and-resources-ole.md)<br/>
Explique l’utilisation des menus et des ressources dans les applications de documents MFC OLE.

[Inscription](../mfc/registration.md)<br/>
Discute de l’installation et de l’initialisation du serveur.

[Serveurs](../mfc/servers.md)<br/>
Décrit comment créer des éléments OLE (ou composants) pour une utilisation par les applications de conteneurs.

[Dispositifs de suivi](../mfc/trackers.md)<br/>
Fournit des `CRectTracker` informations sur la classe, qui fournit une interface graphique pour permettre aux utilisateurs d’interagir avec les éléments clients OLE.

## <a name="related-sections"></a>Sections connexes

[Points de connexion](../mfc/connection-points.md)<br/>
Explique comment implémenter des points de connexion (anciennement `CCmdTarget` `CConnectionPoint`connus sous le nom de points de connexion OLE) en utilisant les classes MFC et .

[Composants COM conteneur/serveur](../mfc/containers-advanced-features.md)<br/>
Décrit les étapes nécessaires pour intégrer des fonctionnalités avancées facultatives dans les applications existantes de conteneurs.

[COM (Component Object Model)](/windows/win32/com/the-component-object-model)<br/>
Décrit l’utilisation d’OLE sans MFC.

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../mfc/mfc-concepts.md)
