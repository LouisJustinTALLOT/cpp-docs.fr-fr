---
description: 'En savoir plus sur : TN030 : personnalisation de l’impression et de l’aperçu avant impression'
title: "TN030 : personnalisation de l'impression et de l'aperçu avant impression"
ms.date: 06/28/2018
f1_keywords:
- vc.print
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
ms.openlocfilehash: 6fc0571b908f85b24b8a0752a00842077d537dce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215610"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030 : personnalisation de l'impression et de l'aperçu avant impression

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit le processus de personnalisation de l’impression et de l’aperçu avant impression, et décrit les objectifs des routines de rappel utilisées dans `CView` et les routines de rappel et les fonctions membres de `CPreviewView` .

## <a name="the-problem"></a>Le problème

MFC fournit une solution complète pour la plupart des besoins en matière d’impression et d’aperçu avant impression. Dans la plupart des cas, il est nécessaire d’avoir un peu de code supplémentaire pour pouvoir imprimer et afficher un aperçu. Toutefois, il existe des moyens d’optimiser l’impression qui nécessitent un effort important de la part du développeur, et certaines applications doivent ajouter des éléments d’interface utilisateur spécifiques au mode aperçu avant impression.

## <a name="efficient-printing"></a>Impression efficace

Quand une application MFC imprime à l’aide des méthodes standard, Windows dirige tous les appels de sortie GDI (Graphics Device Interface) vers un métafichier en mémoire. Lorsque `EndPage` est appelé, Windows lit le métafichier une fois pour chaque bande physique requise par l’imprimante pour imprimer une page. Pendant ce rendu, GDI interroge fréquemment la procédure Abort pour déterminer s’il doit continuer. En règle générale, la procédure d’abandon autorise le traitement des messages afin que l’utilisateur puisse abandonner le travail d’impression à l’aide d’une boîte de dialogue d’impression.

Malheureusement, cela peut ralentir le processus d’impression. Si l’impression dans votre application doit être plus rapide que ce qui est possible à l’aide de la technique standard, vous devez implémenter la mise en bande manuelle.

## <a name="print-banding"></a>Impression des bandes

Pour créer manuellement une bande, vous devez implémenter à nouveau la boucle d’impression, qui `OnPrint` est appelée plusieurs fois par page (une fois par bande). La boucle d’impression est implémentée dans la `OnFilePrint` fonction dans viewprnt. cpp. Dans votre `CView` classe dérivée de, vous surchargez cette fonction afin que l’entrée de la table des messages pour la gestion de la commande Print appelle votre fonction Print. Copiez la `OnFilePrint` routine et modifiez la boucle d’impression pour implémenter les bandes. Vous souhaiterez probablement également passer le rectangle de bande à vos fonctions d’impression afin de pouvoir optimiser le dessin en fonction de la section de la page en cours d’impression.

Deuxièmement, vous devez fréquemment appeler `QueryAbort` tout en traçant la bande. Dans le cas contraire, la procédure d’abandon n’est pas appelée et l’utilisateur ne peut pas annuler le travail d’impression.

## <a name="print-preview-electronic-paper-with-user-interface"></a>Aperçu avant impression : papier électronique avec interface utilisateur

En résumé, l’aperçu avant impression tente de transformer l’affichage en émulation d’une imprimante. Par défaut, la zone cliente de la fenêtre principale est utilisée pour afficher une ou deux pages entièrement dans la fenêtre. L’utilisateur peut effectuer un zoom avant sur une zone de la page pour le voir plus en détail. Avec une prise en charge supplémentaire, l’utilisateur peut même être autorisé à modifier le document en mode aperçu.

## <a name="customizing-print-preview"></a>Personnalisation de l’aperçu avant impression

Cette note concerne uniquement un aspect de la modification de l’aperçu avant impression : l’ajout de l’interface utilisateur au mode aperçu. D’autres modifications sont possibles, mais ces modifications ne sont pas abordées dans le cadre de cette discussion.

## <a name="to-add-ui-to-the-preview-mode"></a>Pour ajouter l’interface utilisateur au mode aperçu

1. Dérivez une classe d’affichage de `CPreviewView` .

2. Ajoutez des gestionnaires de commandes pour les aspects de l’interface utilisateur souhaités.

3. Si vous ajoutez des aspects visuels à l’affichage, remplacez `OnDraw` et effectuez votre dessin après avoir appelé `CPreviewView::OnDraw` .

## <a name="onfileprintpreview"></a>OnFilePrintPreview

Il s’agit du gestionnaire de commandes pour l’aperçu avant impression. Son implémentation par défaut est la suivante :

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` masque le volet principal de l’application. Les barres de contrôles, telles que la barre d’État, peuvent être conservées en les spécifiant dans le membre pState->*dwStates* (il s’agit d’un masque de bits et les bits des barres de contrôle individuelles sont définis par AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR)). La fenêtre pState->*nIDMainPane* est la fenêtre qui est automatiquement masquée et réaffichée. `DoPrintPreview` crée ensuite une barre de boutons pour l’interface utilisateur de l’aperçu standard. Si une gestion spéciale des fenêtres est nécessaire, par exemple pour masquer ou afficher d’autres fenêtres, cette opération doit être effectuée avant l' `DoPrintPreview` appel de.

Par défaut, lorsque l’aperçu avant impression est terminé, il retourne les barres de contrôle à leur état d’origine et le volet principal à afficher. Si une gestion spéciale est nécessaire, elle doit être effectuée dans une substitution de `EndPrintPreview` . En cas d' `DoPrintPreview` échec, fournit également une gestion spéciale.

DoPrintPreview est appelé avec :

- ID de ressource du modèle de boîte de dialogue pour la barre d’outils d’aperçu.

- Pointeur vers la vue pour effectuer l’impression de l’aperçu avant impression.

- Classe Runtime de la classe de vue d’aperçu. Ce sera créé dynamiquement dans DoPrintPreview.

- Pointeur CPrintPreviewState. Notez que la structure CPrintPreviewState (ou la structure dérivée si l’application a besoin d’un État plus préservé) *ne doit pas* être créée sur le frame. DoPrintPreview est non modal et cette structure doit survivre jusqu’à l’appel de EndPrintPreview.

  > [!NOTE]
  > Si une vue ou une classe de vue distincte est nécessaire pour la prise en charge de l’impression, un pointeur vers cet objet doit être passé comme deuxième paramètre.

## <a name="endprintpreview"></a>EndPrintPreview

Cette méthode est appelée pour terminer le mode aperçu avant impression. Il est souvent préférable de passer à la page du document qui a été affiché en mode aperçu avant impression. `EndPrintPreview` est l’occasion pour l’application de le faire. Le membre pInfo->*m_nCurPage* est la page qui a été affichée pour la dernière fois (le plus à gauche si deux pages étaient affichées) et le pointeur est un indicateur qui indique l’emplacement de la page où l’utilisateur était intéressé. Dans la mesure où la structure de la vue de l’application est inconnue de l’infrastructure, vous devez fournir le code pour passer au point choisi.

Vous devez effectuer la plupart des actions avant d’appeler `CView::EndPrintPreview` . Cet appel inverse les effets de `DoPrintPreview` et supprime pview, PDC et pinfo.

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp :: OnFilePrintSetup

Elle doit être mappée pour l’élément de menu Configuration de l’impression. Dans la plupart des cas, il n’est pas nécessaire de substituer l’implémentation.

## <a name="page-nomenclature"></a>Page nomenclature

Autre problème : la numérotation et l’ordre des pages. Pour les applications de type traitement de texte simples, il s’agit d’un problème simple. La plupart des systèmes d’aperçu avant impression supposent que chaque page imprimée correspond à une page dans le document.

Pour fournir une solution généralisée, plusieurs éléments sont à prendre en compte. Imaginez un système CAO. L’utilisateur dispose d’un dessin qui couvre plusieurs feuilles de taille E. Sur un traceur de taille E (ou plus petit, mis à l’échelle), la numérotation des pages est la même que dans le cas simple. Mais sur une imprimante laser, en imprimant 16 pages de taille par feuille, que l’aperçu avant impression considère comme une « page »

Comme l’indique le paragraphe d’introduction, l’aperçu avant impression agit comme une imprimante. Par conséquent, l’utilisateur verra ce qui sortirait de l’imprimante sélectionnée. C’est à la vue de déterminer quelle image est imprimée sur chaque page.

La chaîne de description de page de la `CPrintInfo` structure permet d’afficher le numéro de page à l’utilisateur s’il peut être représenté comme un nombre par page (par exemple, « page 1 » ou « Pages 1-2 »). Cette chaîne est utilisée par l’implémentation par défaut de `CPreviewView::OnDisplayPageNumber` . Si un affichage différent est nécessaire, vous pouvez remplacer cette fonction virtuelle pour fournir, par exemple, « Feuil1, sections A, B ».

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
