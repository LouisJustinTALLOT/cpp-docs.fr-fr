---
description: En savoir plus sur les classes de contrôle
title: Classes de contrôle
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: eb0bee6d865867a052b5f49408bdaa1b70da343f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310120"
---
# <a name="control-classes"></a>Classes de contrôle

Les classes de contrôle encapsulent un large éventail de contrôles Windows standard, allant des contrôles de texte statique aux contrôles d’arborescence. En outre, MFC fournit de nouveaux contrôles, notamment des boutons avec des bitmaps et des barres de contrôles.

Les contrôles dont les noms de classe se terminent par «**CTRL**» étaient nouveaux dans Windows 95 et Windows NT version 3,51.

## <a name="static-display-controls"></a>Contrôles d’affichage statiques

[CStatic](reference/cstatic-class.md)<br/>
Fenêtre d’affichage statique. Les contrôles statiques sont utilisés pour étiqueter, zone ou séparer d’autres contrôles dans une boîte de dialogue ou une fenêtre. Ils peuvent également afficher des images graphiques plutôt que du texte ou une zone.

## <a name="text-controls"></a>Contrôles de texte

[CEdit](reference/cedit-class.md)<br/>
Fenêtre de contrôle de texte modifiable. Les contrôles d’édition sont utilisés pour accepter les entrées textuelles de l’utilisateur.

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
Prend en charge une zone d’édition pour la manipulation d’une adresse IP (Internet Protocol).

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
Contrôle dans lequel l’utilisateur peut entrer et modifier du texte. Contrairement au contrôle encapsulé dans `CEdit` , un contrôle RichEdit prend en charge la mise en forme des caractères et des paragraphes, ainsi que les objets OLE.

## <a name="controls-that-represent-numbers"></a>Contrôles qui représentent des nombres

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
Contrôle contenant un curseur, que l’utilisateur déplace pour sélectionner une valeur ou un ensemble de valeurs.

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
Paire de boutons fléchés sur lesquels l’utilisateur peut cliquer pour incrémenter ou décrémenter une valeur.

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
Affiche un rectangle qui est progressivement rempli de gauche à droite pour indiquer la progression d’une opération.

[CScrollBar](reference/cscrollbar-class.md)<br/>
Fenêtre de contrôle de barre de défilement. La classe fournit les fonctionnalités d’une barre de défilement, à utiliser comme contrôle dans une boîte de dialogue ou une fenêtre, par l’intermédiaire de laquelle l’utilisateur peut spécifier une position dans une plage.

## <a name="buttons"></a>Boutons

[CButton](reference/cbutton-class.md)<br/>
Fenêtre de contrôle de bouton. La classe fournit une interface de programmation pour un bouton de commande, une case à cocher ou une case d’option dans une boîte de dialogue ou une fenêtre.

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
Bouton avec une image bitmap plutôt qu’une légende de texte.

## <a name="lists"></a>Listes

[CListBox](reference/clistbox-class.md)<br/>
Fenêtre de contrôle de zone de liste. Une zone de liste affiche la liste des éléments que l’utilisateur peut afficher et sélectionner.

[CDragListBox](reference/cdraglistbox-class.md)<br/>
Fournit les fonctionnalités d’une zone de liste Windows ; permet à l’utilisateur de déplacer des éléments de zone de liste, tels que des noms de fichiers et des littéraux de chaîne, dans la zone de liste. Les zones de liste avec cette fonctionnalité sont utiles pour une liste d’éléments dans un ordre autre que l’ordre alphabétique, par exemple inclure des chemins d’accès ou des fichiers dans un projet.

[CComboBox](reference/ccombobox-class.md)<br/>
Fenêtre de contrôle de zone de liste déroulante. Une zone de liste déroulante se compose d’un contrôle d’édition et d’une zone de liste.

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
Étend le contrôle de zone de liste déroulante en fournissant la prise en charge des listes d'images.

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
Affiche une liste d’éléments avec des cases à cocher que l’utilisateur peut activer ou désactiver, en regard de chaque élément.

[CListCtrl](reference/clistctrl-class.md)<br/>
Affiche une collection d’éléments, chacun composé d’une icône et d’une étiquette, d’une manière similaire au volet droit de l’Explorateur de fichiers.

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
Affiche une liste hiérarchique des icônes et des étiquettes organisées de manière similaire au volet gauche de l’Explorateur de fichiers.

## <a name="toolbars-and-status-bars"></a>Barres d’outils et barres d’État

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle commun de barre d'outils Windows. La plupart des programmes MFC utilisent [CToolBar](reference/ctoolbar-class.md) au lieu de cette classe.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Fenêtre horizontale, généralement divisée en volets, dans laquelle une application peut afficher des informations d’État. La plupart des programmes MFC utilisent [CStatusBar](reference/cstatusbar-class.md) à la place de cette classe.

## <a name="miscellaneous-controls"></a>Contrôles divers

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
Affiche un clip vidéo simple.

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Petite fenêtre contextuelle qui affiche une seule ligne de texte décrivant l’objectif d’un outil dans une application.

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
Prend en charge un contrôle d’édition étendu ou un simple contrôle d’interface de calendrier, qui permet à un utilisateur de choisir une valeur de date ou d’heure spécifique.

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
Affiche des titres ou des étiquettes pour les colonnes.

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
Prend en charge un contrôle d’interface de calendrier simple qui permet à un utilisateur de sélectionner une date.

[CTabCtrl](reference/ctabctrl-class.md)<br/>
Contrôle avec des onglets sur lesquels l’utilisateur peut cliquer, analogue aux séparateurs d’un bloc-notes.

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
Permet à l’utilisateur de créer une combinaison de touches d’accès rapide, sur laquelle l’utilisateur peut appuyer pour effectuer une action rapidement.

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
Restitue le texte marqué et lance les applications appropriées lorsque l’utilisateur clique sur le lien incorporé.

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle ActiveX WebBrowser dans une fenêtre MFC.

## <a name="related-classes"></a>Classes connexes

[CImageList](reference/cimagelist-class.md)<br/>
Fournit les fonctionnalités de la liste d’images Windows. Les listes d’images sont utilisées avec les contrôles de liste et les contrôles d’arborescence. Ils peuvent également être utilisés pour stocker et archiver un ensemble de bitmaps de même taille.

[CCtrlView](reference/cctrlview-class.md)<br/>
Classe de base pour toutes les vues associées aux contrôles Windows. Les vues basées sur les contrôles sont décrites ci-dessous.

[CEditView](reference/ceditview-class.md)<br/>
Vue qui contient un contrôle d’édition Windows standard.

[CRichEditView](reference/cricheditview-class.md)<br/>
Vue qui contient un contrôle Rich Edit Windows.

[CListView](reference/clistview-class.md)<br/>
Vue qui contient un contrôle de liste Windows.

[CTreeView](reference/ctreeview-class.md)<br/>
Vue qui contient un contrôle d’arborescence Windows.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
