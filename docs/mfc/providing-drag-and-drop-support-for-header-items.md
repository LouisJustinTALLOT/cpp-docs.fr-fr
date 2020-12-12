---
description: 'En savoir plus sur : prise en charge du glisser-déplacer pour les éléments d’en-tête'
title: Prise en charge du glisser-déplacer pour les éléments d'en-tête
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: ed42f61220ee2033dbc36e11c18664be3968dddd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248786"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Prise en charge du glisser-déplacer pour les éléments d'en-tête

Pour assurer la prise en charge du glisser-déplacer pour les éléments d’en-tête, spécifiez le style de HDS_DRAGDROP. La prise en charge du glisser-déplacer pour les éléments d’en-tête donne à l’utilisateur la possibilité de réorganiser les éléments d’en-tête d’un contrôle header. Le comportement par défaut fournit une image de glissement translucide de l’élément d’en-tête déplacé et un indicateur visuel de la nouvelle position, si l’élément d’en-tête est supprimé.

Comme avec la fonctionnalité de glisser-déplacer courante, vous pouvez étendre le comportement par glisser-déplacer par défaut en gérant la HDN_BEGINDRAG et les notifications de HDN_ENDDRAG. Vous pouvez également personnaliser l’apparence de l’image de glissement en remplaçant la fonction membre [CHeaderCtrl :: CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) .

> [!NOTE]
> Si vous fournissez une prise en charge de la fonction glisser-déplacer pour un contrôle d’en-tête incorporé dans un contrôle de liste, consultez la section style étendu dans la rubrique [modification des styles de contrôle de liste](../mfc/changing-list-control-styles.md) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)
