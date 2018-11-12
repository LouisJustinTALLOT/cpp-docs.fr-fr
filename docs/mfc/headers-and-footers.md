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
ms.openlocfilehash: 15c76dabb2512b5906ca631e0da5047fabddf848
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564500"
---
# <a name="headers-and-footers"></a>En-têtes et pieds de page

Cet article explique comment ajouter des en-têtes et pieds de page à un document imprimé.

Lorsque vous consultez un document à l'écran, le nom du document et la position actuelle dans le document sont généralement affichés dans la barre de titre et la barre d'état. En consultant une copie imprimée d'un document, il est utile d'avoir le nom et le numéro de page affichés dans un en-tête ou un pied de page. C'est un point fréquent sur lequel même les programmes WYSIWYG diffèrent dans la façon dont ils effectuent l'impression et l'affichage à l'écran.

Le [OnPrint](../mfc/reference/cview-class.md#onprint) fonction membre est l’emplacement approprié pour imprimer les en-têtes ou pieds de page, car elle est appelée pour chaque page, et parce qu’elle est appelée uniquement pour l’impression, pas pour l’écran. Vous pouvez définir une fonction distincte pour imprimer un en-tête ou un pied de page, et lui passer le contexte de l'imprimante à partir de `OnPrint`. Vous devrez peut-être ajuster l’origine de la fenêtre ou l’étendue avant d’appeler [OnDraw](../mfc/reference/cview-class.md#ondraw) pour éviter que le corps de la superposition de page, l’en-tête ou le pied de page. Vous devrez peut-être modifier `OnDraw` car la quantité de document qui tient dans la page peut être réduite.

Une façon de compenser pour la zone occupée par l’en-tête ou le pied de page est d’utiliser le **m_rectDraw** membre [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Chaque fois qu'une page est imprimée, ce membre est initialisé avec la zone utilisable de la page. Si vous imprimez un en-tête ou un pied de page avant d’imprimer le corps de la page, vous pouvez réduire la taille du rectangle stocké dans **m_rectDraw** pour prendre en compte la zone occupée par l’en-tête ou le pied de page. Puis `OnPrint` peuvent faire référence à **m_rectDraw** pour déterminer la zone restante pour imprimer le corps de la page.

Vous ne pouvez pas imprimer un en-tête, ou tout autre élément, à partir de [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc), car elle est appelée avant la `StartPage` fonction membre de [CDC](../mfc/reference/cdc-class.md) a été appelée. À ce stade, le contexte de l'imprimante est considéré comme étant la limite d'une page. Vous pouvez exécuter l'impression uniquement depuis la fonction membre `OnPrint`.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Imprimer des documents multipages](../mfc/multipage-documents.md)

- [Allocation de ressources GDI pour l’impression](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Voir aussi

[Impression](../mfc/printing.md)

