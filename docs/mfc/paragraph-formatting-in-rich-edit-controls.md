---
description: En savoir plus sur la mise en forme des paragraphes dans les contrôles RichEdit
title: Mise en forme des paragraphes dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 69c853c6b552b9950769fc9e3509bd4b5e55ea43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205913"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Mise en forme des paragraphes dans les contrôles RichEdit

Vous pouvez utiliser les fonctions membres du contrôle Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) pour mettre en forme des paragraphes et récupérer des informations de mise en forme. Les attributs de mise en forme des paragraphes incluent l’alignement, les tabulations, les retraits et la numérotation.

Vous pouvez appliquer la mise en forme des paragraphes à l’aide de la fonction membre [SetParaFormat](reference/cricheditctrl-class.md#setparaformat) . Pour déterminer la mise en forme de paragraphe actuelle pour le texte sélectionné, utilisez la fonction membre [GetParaFormat](reference/cricheditctrl-class.md#getparaformat) . La structure [PARAFORMAT](/windows/win32/api/richedit/ns-richedit-paraformat) est utilisée avec ces fonctions membres pour spécifier les attributs des paragraphes. L’un des membres importants de **PARAFORMAT** est *dwMask*. Dans `SetParaFormat` , *dwMask* spécifie les attributs de paragraphe qui seront définis par cet appel de fonction. `GetParaFormat` signale les attributs du premier paragraphe de la sélection ; *dwMask* spécifie les attributs qui sont cohérents tout au long de la sélection.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)
