---
description: 'En savoir plus sur : classement des éléments dans le contrôle header'
title: Organisation des éléments dans le contrôle Header
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: 6f6db7b134121c4084d9406ad537bf0ce5dc12cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330121"
---
# <a name="ordering-items-in-the-header-control"></a>Organisation des éléments dans le contrôle Header

Une fois que vous avez [ajouté des éléments à un contrôle header](adding-items-to-the-header-control.md), vous pouvez manipuler ou obtenir des informations sur leur ordre à l’aide des fonctions suivantes :

- [CHeaderCtrl :: GetOrderArray](reference/cheaderctrl-class.md#getorderarray) et [CHeaderCtrl :: SetOrderArray](reference/cheaderctrl-class.md#setorderarray)

   Récupère et définit l’ordre de gauche à droite des éléments d’en-tête.

- [CHeaderCtrl :: OrderToIndex](reference/cheaderctrl-class.md#ordertoindex).

   Récupère la valeur d’index pour un élément d’en-tête spécifique.

Outre les fonctions membres précédentes, le style HDS_DRAGDROP permet à l’utilisateur de glisser-déplacer des éléments d’en-tête dans le contrôle header. Pour plus d’informations, consultez [prise en charge du glisser-déplacer pour les éléments d’en-tête](providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CHeaderCtrl](using-cheaderctrl.md)
