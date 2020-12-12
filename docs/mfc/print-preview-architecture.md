---
description: 'En savoir plus sur : architecture de l’aperçu avant impression'
title: Architecture de l'aperçu avant impression
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 34dcd02b189a0065b34cff756596c5c5b1576dc6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205861"
---
# <a name="print-preview-architecture"></a>Architecture de l'aperçu avant impression

Cet article explique comment le framework MFC implémente la fonctionnalité d'aperçu avant impression. Sont abordés les sujets suivants :

- [Processus d'aperçu avant impression](#_core_the_print_preview_process)

- [Modification de l’aperçu avant impression](#_core_modifying_print_preview)

L'aperçu avant impression est quelque peu différent de l'écran et de l'impression puisque, au lieu d'ajouter directement une image sur un périphérique, l'application doit simuler l'imprimante à l'aide de l'écran. Pour ce faire, le bibliothèque MFC (Microsoft Foundation Class) définit une classe spéciale (non documentée) dérivée de la [classe CDC](reference/cdc-class.md), appelée `CPreviewDC` . Tous les objets `CDC` contiennent deux contextes de périphérique, mais ils sont généralement identiques. Dans un `CPreviewDC` objet, ils sont différents : le premier représente l’imprimante simulée et le second représente l’écran sur lequel la sortie est réellement affichée.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a> Processus d’aperçu avant impression

Quand l’utilisateur sélectionne la commande Aperçu avant impression dans le menu **fichier** , l’infrastructure crée un `CPreviewDC` objet. Chaque fois que votre application effectue une opération définissant une caractéristique du contexte de l'imprimante, le framework exécute également une opération semblable dans le contexte de périphérique. Par exemple, si votre application sélectionne une police pour l'impression, le framework sélectionne une police pour l'écran qui simule la police d'imprimante. Chaque fois que votre application envoie la sortie vers l'imprimante, le framework envoie à la place la sortie à l'écran.

L'aperçu avant impression diffère également de l'impression dans l'ordre de plan dans lequel chacun dessine les pages d'un document. Lors de l'impression, le framework suit une boucle continue d'impression jusqu'à ce qu'une certaine plage de pages ait été affichée. Pendant l'aperçu avant impression, une ou deux pages sont affichées à tout moment, puis l'application attend ; aucune page ne s'affiche jusqu'à ce que l'utilisateur réponde. Pendant l’aperçu avant impression, l’application doit également répondre aux messages de WM_PAINT, comme c’est le cas lors de l’affichage d’écran ordinaire.

La fonction [CView :: OnPreparePrinting](reference/cview-class.md#onprepareprinting) est appelée quand le mode aperçu est appelé, de la même manière qu’au début d’un travail d’impression. La structure de l' [CPrintInfo](reference/cprintinfo-structure.md) qui est passée à la fonction contient plusieurs membres dont vous pouvez définir des valeurs pour ajuster certaines caractéristiques de l’opération d’aperçu avant impression. Par exemple, vous pouvez définir le membre *m_nNumPreviewPages* pour spécifier si vous souhaitez afficher un aperçu du document en mode une ou deux pages.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a> Modification de l’aperçu avant impression

Vous pouvez facilement modifier le comportement et l'affichage de l'aperçu avant impression de plusieurs façons. Par exemple, vous pouvez, entre autres choses :

- Amener l'aperçu avant impression à afficher une barre de défilement pour un accès aisé à toute page du document.

- Amener l'aperçu avant impression à maintenir la position de l'utilisateur dans le document en commençant son affichage par la page actuelle.

- Amener l'exécution de différentes initialisations pour l'aperçu avant impression et l'impression.

- Amener l'aperçu avant impression à afficher des numéros de page dans vos propres formats.

Si vous connaissez le délai d'attente du document et appelez `SetMaxPage` avec la valeur appropriée, le framework peut utiliser ces informations en mode aperçu ainsi que lors de l'impression. Une fois que le framework connaît la longueur du document, elle peut fournir à la fenêtre d'aperçu une barre de défilement, ce qui permet à l'utilisateur de passer d'une page à une autre dans les deux sens au sein du document en mode aperçu. Si vous n'avez pas défini la longueur du document, le framework ne peut pas placer la zone de défilement pour indiquer la position actuelle, le framework n'ajoute pas de barre de défilement. Dans ce cas, l'utilisateur doit utiliser les boutons de page suivante et de page précédente dans la barre de contrôle de la fenêtre d'aperçu pour naviguer dans le document.

Pour l’aperçu avant impression, il peut s’avérer utile d’attribuer une valeur au membre *m_nCurPage* de `CPrintInfo` , même si vous ne le faites jamais pour une impression ordinaire. Lors de l'impression ordinaire, ce membre fournit les informations de le framework à votre classe d'affichage. Voici comment le framework indique à la vue quelle page doit être imprimée.

En revanche, lorsque le mode aperçu avant impression est démarré, le membre *m_nCurPage* transporte des informations dans la direction opposée : de la vue à l’infrastructure. Le framework utilise la valeur de ce membre pour déterminer si la page doit d'abord afficher un aperçu. La valeur par défaut de ce membre est 1, la première page du document s'affiche initialement. Vous pouvez remplacer `OnPreparePrinting` pour affecter à ce membre le numéro de la page affichée lorsque la commande aperçu avant impression a été appelée. De cette manière, l'application gère la position actuelle de l'utilisateur lors du passage du mode d'affichage normale au mode d'aperçu avant impression.

Parfois, vous pouvez souhaiter que `OnPreparePrinting` effectue différentes initialisations selon qu'il est appelé pour un travail d'impression ou pour l'aperçu avant impression. Vous pouvez le déterminer en examinant la variable membre *m_bPreview* dans la `CPrintInfo` structure. Ce membre a la valeur **true** lorsque l’aperçu avant impression est appelé.

La `CPrintInfo` structure contient également un membre nommé *m_strPageDesc*, qui est utilisé pour mettre en forme les chaînes affichées en bas de l’écran en mode page unique et en mode plusieurs pages. Par défaut, ces chaînes se présentent sous la forme « page *n*» et « pages *n*  -  *m*», mais vous pouvez modifier les *m_strPageDesc* à partir de `OnPreparePrinting` et définir les chaînes sur un nom plus élaboré. Pour plus d’informations, consultez [CPrintInfo, structure](reference/cprintinfo-structure.md) dans la *référence MFC* .

## <a name="see-also"></a>Voir aussi

[Impression et aperçu avant impression](printing-and-print-preview.md)<br/>
[Impression](printing.md)<br/>
[CView, classe](reference/cview-class.md)<br/>
[Classe CDC](reference/cdc-class.md)
