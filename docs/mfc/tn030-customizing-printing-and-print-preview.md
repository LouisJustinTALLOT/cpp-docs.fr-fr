---
title: 'TN030 : Personnalisation de l’impression et Aperçu avant impression | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.print
dev_langs:
- C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 208d179cb8131a690c0ca842f392c934b4386549
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951303"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030 : personnalisation de l'impression et de l'aperçu avant impression
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit le processus de personnalisation de l’impression et Aperçu avant impression et les besoins des routines de rappel utilisées dans `CView` et les routines de rappel et les fonctions membres de `CPreviewView`.  
  
## <a name="the-problem"></a>Le problème  
 MFC fournit une solution complète pour la plupart de l’impression et Aperçu avant impression doit. Dans la plupart des cas, peu de code supplémentaire est nécessaire d’avoir une vue en mesure de l’impression et aperçu. Toutefois, pour optimiser l’impression des méthodes qui requièrent des efforts considérables part du développeur, et certaines applications ont besoin ajouter des éléments d’interface utilisateur spécifique pour le mode Aperçu avant impression.  
  
## <a name="efficient-printing"></a>Impression efficace  
 Lorsqu’une application MFC est imprimée à l’aide des méthodes standard, Windows dirige tous les appels de sortie graphique GDI (Device Interface) pour un métafichier en mémoire. Lorsque `EndPage` est appelée, Windows lit le métafichier une fois pour chaque bande physique nécessitant l’imprimante pour imprimer une page. Pendant le rendu de ce type, GDI demande fréquemment la procédure d’abandon pour déterminer si elle doit continuer. En général, la procédure d’abandon autorise les messages doivent être traités afin que l’utilisateur peut annuler le travail d’impression à l’aide d’une boîte de dialogue d’impression.  
  
 Malheureusement, cela peut ralentir le processus d’impression. Si l’impression dans votre application doit être supérieure à ce que peut être obtenue à l’aide de la technique standard, vous devez implémenter des bandes manuelle.  
  
## <a name="print-banding"></a>Imprimer des bandes  
 Pour des bandes manuellement, vous devez re implémenter la boucle d’impression telles que `OnPrint` est appelée plusieurs fois par page (une fois par bande). La boucle d’impression est implémentée dans le `OnFilePrint` dans viewprnt.cpp (fonction). Dans votre `CView`-classe dérivée, vous surchargez cette fonction afin que l’entrée de mappage de message pour la gestion de la commande d’impression appelle votre fonction d’impression. Copie le `OnFilePrint` routine et modification de la boucle d’impression pour implémenter des bandes. Vous serez probablement que vous souhaitez également passer le rectangle de regroupement pour vos fonctions d’impression, afin que vous pouvez optimiser le dessin en fonction de la section de la page en cours d’impression.  
  
 En second lieu, vous devez fréquemment appeler `QueryAbort` lors du dessin de la bande. Sinon, la procédure d’abandon n’est pas appelée et l’utilisateur sera impossible d’annuler le travail d’impression.  
  
## <a name="print-preview-electronic-paper-with-user-interface"></a>Aperçu avant impression : Le livre électronique avec Interface utilisateur  
 Aperçu avant impression, essaie fondamentalement activer l’affichage dans une émulation d’une imprimante. Par défaut, la zone cliente de la fenêtre principale est utilisée pour afficher une ou deux pages entièrement dans la fenêtre. L’utilisateur est en mesure de faire un zoom avant sur une zone de la page pour voir plus de détails. Avec prise en charge supplémentaire, l’utilisateur peut même être autorisé à modifier le document en mode Aperçu.  
  
## <a name="customizing-print-preview"></a>Personnalisation de l’aperçu avant impression  
 Cette note ne traite qu’un aspect de la modification de l’aperçu avant impression : ajout d’une interface utilisateur en mode Aperçu. Autres modifications sont possibles, mais ces modifications hors de l’étendue de cette discussion.  
  
## <a name="to-add-ui-to-the-preview-mode"></a>Pour ajouter une interface utilisateur pour le mode Aperçu  
  
1.  Dérivez une classe de vue de `CPreviewView`.  
  
2.  Ajouter des gestionnaires de commandes pour les aspects de l’interface utilisateur que vous le souhaitez.  
  
3.  Si vous ajoutez des aspects visuels à l’affichage, substituez `OnDraw` et exécuter votre dessin après l’appel `CPreviewView::OnDraw`.  
  
## <a name="onfileprintpreview"></a>OnFilePrintPreview  
 Il s’agit du Gestionnaire de commandes pour l’aperçu avant impression. Son implémentation par défaut est la suivante :  
  
```  
void CView::OnFilePrintPreview()  
{ *// In derived classes,
    implement special window handling here *// Be sure to Unhook Frame Window close if hooked.  
 *// must not create this on the frame. Must outlive this function  
    CPrintPreviewState* pState = new CPrintPreviewState;  
 
    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR,
    this,  
    RUNTIME_CLASS(CPreviewView),
    pState))  
 { *// In derived classes,
    reverse special window handling *// here for Preview failure case  
 
    TRACE0("Error: DoPrintPreview failed");

    AfxMessageBox(AFX_IDP_COMMAND_FAILURE);

 delete pState;      // preview failed to initialize, *// delete State now  
 }  
}  
```  
  
 `DoPrintPreview` allez masquer le volet principal de l’application. Barres de contrôles, tels que la barre d’état, peuvent être conservées en les spécifiant dans la pState ->*dwStates* membre (c’est un masque de bits et les bits pour les barres de contrôles individuels sont définis par AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR)). La fenêtre pState ->*nIDMainPane* est la fenêtre qui est automatiquement masquée et reshown. `DoPrintPreview` Crée une barre de boutons pour l’interface utilisateur d’aperçu standard. Si la gestion de fenêtre spéciale est nécessaire, par exemple, masquer ou afficher d’autres fenêtres, ce qui doivent être effectuées avant `DoPrintPreview` est appelée.  
  
 Par défaut, une fois l’aperçu avant impression, il retourne les barres de contrôles à leur état d’origine et le volet principal visible. Si un traitement spécial est nécessaire, il doit être effectuée dans une substitution de `EndPrintPreview`. Si `DoPrintPreview` échoue, fournissent également un traitement spécial.  
  
 DoPrintPreview est appelée avec :  
  
-   L’ID de ressource du modèle de boîte de dialogue de la barre d’outils de l’aperçu.  
  
-   Pointeur vers la vue pour effectuer l’impression pour l’aperçu avant impression.  
  
-   La classe d’exécution de la classe d’affichage de l’aperçu. Cela sera créé dynamiquement dans DoPrintPreview.  
  
-   Le pointeur CPrintPreviewState. Notez que la structure CPrintPreviewState (ou la structure dérivée si l’application a besoin de plus d’état conservé) doit *pas* être créé sur le frame. DoPrintPreview est non modale et cette structure doit survivent jusqu'à ce que EndPrintPreview est appelée.  
  
    > [!NOTE]
    >  Si une vue distincte ou une classe d’affichage est nécessaire pour la prise en charge l’impression, un pointeur vers cet objet doit être passé comme deuxième paramètre.  
  
## <a name="endprintpreview"></a>EndPrintPreview  
 Cela est appelé pour terminer le mode Aperçu avant impression. Il est souvent souhaitable de passer à la page dans le document qui a été a affiché en aperçu avant impression. `EndPrintPreview` est la possibilité de l’application pour ce faire. Le pInfo ->*m_nCurPage* membre est la page dernier affichage (à l’extrême gauche si deux pages étaient affichés) et le pointeur est un Conseil au concernant où l’utilisateur a été intéressé par sur la page. Étant donné que la structure de vue de l’application est inconnue du Framework, vous devez fournir le code pour déplacer vers le point choisi.  
  
 Vous devez effectuer la plupart des actions avant d’appeler `CView::EndPrintPreview`. Cet appel annule les effets de `DoPrintPreview` et supprime pInfo pView et contrôleur de domaine principal.  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC,
    pInfo,
    point,
    pView);
```  
  
## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 Cela doit être mappé pour l’élément de menu de configuration de l’impression. Dans la plupart des cas, il n’est pas nécessaire de remplacer l’implémentation.  
  
## <a name="page-nomenclature"></a>Page Nomenclature  
 Un autre problème est que des numéros de page et l’ordre. Pour les applications de type de traitement de texte simple, il s’agit d’un problème simple. La plupart des systèmes d’aperçu avant impression partent du principe que chaque page imprimée correspond à une page dans le document.  
  
 En essayant de fournir une solution généralisée, il existe plusieurs éléments à prendre en compte. Imaginez un système de CAO. L’utilisateur a un dessin qui couvre plusieurs feuilles E-taille. Sur une taille de E (ou à l’échelle un plus petit) traceur, la numérotation des pages serait comme dans le cas simple. Mais comme sur une imprimante laser, impression des pages de taille A 16 par feuille, ce qui l’aperçu avant impression une « page »  
  
 Comme l’indique le paragraphe d’introduction, aperçu avant impression agit comme une imprimante. Par conséquent, il pourra voir ce que serait sortent de l’imprimante sélectionnée. C’est à la vue pour déterminer quelle image est imprimée sur chaque page.  
  
 La chaîne de description de page dans le `CPrintInfo` structure fournit un moyen d’afficher le numéro de page à l’utilisateur si elle peut être représentée comme un nombre par page (comme dans « Page 1 » ou « Pages 1-2 »). Cette chaîne est utilisée par l’implémentation par défaut de `CPreviewView::OnDisplayPageNumber`. Si un autre affichage est nécessaire, un peut substituer cette fonction virtuelle pour fournir, par exemple, « Feuille1, Sections A, B ».  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

