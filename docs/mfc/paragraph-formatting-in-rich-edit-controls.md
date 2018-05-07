---
title: Mise en forme dans les contrôles RichEdit | Documents Microsoft
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
ms.openlocfilehash: 113d47a88f0de7ddd12f474678705688569ad50d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Mise en forme des paragraphes dans les contrôles RichEdit
Vous pouvez utiliser les fonctions membres du contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) pour mettre en forme les paragraphes et pour récupérer les informations de mise en forme. Attributs de mise en forme de paragraphe incluent l’alignement, les onglets, les retraits et la numérotation.  
  
 Vous pouvez appliquer la mise en forme à l’aide de la [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) fonction membre. Pour déterminer la mise en forme pour le texte sélectionné, utilisez le [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) fonction membre. Le [RAJOUTER](http://msdn.microsoft.com/library/windows/desktop/bb787940) structure est utilisée avec ces fonctions membres pour spécifier des attributs de paragraphe. Un des membres importants de **RAJOUTER** est **dwMask**. Dans `SetParaFormat`, **dwMask** spécifie les attributs de paragraphe seront définis par cet appel de fonction. `GetParaFormat` Indique les attributs du premier paragraphe de la sélection ; **dwMask** spécifie les attributs qui sont cohérentes dans la sélection.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

