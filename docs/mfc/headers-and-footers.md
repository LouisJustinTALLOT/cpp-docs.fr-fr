---
title: En-têtes et pieds de page
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 7024c57dbe41a579582d409d0536db0ca0bc46d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620110"
---
# <a name="headers-and-footers"></a>En-têtes et pieds de page

Cet article explique comment ajouter des en-têtes et pieds de page à un document imprimé.

Lorsque vous consultez un document à l'écran, le nom du document et la position actuelle dans le document sont généralement affichés dans la barre de titre et la barre d'état. En consultant une copie imprimée d'un document, il est utile d'avoir le nom et le numéro de page affichés dans un en-tête ou un pied de page. C'est un point fréquent sur lequel même les programmes WYSIWYG diffèrent dans la façon dont ils effectuent l'impression et l'affichage à l'écran.

La fonction membre [OnPrint](reference/cview-class.md#onprint) est l’emplacement approprié pour imprimer des en-têtes ou des pieds de page, car elle est appelée pour chaque page, et parce qu’elle est appelée uniquement pour l’impression, pas pour l’affichage à l’écran. Vous pouvez définir une fonction distincte pour imprimer un en-tête ou un pied de page, et lui passer le contexte de l'imprimante à partir de `OnPrint`. Vous devrez peut-être ajuster l’origine ou l’étendue de la fenêtre avant d’appeler [OnDraw](reference/cview-class.md#ondraw) pour éviter que le corps de la page ne chevauche l’en-tête ou le pied de page. Vous devrez peut-être modifier `OnDraw` car la quantité de document qui tient dans la page peut être réduite.

Pour compenser la zone occupée par l’en-tête ou le pied de page, il est possible d’utiliser le membre **m_rectDraw** de [CPrintInfo](reference/cprintinfo-structure.md). Chaque fois qu'une page est imprimée, ce membre est initialisé avec la zone utilisable de la page. Si vous imprimez un en-tête ou un pied de page avant d’imprimer le corps de la page, vous pouvez réduire la taille du rectangle stocké dans **m_rectDraw** pour prendre en compte la zone occupée par l’en-tête ou le pied de page. `OnPrint`Peut ensuite faire référence à **m_rectDraw** pour savoir combien de temps reste-il pour imprimer le corps de la page.

Vous ne pouvez pas imprimer un en-tête, ou autre chose, à partir de [OnPrepareDC](reference/cview-class.md#onpreparedc), car il est appelé avant que la `StartPage` fonction membre de [CDC](reference/cdc-class.md) soit appelée. À ce stade, le contexte de l'imprimante est considéré comme étant la limite d'une page. Vous pouvez exécuter l'impression uniquement depuis la fonction membre `OnPrint`.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Imprimer des documents multipages](multipage-documents.md)

- [Allocation de ressources GDI pour l'impression](allocating-gdi-resources.md)

## <a name="see-also"></a>Voir aussi

[Impression](printing.md)
