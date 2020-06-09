---
title: Contrôles (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: accbee66cdee4e7b849da2b034d253b1c206d8f1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617177"
---
# <a name="controls-mfc"></a>Contrôles (MFC)

Les contrôles sont des objets avec lesquels les utilisateurs peuvent interagir pour entrer ou manipuler des données. Ils apparaissent généralement dans des boîtes de dialogue ou des barres d’outils. Cette série de rubriques traite de trois principaux types de contrôles :

- Contrôles communs Windows, notamment les contrôles de type owner-drawn

- Contrôles ActiveX

- Autres classes de contrôles fournies par la bibliothèque MFC (Microsoft Foundation Class Library)

## <a name="windows-common-controls"></a>Contrôles Windows communs

Le système d’exploitation Windows a toujours fourni un certain nombre de contrôles communs Windows. Ces objets de contrôle sont programmables, et l’éditeur de boîte de dialogue Visual C++ prend en charge leur ajout à vos boîtes de dialogue. La bibliothèque MFC fournit des classes qui encapsulent chacun de ces contrôles, comme indiqué dans le tableau [Contrôles communs Windows et classes MFC](#_core_windows_common_controls_and_mfc_classes). (Certains éléments du tableau ont des rubriques associées qui les décrivent en détail. Pour les contrôles pour lesquels il n’existe pas de rubrique, consultez la documentation de la classe MFC.)

La classe [CWnd](reference/cwnd-class.md) est la classe de base de toutes les classes de fenêtre, y compris toutes les classes de contrôles.

## <a name="activex-controls"></a>Contrôles ActiveX

Vous pouvez utiliser des contrôles ActiveX, anciennement appelés contrôles OLE, dans les boîtes de dialogue de vos applications pour Windows, ou dans des pages HTML sur le World Wide Web. Pour plus d’informations, consultez [contrôles ActiveX MFC](mfc-activex-controls.md).

## <a name="other-mfc-control-classes"></a>Autres classes de contrôles MFC

En plus des classes qui encapsulent tous les contrôles communs Windows et qui prennent en charge la programmation de vos propres contrôles ActiveX (ou l’utilisation de contrôles ActiveX fournis par des tiers), la bibliothèque MFC fournit les classes de contrôles suivantes :

- [CBitmapButton](reference/cbitmapbutton-class.md)

- [CCheckListBox](reference/cchecklistbox-class.md)

- [CDragListBox](reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a>Recherche d’informations sur les contrôles communs Windows

Le tableau ci-dessous décrit brièvement chacun des contrôles communs Windows, notamment la classe wrapper MFC du contrôle.

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Contrôles communs Windows et classes MFC

|Control|Classe MFC|Description|Nouveautés de Windows 95|
|-------------|---------------|-----------------|------------------------|
|[Animation](using-canimatectrl.md)|[CAnimateCtrl](reference/canimatectrl-class.md)|Affiche les frames successives d’un clip vidéo AVI|Oui|
|Bouton|[CButton](reference/cbutton-class.md)|Boutons de commande qui déclenchent une action ; également utilisé pour les cases à cocher, cases d’option et zones de groupe|Non|
|zone de liste déroulante|[CComboBox](reference/ccombobox-class.md)|Combinaison d’une zone d’édition et d’une zone de liste|Non|
|[sélecteur de date et d’heure](using-cdatetimectrl.md)|[CDateTimeCtrl](reference/cdatetimectrl-class.md)|Permet à l’utilisateur de choisir une valeur de date ou d’heure spécifique|Oui|
|zone d’édition|[CEdit](reference/cedit-class.md)|Zones de saisie de texte|Non|
|[zone de liste déroulante étendue](using-ccomboboxex.md)|[CComboBoxEx](reference/ccomboboxex-class.md)|Contrôle de zone de liste déroulante avec la capacité à afficher des images|Oui|
|[titre](using-cheaderctrl.md)|[CHeaderCtrl](reference/cheaderctrl-class.md)|Bouton qui s’affiche au-dessus d’une colonne de texte : contrôle la largeur du texte affiché|Oui|
|[séquence](using-chotkeyctrl.md)|[CHotKeyCtrl](reference/chotkeyctrl-class.md)|Fenêtre qui permet à l’utilisateur de créer une « touche d’accès rapide » pour effectuer une action rapidement|Oui|
|[liste d’images](using-cimagelist.md)|[CImageList](reference/cimagelist-class.md)|Collection d’images utilisée pour gérer de grands ensembles d’icônes ou de bitmaps (la liste d’images n’est pas vraiment un contrôle ; elle prend en charge les listes utilisées par d’autres contrôles)|Oui|
|[list](using-clistctrl.md)|[CListCtrl](reference/clistctrl-class.md)|Fenêtre qui affiche une liste de texte avec des icônes|Oui|
|zone de liste|[CListBox](reference/clistbox-class.md)|Zone qui contient une liste de chaînes|Non|
|[calendrier du mois](using-cmonthcalctrl.md)|[CMonthCalCtrl](reference/cmonthcalctrl-class.md)|Contrôle qui affiche des informations de date|Oui|
|[avancement](using-cprogressctrl.md)|[CProgressCtrl](reference/cprogressctrl-class.md)|Fenêtre qui indique la progression d’une opération longue|Oui|
|[rebar](using-crebarctrl.md)|[CRebarCtrl](reference/crebarctrl-class.md)|Barre d’outils qui peut contenir des fenêtres enfants supplémentaires sous la forme de contrôles|Oui|
|[édition enrichie](using-cricheditctrl.md)|[CRichEditCtrl](reference/cricheditctrl-class.md)|Fenêtre dans laquelle l’utilisateur peut modifier la mise en forme des caractères et des paragraphes (consultez [Classes associées aux contrôles RichEdit](classes-related-to-rich-edit-controls.md))|Oui|
|barre de défilement|[CScrollBar](reference/cscrollbar-class.md)|Barre de défilement utilisée comme contrôle dans une boîte de dialogue (pas dans une fenêtre)|Non|
|[curseur](using-csliderctrl.md)|[CSliderCtrl](reference/csliderctrl-class.md)|Fenêtre contenant un contrôle Slider avec des graduations facultatives|Oui|
|[bouton toupie](using-cspinbuttonctrl.md)|[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)|Paire de boutons fléchés sur lesquels l’utilisateur peut cliquer pour incrémenter ou décrémenter une valeur|Oui|
|texte statique|[CStatic](reference/cstatic-class.md)|Texte servant à étiqueter d’autres contrôles|Non|
|[barre d’État](using-cstatusbarctrl.md)|[CStatusBarCtrl](reference/cstatusbarctrl-class.md)|Fenêtre servant à afficher des informations d’état, semblable à la classe MFC `CStatusBar`|Oui|
|[/](using-ctabctrl.md)|[CTabCtrl](reference/ctabctrl-class.md)|Analogues aux intercalaires d’un agenda ; utilisé dans les boîtes de dialogue avec onglets ou dans les feuilles de propriétés|Oui|
|[barre](using-ctoolbarctrl.md)|[CToolBarCtrl](reference/ctoolbarctrl-class.md)|Fenêtre avec des boutons générant des commandes, semblable à la classe MFC `CToolBar`|Oui|
|[info-bulle](using-ctooltipctrl.md)|[CToolTipCtrl](reference/ctooltipctrl-class.md)|Petite fenêtre contextuelle qui décrit la fonction d’un bouton de barre d’outils ou autre outil|Oui|
|[tree](using-ctreectrl.md)|[CTreeCtrl](reference/ctreectrl-class.md)|Fenêtre qui affiche une liste hiérarchique d’éléments|Oui|

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- Un contrôle spécifique : consultez le tableau [Contrôles communs Windows et classes MFC](#_core_windows_common_controls_and_mfc_classes) dans cette rubrique pour obtenir des liens vers tous les contrôles

- [Création et utilisation de contrôles](making-and-using-controls.md)

- [Utilisation de l’éditeur de boîtes de dialogue pour ajouter des contrôles](using-the-dialog-editor-to-add-controls.md)

- [Ajout manuel de contrôles à une boîte de dialogue](adding-controls-by-hand.md)

- [Dérivation de classes de contrôles à partir des classes de contrôles MFC](deriving-controls-from-a-standard-control.md)

- [Utilisation de contrôles communs comme fenêtres enfants](using-a-common-control-as-a-child-window.md)

- [Notifications de contrôles communs](receiving-notification-from-common-controls.md)

- [Ajouter des contrôles communs à une boîte de dialogue](using-common-controls-in-a-dialog-box.md).

- [Dériver un contrôle à partir d’un contrôle Windows standard](deriving-controls-from-a-standard-control.md)

- [Accéder à des contrôles de boîte de dialogue avec la sécurité de type](type-safe-access-to-controls-in-a-dialog-box.md)

- [Recevoir des messages de notification à partir de contrôles communs](receiving-notification-from-common-controls.md)

- [Exemples](common-control-sample-list.md)

Pour plus d’informations sur les contrôles communs Windows dans le SDK Windows, consultez [contrôles communs](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)
