---
description: En savoir plus sur les feuilles de propriétés sous forme d’assistants
title: Feuilles de propriétés sous forme d'assistants
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
ms.openlocfilehash: 2a68a16936e8ab134bab2fe78dac0d29c125b4db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248863"
---
# <a name="property-sheets-as-wizards"></a>Feuilles de propriétés sous forme d'assistants

Une des principales caractéristiques d’une feuille de propriétés de l’Assistant est que la navigation est assurée avec les boutons suivant ou terminer, précédent et annuler au lieu des tabulations. Vous devez appeler [CPropertySheet :: SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) avant d’appeler [CPropertySheet ::D omodal](../mfc/reference/cpropertysheet-class.md#domodal) sur l’objet de feuille de propriétés pour tirer parti de cette fonctionnalité.

L’utilisateur reçoit les mêmes notifications [CPropertyPage :: OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) et [CPropertyPage :: OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) lors du déplacement d’une page à une autre. Les boutons suivant et terminer sont des contrôles s’excluant mutuellement ; autrement dit, une seule d’entre elles sera affichée à la fois. Sur la première page, le bouton suivant doit être activé. Si l’utilisateur se trouve sur la dernière page, le bouton Terminer doit être activé. Cela n’est pas effectué automatiquement par le Framework. Vous devez appeler [CPropertySheet :: SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) sur la dernière page pour y parvenir.

Pour afficher tous les boutons par défaut, vous doit afficher le bouton Terminer et déplacer le bouton suivant. Déplacez ensuite le bouton précédent afin que sa position relative sur le bouton suivant soit conservée.

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)
