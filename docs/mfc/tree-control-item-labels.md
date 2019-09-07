---
title: Étiquettes d'élément de contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 16bb2bbe63eaf8ea4ce30040589d4a8a4cf4dfd3
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741460"
---
# <a name="tree-control-item-labels"></a>Étiquettes d'élément de contrôle d'arborescence

En général, vous spécifiez le texte de l’étiquette d’un élément lors de l’ajout de l’élément au contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). La `InsertItem` fonction membre peut passer une structure [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) qui définit les propriétés de l’élément, y compris une chaîne contenant le texte de l’étiquette. `InsertItem`a plusieurs surcharges qui peuvent être appelées avec différentes combinaisons de paramètres.

Un contrôle d’arborescence alloue de la mémoire pour stocker chaque élément ; le texte des étiquettes d’élément occupe une partie importante de cette mémoire. Si votre application gère une copie des chaînes dans le contrôle d’arborescence, vous pouvez réduire les besoins en mémoire du contrôle en spécifiant la valeur **LPSTR_TEXTCALLBACK** dans le membre pszText `TV_ITEM` de ou le *lpszItem* au lieu de passer des chaînes réelles au contrôle d’arborescence. Si vous utilisez **LPSTR_TEXTCALLBACK** , le contrôle d’arborescence récupère le texte de l’étiquette d’un élément à partir de l’application chaque fois que l’élément doit être redessiné. Pour récupérer le texte, le contrôle d’arborescence envoie un message de notification [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) , qui comprend l’adresse d’une structure [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) . Vous devez répondre en définissant les membres appropriés de la structure incluse.

Un contrôle d’arborescence utilise la mémoire allouée à partir du tas du processus qui crée le contrôle d’arborescence. Le nombre maximal d’éléments dans un contrôle d’arborescence est basé sur la quantité de mémoire disponible dans le tas. Chaque élément utilise 64 octets.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
