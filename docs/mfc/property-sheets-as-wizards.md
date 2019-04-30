---
title: Feuilles de propriétés sous forme d'assistants
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
ms.openlocfilehash: c60148c099b34993bef0c9808e6561e37c26cc7f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391359"
---
# <a name="property-sheets-as-wizards"></a>Feuilles de propriétés sous forme d'assistants

Une caractéristique clé d’une feuille de propriétés Assistant est que la navigation est fournie avec des boutons suivant ou terminer, précédent et annuler au lieu d’onglets. Vous devez appeler [fonction CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) avant d’appeler [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) sur l’objet de feuille de propriétés pour tirer parti de cette fonctionnalité.

L’utilisateur reçoit les mêmes [notifications CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) et [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) notifications lors du déplacement d’une page vers une autre page. Boutons suivant et terminer sont des contrôles qui s’excluent mutuellement ; Autrement dit, qu’un seul d'entre eux s’affichera à la fois. Sur la première page, le bouton suivant doit être activé. Si l’utilisateur se trouve sur la dernière page, le bouton Terminer doit être activé. Cela n'est pas effectuée automatiquement par l’infrastructure. Vous devez appeler [fonction CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) sur la dernière page pour y parvenir.

Pour afficher tous les boutons par défaut, vous devez afficher le bouton Terminer et déplacez le bouton suivant. Déplacez ensuite le bouton précédent afin que sa position relative pour le bouton suivant est maintenue.

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)
