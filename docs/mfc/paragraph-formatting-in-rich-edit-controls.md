---
title: Mise en forme des paragraphes dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: f2ac69838bf39afb636c3d41c97adc1378463d1b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507976"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Mise en forme des paragraphes dans les contrôles RichEdit

Vous pouvez utiliser les fonctions membres du contrôle Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pour mettre en forme des paragraphes et récupérer des informations de mise en forme. Les attributs de mise en forme des paragraphes incluent l’alignement, les tabulations, les retraits et la numérotation.

Vous pouvez appliquer la mise en forme des paragraphes à l’aide de la fonction membre [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) . Pour déterminer la mise en forme de paragraphe actuelle pour le texte sélectionné, utilisez la fonction membre [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) . La structure [PARAFORMAT](/windows/win32/api/richedit/ns-richedit-paraformat) est utilisée avec ces fonctions membres pour spécifier les attributs des paragraphes. L’un des membres importants de **PARAFORMAT** est *dwMask*. Dans `SetParaFormat`, *dwMask* spécifie les attributs de paragraphe qui seront définis par cet appel de fonction. `GetParaFormat`signale les attributs du premier paragraphe de la sélection; *dwMask* spécifie les attributs qui sont cohérents tout au long de la sélection.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
