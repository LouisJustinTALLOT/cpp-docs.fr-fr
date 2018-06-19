---
title: Classes de contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.control
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffd7b3b7d2eb9db68fd61ac693c65d87b2ee62d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358642"
---
# <a name="control-classes"></a>Classes de contrôle
Classes de contrôle encapsulent une grande variété de contrôles Windows standard comprises entre les contrôles de texte statique et contrôles d’arborescence. En outre, MFC fournit de nouveaux contrôles, y compris les boutons de barres de contrôle et les bitmaps.  
  
 Les contrôles dont les noms classe se terminent par «**Ctrl**« constituaient une nouveauté de Windows 95 et Windows NT version 3.51.  
  
## <a name="static-display-controls"></a>Contrôles d’affichage statique  
 [CStatic](../mfc/reference/cstatic-class.md)  
 Une fenêtre d’affichage statique. Les contrôles statiques sont utilisés pour étiqueter, de zone ou de séparer des autres contrôles dans une fenêtre ou une boîte de dialogue. Ils peuvent également afficher des images graphiques plutôt que de texte ou d’une zone.  
  
## <a name="text-controls"></a>Contrôles de texte  
 [CEdit](../mfc/reference/cedit-class.md)  
 Une fenêtre de contrôle de texte modifiable. Modifier les contrôles sont utilisés pour accepter l’entrée de texte à partir de l’utilisateur.  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 Prend en charge une zone d’édition pour la manipulation d’une adresse IP (Internet Protocol).  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 Un contrôle dans lequel l’utilisateur peut entrer et modifier du texte. Contrairement au contrôle encapsulé dans `CEdit`, un contrôle RichEdit prend en charge les caractères et la mise en forme et les objets OLE.  
  
## <a name="controls-that-represent-numbers"></a>Contrôles qui représentent des nombres  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 Un contrôle contenant un curseur, l’utilisateur passe à une valeur ou un ensemble de valeurs.  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 Une paire de boutons de direction, l’utilisateur peut cliquer pour incrémenter ou décrémenter une valeur.  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 Affiche un rectangle qui se remplit progressivement de gauche à droite pour indiquer la progression d’une opération.  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 Une fenêtre de contrôle de barre de défilement. La classe fournit les fonctionnalités d’une barre de défilement pour une utilisation en tant que contrôle dans une fenêtre, par le biais duquel l’utilisateur peut spécifier une position dans une plage ou une boîte de dialogue.  
  
## <a name="buttons"></a>Boutons  
 [CButton](../mfc/reference/cbutton-class.md)  
 Une fenêtre de contrôle de bouton. La classe fournit une interface de programmation pour un bouton de commande, une case à cocher ou une case d’option dans une fenêtre ou une boîte de dialogue.  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 Bouton avec une image bitmap au lieu d’une légende de texte.  
  
## <a name="lists"></a>Listes  
 [CListBox](../mfc/reference/clistbox-class.md)  
 Une fenêtre de contrôle de zone de liste. Une zone de liste affiche une liste d’éléments que l’utilisateur peut afficher et sélectionner.  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 Fournit les fonctionnalités d’une zone de liste Windows ; permet à l’utilisateur de déplacer des éléments de zone de liste, telle que les littéraux de chaîne et les noms de fichiers, dans la zone de liste. Zones de liste avec cette fonctionnalité sont utiles pour une liste d’éléments dans un ordre autre qu’alphabétique, inclure tels que des fichiers ou chemins d’accès dans un projet.  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 Une fenêtre de contrôle de zone de liste déroulante. Une zone de liste déroulante se compose d’un contrôle d’édition et une zone de liste.  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 Étend le contrôle de zone de liste déroulante en fournissant la prise en charge des listes d'images.  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 Affiche une liste d’éléments avec des cases à cocher, l’utilisateur peut vérifier ou effacer, en regard de chaque élément.  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 Affiche une collection d’éléments constitués chacun d’une icône et une étiquette, d’une manière semblable au volet de droite de l’Explorateur de fichiers.  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 Affiche une liste hiérarchique des icônes et des étiquettes organisées de façon similaire dans le volet de gauche de l’Explorateur de fichiers.  
  
## <a name="toolbars-and-status-bars"></a>Barres d’outils et les barres d’état  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 Fournit les fonctionnalités du contrôle commun de barre d'outils Windows. MFC la plupart des programmes utilisent [CToolBar](../mfc/reference/ctoolbar-class.md) au lieu de cette classe.  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 Une fenêtre horizontale, généralement divisée en volets, dans laquelle une application peut afficher des informations d’état. MFC la plupart des programmes utilisent [CStatusBar](../mfc/reference/cstatusbar-class.md) au lieu de cette classe.  
  
## <a name="miscellaneous-controls"></a>Divers contrôles  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 Affiche un clip vidéo simple.  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 Une petite fenêtre contextuelle qui affiche une ligne unique de texte qui décrit le rôle d’un outil dans une application.  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 Prend en charge d’un contrôle d’édition étendues, ou d’un contrôle d’interface de calendrier simple, qui permet à un utilisateur de choisir une valeur d’heure ou une date spécifique.  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 Affiche les titres ou des étiquettes pour les colonnes.  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 Prend en charge un contrôle d’interface de calendrier simple qui permet à un utilisateur de sélectionner une date.  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 Un contrôle avec onglets sur lequel l’utilisateur peut cliquer, analogues aux intercalaires d’un ordinateur portable.  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 Permet à l’utilisateur créer une combinaison de touches à chaud, l’utilisateur peut sélectionner pour exécuter une action rapidement.  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 Restitue le texte marqué et de lancer les applications appropriées lorsque l’utilisateur clique sur le lien incorporé.  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 Fournit les fonctionnalités du contrôle ActiveX WebBrowser dans une fenêtre MFC.  
  
## <a name="related-classes"></a>Classes associées  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Fournit les fonctionnalités de la liste d’images Windows. Listes d’images sont utilisées avec les contrôles de liste et les contrôles d’arborescence. Ils peuvent également servir à stocker et archiver un ensemble de bitmaps de même taille.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La classe de base pour toutes les vues associées aux contrôles de Windows. Les vues basées sur des contrôles sont décrits ci-dessous.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Contrôle d’édition une vue qui contient un standard de Windows.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Contrôle d’édition une vue qui contient un riche de Windows.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Une vue qui contient un contrôle de liste Windows.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Une vue qui contient un contrôle d’arborescence Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

