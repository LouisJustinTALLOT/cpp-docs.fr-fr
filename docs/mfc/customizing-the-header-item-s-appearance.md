---
title: Personnalisation de l’élément d’en-tête&#39;s apparence
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 081260bd5c1cf6335d398a4fd773c9590dbc8030
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268835"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personnalisation de l’élément d’en-tête&#39;s apparence

En définissant le *dwStyle* paramètre lorsque vous créez un contrôle header ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), vous pouvez définir l’apparence et les éléments de comportement de l’en-tête ou du contrôle header lui-même.

Voici un échantillon des styles que vous pouvez définir et leur objectif :

- Pour rendre un élément d’en-tête se présenter comme un bouton de commande, utilisez le **HDS_BUTTONS** style.

   Utilisez ce style si vous souhaitez exécuter des actions en réponse aux clics de souris sur un élément d’en-tête, telles que le tri des données par une colonne particulière, comme c’est le cas dans Microsoft Outlook.

- Pour donner des éléments d’en-tête une apparence « réactive » lorsque le curseur de la souris passe dessus, utilisez le **HDS_HOTTRACK** style.

   Suivi affiche un contour 3D lorsque le pointeur passe sur un élément dans un sinon plat barre.

- Pour indiquer que le contrôle header doit être masqué, utilisez le **HDS_HIDDEN** style.

   Le **HDS_HIDDEN** style indique que le contrôle header est destiné à être utilisé comme un conteneur de données et pas un contrôle visuel. Ce style ne masque pas automatiquement le contrôle, mais, au lieu de cela, affecte le comportement de `CHeaderCtrl::Layout`. La valeur retournée dans le *cy* membre de la `WINDOWPOS` structure sera égal à zéro qui indique que le contrôle ne doit pas être visible par l’utilisateur.

Pour plus d’informations sur ces propriétés, consultez [éléments](/windows/desktop/Controls/header-controls) dans le SDK Windows. Pour plus d’informations sur l’ajout d’éléments à un contrôle header, consultez [Ajout d’éléments au contrôle Header](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
