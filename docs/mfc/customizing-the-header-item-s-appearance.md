---
title: Personnalisation de l’apparence des&#39;éléments d’en-tête
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 6ce676695d717fcc5d418fe4ed5df91b4f9bca95
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508719"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personnalisation de l’apparence des&#39;éléments d’en-tête

En définissant le paramètre *dwStyle* lorsque vous créez pour la première fois un contrôle header ([CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create)), vous pouvez définir l’apparence et le comportement des éléments d’en-tête ou du contrôle header lui-même.

Voici un échantillon des styles que vous pouvez définir, et leur fonction:

- Pour qu’un élément d’en-tête ressemble à un PUSHBUTTON, utilisez le style **HDS_BUTTONS** .

   Utilisez ce style si vous souhaitez effectuer des actions en réponse à des clics de souris sur un élément d’en-tête, comme le tri des données par une colonne particulière, comme c’est le cas dans Microsoft Outlook.

- Pour attribuer à l’en-tête des éléments une apparence «suivi à chaud» lorsque le curseur de la souris passe dessus, utilisez le style **HDS_HOTTRACK** .

   Le suivi réactif affiche un contour 3D lorsque le pointeur passe sur un élément dans une barre à deux dimensions.

- Pour indiquer que le contrôle header doit être masqué, utilisez le style **HDS_HIDDEN** .

   Le style **HDS_HIDDEN** indique que le contrôle header est destiné à être utilisé comme conteneur de données et non comme un contrôle visuel. Ce style ne masque pas automatiquement le contrôle, mais affecte le comportement de `CHeaderCtrl::Layout`. La valeur retournée dans le membre *CY* de `WINDOWPOS` la structure est égale à zéro, ce qui indique que le contrôle ne doit pas être visible par l’utilisateur.

Pour plus d’informations sur ces propriétés, consultez [éléments](/windows/win32/Controls/header-controls) dans la SDK Windows. Pour plus d’informations sur l’ajout d’éléments à un contrôle header, consultez [Ajout d’éléments au contrôle header](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
