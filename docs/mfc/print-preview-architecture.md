---
title: Architecture de l’aperçu avant impression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5c3aee94f5c3a53f7e31c99a7c2edbfd624e8b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931776"
---
# <a name="print-preview-architecture"></a>Architecture de l'aperçu avant impression
Cet article explique comment le framework MFC implémente la fonctionnalité d'aperçu avant impression. Les sujets abordés sont les suivantes :  
  
-   [Processus d’aperçu avant impression](#_core_the_print_preview_process)  
  
-   [Modification de l’aperçu avant impression](#_core_modifying_print_preview)  
  
 L'aperçu avant impression est quelque peu différent de l'écran et de l'impression puisque, au lieu d'ajouter directement une image sur un périphérique, l'application doit simuler l'imprimante à l'aide de l'écran. Pour ce faire, la bibliothèque Microsoft Foundation Class définit une classe de (non documentée) spéciale dérivée [CDC (classe)](../mfc/reference/cdc-class.md), appelé `CPreviewDC`. Tous les objets `CDC` contiennent deux contextes de périphérique, mais ils sont généralement identiques. Dans un `CPreviewDC` de l’objet, ils sont différents : le premier représente l’imprimante et le second représente l’écran sur lequel sortie est réellement affichée.  
  
##  <a name="_core_the_print_preview_process"></a> Le processus d’aperçu avant impression  
 Lorsque l’utilisateur sélectionne la commande Aperçu avant impression à partir de la **fichier** menu, l’infrastructure crée un `CPreviewDC` objet. Chaque fois que votre application effectue une opération définissant une caractéristique du contexte de l'imprimante, le framework exécute également une opération semblable dans le contexte de périphérique. Par exemple, si votre application sélectionne une police pour l'impression, le framework sélectionne une police pour l'écran qui simule la police d'imprimante. Chaque fois que votre application envoie la sortie vers l'imprimante, le framework envoie à la place la sortie à l'écran.  
  
 L'aperçu avant impression diffère également de l'impression dans l'ordre de plan dans lequel chacun dessine les pages d'un document. Lors de l'impression, le framework suit une boucle continue d'impression jusqu'à ce qu'une certaine plage de pages ait été affichée. Pendant l'aperçu avant impression, une ou deux pages sont affichées à tout moment, puis l'application attend ; aucune page ne s'affiche jusqu'à ce que l'utilisateur réponde. Au cours de l’aperçu avant impression, l’application doit également répondre aux messages WM_PAINT, comme il le fait pendant l’affichage à l’écran ordinaire.  
  
 Le [comme CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) fonction est appelée lorsque le mode aperçu est appelé, comme au début d’un travail d’impression. Le [CPrintInfo (Structure)](../mfc/reference/cprintinfo-structure.md) structure passée à la fonction contient plusieurs membres dont les valeurs que vous pouvez définir pour modifier certaines caractéristiques de l’opération d’aperçu avant impression. Par exemple, vous pouvez définir le *m_nNumPreviewPages* membre pour spécifier si vous souhaitez afficher un aperçu du document en mode une page ou deux pages.  
  
##  <a name="_core_modifying_print_preview"></a> Modification de l’aperçu avant impression  
 Vous pouvez facilement modifier le comportement et l'affichage de l'aperçu avant impression de plusieurs façons. Par exemple, vous pouvez, entre autres choses :  
  
-   Amener l'aperçu avant impression à afficher une barre de défilement pour un accès aisé à toute page du document.  
  
-   Amener l'aperçu avant impression à maintenir la position de l'utilisateur dans le document en commençant son affichage par la page actuelle.  
  
-   Amener l'exécution de différentes initialisations pour l'aperçu avant impression et l'impression.  
  
-   Amener l'aperçu avant impression à afficher des numéros de page dans vos propres formats.  
  
 Si vous connaissez le délai d'attente du document et appelez `SetMaxPage` avec la valeur appropriée, le framework peut utiliser ces informations en mode aperçu ainsi que lors de l'impression. Une fois que le framework connaît la longueur du document, elle peut fournir à la fenêtre d'aperçu une barre de défilement, ce qui permet à l'utilisateur de passer d'une page à une autre dans les deux sens au sein du document en mode aperçu. Si vous n'avez pas défini la longueur du document, le framework ne peut pas placer la zone de défilement pour indiquer la position actuelle, le framework n'ajoute pas de barre de défilement. Dans ce cas, l'utilisateur doit utiliser les boutons de page suivante et de page précédente dans la barre de contrôle de la fenêtre d'aperçu pour naviguer dans le document.  
  
 Pour l’aperçu avant impression, il peut s’avérer utile pour affecter une valeur à la *m_nCurPage* membre `CPrintInfo`, même si vous le feriez jamais pour une impression ordinaire. Lors de l'impression ordinaire, ce membre fournit les informations de le framework à votre classe d'affichage. Voici comment le framework indique à la vue quelle page doit être imprimée.  
  
 En revanche, lorsque le mode Aperçu avant impression démarre, le *m_nCurPage* membre transmet les informations dans le sens inverse : de la vue à l’infrastructure. Le framework utilise la valeur de ce membre pour déterminer si la page doit d'abord afficher un aperçu. La valeur par défaut de ce membre est 1, la première page du document s'affiche initialement. Vous pouvez remplacer `OnPreparePrinting` pour affecter à ce membre le numéro de la page affichée lorsque la commande aperçu avant impression a été appelée. De cette manière, l'application gère la position actuelle de l'utilisateur lors du passage du mode d'affichage normale au mode d'aperçu avant impression.  
  
 Parfois, vous pouvez souhaiter que `OnPreparePrinting` effectue différentes initialisations selon qu'il est appelé pour un travail d'impression ou pour l'aperçu avant impression. Vous pouvez le déterminer en examinant le *m_bPreview* variable de membre dans le `CPrintInfo` structure. Ce membre a la valeur **TRUE** lorsque l’aperçu avant impression est appelé.  
  
 Le `CPrintInfo` structure contient également un membre nommé *m_strPageDesc*, qui est utilisé pour mettre en forme les chaînes affichées en bas de l’écran dans les modes page unique et plusieurs pages. Par défaut, ces chaînes sont sous la forme « Page *n*» et « Pages *n* - *m*, », mais vous pouvez modifier *m_strPageDesc* à partir de dans `OnPreparePrinting` et définir les chaînes de façon plus élaborée. Consultez [CPrintInfo (Structure)](../mfc/reference/cprintinfo-structure.md) dans les *référence MFC* pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Impression et Aperçu avant impression](../mfc/printing-and-print-preview.md)   
 [Impression](../mfc/printing.md)   
 [CView (classe)](../mfc/reference/cview-class.md)   
 [CDC, classe](../mfc/reference/cdc-class.md)
