---
title: Mise en forme dans les contrôles Rich Edit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8258ff95fc91f6f29d424e77be95ce1b44f621ac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215819"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Mise en forme des paragraphes dans les contrôles RichEdit
Vous pouvez utiliser les fonctions membres de contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pour mettre en forme les paragraphes et pour récupérer des informations de mise en forme. Attributs de mise en forme de paragraphe incluent l’alignement, les onglets, tirets et la numérotation.  
  
 Vous pouvez appliquer la mise en forme à l’aide de la [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) fonction membre. Pour déterminer le paragraphe actuel de mise en forme pour le texte sélectionné, utilisez le [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) fonction membre. Le [RAJOUTER](/windows/desktop/api/richedit/ns-richedit-_paraformat) structure est utilisée avec ces fonctions membres pour spécifier les attributs de paragraphe. Un des membres importants de **RAJOUTER** est *dwMask*. Dans `SetParaFormat`, *dwMask* spécifie quels attributs de paragraphe seront définis par cet appel de fonction. `GetParaFormat` Indique les attributs du premier paragraphe de la sélection ; *dwMask* spécifie les attributs qui sont cohérentes dans la sélection.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

