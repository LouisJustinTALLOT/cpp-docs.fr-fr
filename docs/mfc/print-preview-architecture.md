---
title: Architecture de l'aperçu avant impression
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375943"
---
# <a name="print-preview-architecture"></a>Architecture de l'aperçu avant impression

Cet article explique comment le framework MFC implémente la fonctionnalité d'aperçu avant impression. Sont abordés les sujets suivants :

- [Processus d'aperçu avant impression](#_core_the_print_preview_process)

- [Modification de l’aperçu d’impression](#_core_modifying_print_preview)

L'aperçu avant impression est quelque peu différent de l'écran et de l'impression puisque, au lieu d'ajouter directement une image sur un périphérique, l'application doit simuler l'imprimante à l'aide de l'écran. Pour s’adapter à cela, la Microsoft Foundation Class Library définit une `CPreviewDC`classe spéciale (sans papiers) dérivée de la classe [CDC](../mfc/reference/cdc-class.md), appelée . Tous les objets `CDC` contiennent deux contextes de périphérique, mais ils sont généralement identiques. Dans `CPreviewDC` un objet, ils sont différents : le premier représente l’imprimante simulée, et le second représente l’écran sur lequel la sortie est effectivement affichée.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Le processus d’aperçu d’impression

Lorsque l’utilisateur sélectionne la commande Aperçu d’impression `CPreviewDC` dans le menu **Fichier,** le cadre crée un objet. Chaque fois que votre application effectue une opération définissant une caractéristique du contexte de l'imprimante, le framework exécute également une opération semblable dans le contexte de périphérique. Par exemple, si votre application sélectionne une police pour l'impression, le framework sélectionne une police pour l'écran qui simule la police d'imprimante. Chaque fois que votre application envoie la sortie vers l'imprimante, le framework envoie à la place la sortie à l'écran.

L'aperçu avant impression diffère également de l'impression dans l'ordre de plan dans lequel chacun dessine les pages d'un document. Lors de l'impression, le framework suit une boucle continue d'impression jusqu'à ce qu'une certaine plage de pages ait été affichée. Pendant l'aperçu avant impression, une ou deux pages sont affichées à tout moment, puis l'application attend ; aucune page ne s'affiche jusqu'à ce que l'utilisateur réponde. Lors de l’aperçu d’impression, l’application doit également répondre à WM_PAINT messages, tout comme lors de l’affichage de l’écran ordinaire.

La fonction [CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) est appelée lorsque le mode aperçu est invoqué, tout comme il est au début d’un travail d’impression. La structure [CPrintInfo Structure](../mfc/reference/cprintinfo-structure.md) transmise à la fonction contient plusieurs membres dont vous pouvez définir les valeurs pour ajuster certaines caractéristiques de l’opération d’aperçu d’impression. Par exemple, vous pouvez définir le *m_nNumPreviewPages* membre pour spécifier si vous souhaitez prévisualiser le document en mode d’une ou deux pages.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Modification de l’aperçu de l’impression

Vous pouvez facilement modifier le comportement et l'affichage de l'aperçu avant impression de plusieurs façons. Par exemple, vous pouvez, entre autres choses :

- Amener l'aperçu avant impression à afficher une barre de défilement pour un accès aisé à toute page du document.

- Amener l'aperçu avant impression à maintenir la position de l'utilisateur dans le document en commençant son affichage par la page actuelle.

- Amener l'exécution de différentes initialisations pour l'aperçu avant impression et l'impression.

- Amener l'aperçu avant impression à afficher des numéros de page dans vos propres formats.

Si vous connaissez le délai d'attente du document et appelez `SetMaxPage` avec la valeur appropriée, le framework peut utiliser ces informations en mode aperçu ainsi que lors de l'impression. Une fois que le framework connaît la longueur du document, elle peut fournir à la fenêtre d'aperçu une barre de défilement, ce qui permet à l'utilisateur de passer d'une page à une autre dans les deux sens au sein du document en mode aperçu. Si vous n'avez pas défini la longueur du document, le framework ne peut pas placer la zone de défilement pour indiquer la position actuelle, le framework n'ajoute pas de barre de défilement. Dans ce cas, l'utilisateur doit utiliser les boutons de page suivante et de page précédente dans la barre de contrôle de la fenêtre d'aperçu pour naviguer dans le document.

Pour l’aperçu d’impression, vous pouvez trouver utile d’attribuer une valeur à la *m_nCurPage* membre de `CPrintInfo`, même si vous ne le feriez jamais pour l’impression ordinaire. Lors de l'impression ordinaire, ce membre fournit les informations de le framework à votre classe d'affichage. Voici comment le framework indique à la vue quelle page doit être imprimée.

En revanche, lorsque le mode d’aperçu d’impression est lancé, le *m_nCurPage* membre porte des informations dans la direction opposée: de la vue au cadre. Le framework utilise la valeur de ce membre pour déterminer si la page doit d'abord afficher un aperçu. La valeur par défaut de ce membre est 1, la première page du document s'affiche initialement. Vous pouvez remplacer `OnPreparePrinting` pour affecter à ce membre le numéro de la page affichée lorsque la commande aperçu avant impression a été appelée. De cette manière, l'application gère la position actuelle de l'utilisateur lors du passage du mode d'affichage normale au mode d'aperçu avant impression.

Parfois, vous pouvez souhaiter que `OnPreparePrinting` effectue différentes initialisations selon qu'il est appelé pour un travail d'impression ou pour l'aperçu avant impression. Vous pouvez le déterminer *m_bPreview* en examinant la variable `CPrintInfo` m_bPreview membre de la structure. Ce membre est réglé sur **TRUE** lorsque l’aperçu d’impression est invoqué.

La `CPrintInfo` structure contient également un membre nommé *m_strPageDesc*, qui est utilisé pour formater les chaînes affichées au bas de l’écran en mode page unique et plusieurs pages. Par défaut, ces chaînes sont du formulaire " Page *n*" et " Pages `OnPreparePrinting` *n* - *m*", mais vous pouvez modifier *m_strPageDesc* de l’intérieur et régler les cordes à quelque chose de plus élaboré. Voir [la structure CPrintInfo](../mfc/reference/cprintinfo-structure.md) dans la *référence MFC* pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Impression et aperçu avant impression](../mfc/printing-and-print-preview.md)<br/>
[Impression](../mfc/printing.md)<br/>
[Classe CView](../mfc/reference/cview-class.md)<br/>
[Classe CDC](../mfc/reference/cdc-class.md)
