---
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
ms.openlocfilehash: 79a71a4660cd49f85726d730c9fad0b2f10f83bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300425"
---
# <a name="control-classes"></a>Classes de contrôle

Classes de contrôle encapsulent une grande variété de contrôles Windows standard, comprise entre les contrôles de texte statique et contrôles d’arborescence. En outre, MFC fournit de nouveaux contrôles, notamment des boutons avec des barres de bitmaps et de contrôle.

Les contrôles dont les noms classe se terminent par «**Ctrl**» ont été apportées dans Windows 95 et Windows NT version 3.51.

## <a name="static-display-controls"></a>Contrôles d’affichage statique

[CStatic](../mfc/reference/cstatic-class.md)<br/>
Une fenêtre d’affichage statique. Contrôles statiques servent à étiqueter, zone ou séparer des autres contrôles dans une fenêtre ou boîte de dialogue. Ils peuvent également afficher des images graphiques plutôt que de texte ou d’une zone.

## <a name="text-controls"></a>Contrôles de texte

[CEdit](../mfc/reference/cedit-class.md)<br/>
Une fenêtre de contrôle de texte modifiable. Modifier les contrôles sont utilisés pour accepter l’entrée textuelle de l’utilisateur.

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
Prend en charge une zone d’édition pour la manipulation d’une adresse IP (Internet Protocol).

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
Un contrôle dans lequel l’utilisateur peut entrer et modifier du texte. Contrairement au contrôle encapsulé dans `CEdit`, un contrôle rich edit prend en charge les caractères et la mise en forme et les objets OLE.

## <a name="controls-that-represent-numbers"></a>Contrôles qui représentent des nombres

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
Un contrôle contenant un curseur, l’utilisateur déplace pour sélectionner une valeur ou un ensemble de valeurs.

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
Une paire de boutons de direction, l’utilisateur peut cliquer pour incrémenter ou décrémenter une valeur.

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
Affiche un rectangle qui se remplit progressivement de gauche à droite pour indiquer la progression d’une opération.

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
Une fenêtre de contrôle de barre de défilement. La classe fournit les fonctionnalités d’une barre de défilement pour une utilisation en tant que contrôle dans une fenêtre, par le biais duquel l’utilisateur peut spécifier une position dans une plage ou la boîte de dialogue.

## <a name="buttons"></a>Boutons

[CButton](../mfc/reference/cbutton-class.md)<br/>
Une fenêtre de contrôle de bouton. La classe fournit une interface de programmation pour un bouton de commande, une case à cocher ou une case d’option dans une fenêtre ou boîte de dialogue.

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
Bouton avec une image bitmap plutôt que d’une légende de texte.

## <a name="lists"></a>Listes

[CListBox](../mfc/reference/clistbox-class.md)<br/>
Une fenêtre de contrôle de zone de liste. Une zone de liste affiche une liste d’éléments que l’utilisateur peut afficher et sélectionner.

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
Fournit les fonctionnalités d’une zone de liste Windows ; permet à l’utilisateur déplacer des éléments de liste, telle que les littéraux de chaîne et les noms de fichiers, au sein de la zone de liste. Avec cette fonctionnalité, les zones de liste sont utiles pour une liste d’éléments dans un ordre autre qu’alphabétique, tel qu’inclure des fichiers ou des chemins d’accès dans un projet.

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
Une fenêtre de contrôle de zone de liste déroulante. Une zone de liste déroulante constitué d’un contrôle d’édition et d’une zone de liste.

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
Étend le contrôle de zone de liste déroulante en fournissant la prise en charge des listes d'images.

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
Affiche une liste d’éléments avec des cases à cocher, l’utilisateur peut vérifier ou effacer, en regard de chaque élément.

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
Affiche une collection d’éléments, chacun d'entre eux comprenant une icône et une étiquette, d’une manière similaire dans le volet de droite de l’Explorateur de fichiers.

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
Affiche une liste hiérarchique des icônes et des étiquettes organisés de manière similaire dans le volet de gauche de l’Explorateur de fichiers.

## <a name="toolbars-and-status-bars"></a>Barres d’outils et des barres d’état

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle commun de barre d'outils Windows. MFC la plupart des programmes utilisent [CToolBar](../mfc/reference/ctoolbar-class.md) au lieu de cette classe.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Une fenêtre horizontale, généralement divisée en volets, dans laquelle une application peut afficher des informations d’état. MFC la plupart des programmes utilisent [CStatusBar](../mfc/reference/cstatusbar-class.md) au lieu de cette classe.

## <a name="miscellaneous-controls"></a>Divers contrôles

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
Affiche un clip vidéo simple.

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Une petite fenêtre contextuelle qui affiche une seule ligne de texte qui décrit l’objectif d’un outil dans une application.

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
Prend en charge un contrôle d’édition étendues, ou d’un contrôle d’interface de calendrier simple, qui permet à un utilisateur de choisir une date spécifique ou une valeur d’heure.

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
Affiche les titres ou des étiquettes pour les colonnes.

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
Prend en charge un contrôle d’interface de calendrier simple qui permet à un utilisateur de sélectionner une date.

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
Un contrôle avec onglets sur lequel l’utilisateur peut cliquer, analogues aux intercalaires d’un bloc-notes.

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
Permet à l’utilisateur créer une combinaison de touches à chaud, l’utilisateur peut appuyer sur pour effectuer une action rapidement.

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
Restitue le texte marqué et lance des applications appropriées lorsque l’utilisateur clique sur le lien incorporé.

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
Fournit les fonctionnalités du contrôle ActiveX WebBrowser dans une fenêtre MFC.

## <a name="related-classes"></a>Classes connexes

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Fournit les fonctionnalités de la liste d’images Windows. Listes d’images sont utilisées avec les contrôles de liste et contrôles d’arborescence. Ils peuvent également être utilisés pour stocker et archiver un ensemble de bitmaps de même taille.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La classe de base pour toutes les vues associées aux contrôles de Windows. Les vues basées sur les contrôles sont décrits ci-dessous.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Contrôle d’édition une vue qui contient un standard de Windows.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Contrôle d’édition une vue qui contient un riche de Windows.

[CListView](../mfc/reference/clistview-class.md)<br/>
Une vue qui contient un contrôle de liste Windows.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Une vue qui contient un contrôle d’arborescence Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
