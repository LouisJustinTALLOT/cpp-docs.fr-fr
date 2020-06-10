---
title: 'Contrôles ActiveX MFC : méthodes'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 9f9ec06852ed0376583363df7649331a0be02105
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621237"
---
# <a name="mfc-activex-controls-methods"></a>Contrôles ActiveX MFC : méthodes

Un contrôle ActiveX déclenche des événements pour communiquer entre lui-même et son conteneur de contrôle. Un conteneur peut également communiquer avec un contrôle au moyen de méthodes et de propriétés. Les méthodes sont également appelées fonctions.

Les méthodes et les propriétés fournissent une interface exportée pour une utilisation par d’autres applications, telles que les clients Automation et les conteneurs de contrôles ActiveX. Pour plus d’informations sur les propriétés des contrôles ActiveX, consultez l’article [contrôles ActiveX MFC : propriétés](mfc-activex-controls-properties.md).

Les méthodes sont similaires et utilisées pour les fonctions membres d’une classe C++. Il existe deux types de méthodes que votre contrôle peut implémenter : stock et personnalisé. À l’instar des événements stock, les méthodes stock sont les méthodes pour lesquelles [COleControl](reference/colecontrol-class.md) fournit une implémentation. Pour plus d’informations sur les méthodes stock, consultez l’article [contrôles ActiveX MFC : ajout de méthodes stock](mfc-activex-controls-adding-stock-methods.md). Les méthodes personnalisées, définies par le développeur, permettent une personnalisation supplémentaire du contrôle. Pour plus d’informations, consultez l’article [contrôles ActiveX MFC : ajout de méthodes personnalisées](mfc-activex-controls-adding-custom-methods.md).

Le bibliothèque MFC (Microsoft Foundation Class) (MFC) implémente un mécanisme qui permet à votre contrôle de prendre en charge les méthodes stock et personnalisées. La première partie est la classe `COleControl` . Dérivée de `CWnd` , `COleControl` les fonctions membres prennent en charge les méthodes stock qui sont communes à tous les contrôles ActiveX. La deuxième partie de ce mécanisme est la table de dispatch. Une table de dispatch est semblable à une table des messages ; Toutefois, au lieu de mapper une fonction à un ID de message Windows, un mappage de dispatch mappe des fonctions membres virtuelles à des ID IDispatch.

Pour qu’un contrôle prenne en charge différentes méthodes correctement, sa classe doit déclarer une table de dispatch. Pour ce faire, la ligne de code suivante se trouve dans l’en-tête de la classe de contrôle (. H) :

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

L’objectif principal de la table de dispatch est d’établir la relation entre les noms de méthode utilisés par un appelant externe (tel que le conteneur) et les fonctions membres de la classe du contrôle qui implémente les méthodes. Une fois que le mappage de dispatch a été déclaré, il doit être défini dans l’implémentation du contrôle (. CPP). Les lignes de code suivantes définissent la table de dispatch :

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Si vous avez utilisé l' [Assistant contrôle ActiveX MFC](reference/mfc-activex-control-wizard.md) pour créer le projet, ces lignes ont été ajoutées automatiquement. Si l’Assistant contrôle ActiveX MFC n’a pas été utilisé, vous devez ajouter ces lignes manuellement.

Les articles suivants décrivent en détail les méthodes :

- [Contrôles ActiveX MFC : ajout de méthodes stock](mfc-activex-controls-adding-stock-methods.md)

- [Contrôles ActiveX MFC : ajout de méthodes personnalisées](mfc-activex-controls-adding-custom-methods.md)

- [Contrôles ActiveX MFC : retour de codes d'erreur à partir d'une méthode](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
