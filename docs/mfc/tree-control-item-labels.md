---
title: Étiquettes d’élément de contrôle d’arborescence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f07032a203761e78bd44f40456093eae9a84d07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399877"
---
# <a name="tree-control-item-labels"></a>Étiquettes d’élément de contrôle d’arborescence

En règle générale, vous spécifiez le texte d’étiquette de l’élément lors de l’ajout de l’élément au contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Le `InsertItem` fonction membre peut passer un [structure TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) structure qui définit les propriétés de l’élément, y compris une chaîne contenant le texte de l’étiquette. `InsertItem` a plusieurs surcharges qui peuvent être appelées avec diverses combinaisons de paramètres.

Un contrôle d’arborescence alloue de la mémoire pour le stockage de chaque élément ; le texte des étiquettes occupe une partie significative de cette mémoire. Si votre application conserve une copie des chaînes dans le contrôle d’arborescence, vous pouvez réduire la mémoire requise par le contrôle en spécifiant le **LPSTR_TEXTCALLBACK** valeur dans le *pszText* membre `TV_ITEM` ou *lpszItem* paramètre au lieu de passer des chaînes réelles au contrôle d’arborescence. À l’aide de **LPSTR_TEXTCALLBACK** entraîne le contrôle d’arborescence récupérer le texte d’étiquette de l’élément à partir de l’application chaque fois que l’élément doit être redessiné. Pour récupérer le texte, le contrôle d’arborescence envoie un [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) message de notification, qui inclut l’adresse d’un [structure NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) structure. Vous devez répondre en définissant les membres appropriés de la structure incluse.

Un contrôle d’arborescence utilise la mémoire allouée à partir du tas du processus qui crée le contrôle d’arborescence. Le nombre maximal d’éléments dans un contrôle d’arborescence est basé sur la quantité de mémoire disponible dans le tas. Chaque élément occupe 64 octets.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

