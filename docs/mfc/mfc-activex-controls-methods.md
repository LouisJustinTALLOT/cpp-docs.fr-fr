---
title: 'Contrôles ActiveX MFC : Méthodes'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 71c4cdd5ea07b3468b7878a221129a0de5eb4974
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386367"
---
# <a name="mfc-activex-controls-methods"></a>Contrôles ActiveX MFC : Méthodes

Un contrôle ActiveX déclenche des événements pour communiquer entre lui-même et son conteneur. Un conteneur peut également communiquer avec un contrôle au moyen de méthodes et propriétés. Méthodes sont également appelées fonctions.

Méthodes et propriétés fournissent une interface exportée pour une utilisation par d’autres applications, telles que les clients Automation et les conteneurs de contrôles ActiveX. Pour plus d’informations sur les propriétés de contrôle ActiveX, consultez l’article [contrôles ActiveX MFC : Propriétés](../mfc/mfc-activex-controls-properties.md).

Méthodes sont similaires dans l’utilisation et de fin pour les fonctions membres d’une classe C++. Il existe deux types de méthodes de votre contrôle peut implémenter : stock et personnalisés. Similaire à des événements stock, les méthodes stock sont celles qui [COleControl](../mfc/reference/colecontrol-class.md) fournit une implémentation. Pour plus d’informations sur les méthodes stock, consultez l’article [contrôles ActiveX MFC : Ajout de méthodes Stock](../mfc/mfc-activex-controls-adding-stock-methods.md). Des méthodes personnalisées définies par le développeur, permettent une personnalisation supplémentaire du contrôle. Pour plus d’informations, consultez l’article [contrôles ActiveX MFC : Ajout de méthodes personnalisées](../mfc/mfc-activex-controls-adding-custom-methods.md).

Les MFC Microsoft Foundation Class Library () implémente un mécanisme qui permet à votre contrôle prenne en charge les méthodes stock et personnalisées. La première partie est la classe `COleControl`. Dérivé `CWnd`, `COleControl` fonctions membres prennent en charge les méthodes stock qui sont communes à tous les contrôles ActiveX. La deuxième partie de ce mécanisme est la table de dispatch. Une table de dispatch est similaire à une table des messages ; Toutefois, au lieu d’une fonction de mappage à un ID de message Windows, une table de dispatch mappe des fonctions membres virtuelles à des ID IDispatch.

Pour un contrôle prendre en charge différentes méthodes correctement, sa classe doit déclarer une table de dispatch. Pour cela la ligne de code qui se trouve dans l’en-tête de classe de contrôle suivante (. H) fichier :

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

L’objectif principal de la table de dispatch consiste à établir la relation entre les noms de la méthode utilisée par un appelant externe (par exemple, le conteneur) et les fonctions membres de la classe du contrôle qui implémentent les méthodes. Une fois que la table de dispatch a été déclarée, il doit être défini dans l’implémentation du contrôle (. Fichier CPP). Les lignes de code suivantes définissent la table de dispatch :

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Si vous avez utilisé le [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) pour créer le projet, ces lignes ont été ajoutées automatiquement. Si l’Assistant contrôle ActiveX MFC n’a pas été utilisé, vous devez ajouter manuellement ces lignes.

Les articles suivants traitent des méthodes en détail :

- [Contrôles ActiveX MFC : Ajout de méthodes stock](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Contrôles ActiveX MFC : Ajout de méthodes personnalisées](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Contrôles ActiveX MFC : Retour de codes d’erreur à partir d’une méthode](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
