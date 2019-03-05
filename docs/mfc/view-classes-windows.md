---
title: Classes d'affichage (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: ad58fd6fa2548c2cf320baf75b8fc33a835ddd55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267093"
---
# <a name="view-classes-windows"></a>Classes d'affichage (Windows)

`CView` et ses classes dérivées sont des fenêtres enfants qui représentent la zone cliente d’une fenêtre frame. Vues affichent les données et acceptent l’entrée pour un document.

Une classe d’affichage est associée à une classe de document et une classe de fenêtre frame à l’aide d’un objet de modèle de document.

[CView](../mfc/reference/cview-class.md)<br/>
La classe de base pour les vues de données d’un document spécifique à l’application. Vues affichent des données et acceptent l’entrée d’utilisateur pour modifier ou sélectionner les données. Dériver votre classe d’affichage ou les classes de `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
La classe de base pour les vues avec des fonctionnalités de défilement. Dérivez votre classe de vue de `CScrollView` pour le défilement automatique.

## <a name="form-and-record-views"></a>Formulaire et les vues d’enregistrements

Vues de formulaire sont également faire défiler les vues. Ils sont basés sur un modèle de boîte de dialogue.

Vues des enregistrements sont dérivées des vues de formulaire. Outre le modèle de boîte de dialogue, ils ont également une connexion à une base de données.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Une vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Fournit un formulaire de vue directement connecté à un objet de jeu d’enregistrements d’objet DAO (Data Access). Comme toutes les vues de formulaire, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Fournit un formulaire de vue directement connecté à un objet de jeu d’enregistrements Open Database Connectivity (ODBC). Comme toutes les vues de formulaire, un `CRecordView` est basé sur un modèle de boîte de dialogue.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Une vue de formulaire qui fournit les fonctionnalités de la plateforme d’édition WebBrowser HTML.

## <a name="control-views"></a>Vues de contrôle

Vues de contrôle affichent un contrôle comme leur affichage.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La classe de base pour toutes les vues associées aux contrôles de Windows. Les vues basées sur les contrôles sont décrits ci-dessous.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Contrôle d’édition une vue qui contient un standard de Windows (voir [CEdit](../mfc/reference/cedit-class.md)). Modifier l’édition de texte de prise en charge des contrôles, la recherche, en remplaçant et possibilités de défilement.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Contrôle d’édition une vue qui contient un riche de Windows (voir [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Outre les fonctionnalités d’un contrôle d’édition, la propriété RichEdit tient compte des contrôles prise en charge des polices, couleurs, mise en forme et les objets OLE incorporés.

[CListView](../mfc/reference/clistview-class.md)<br/>
Une vue qui contient un contrôle de liste Windows (consultez [CListCtrl](../mfc/reference/clistctrl-class.md)). Un contrôle de liste affiche une collection d’éléments, chacun d'entre eux comprenant une icône et une étiquette, d’une manière similaire dans le volet de droite de l’Explorateur de fichiers.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Une vue qui contient un contrôle d’arborescence Windows (consultez [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un contrôle d’arborescence affiche une liste hiérarchique des icônes et des étiquettes organisés de manière similaire dans le volet de gauche de l’Explorateur de fichiers.

## <a name="related-classes"></a>Classes connexes

`CSplitterWnd` vous permet d’avoir plusieurs vues dans une même fenêtre frame. `CPrintDialog` et `CPrintInfo` prennent en charge l’impression et Aperçu avant impression des vues. `CRichEditDoc` et `CRichEditCntrItem` sont utilisés avec `CRichEditView` pour implémenter les fonctionnalités de conteneur OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Une fenêtre de l’utilisateur peut être fractionnée en plusieurs volets. Ces volets peuvent être redimensionnables par l’utilisateur ou d’une taille fixe.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour l’impression d’un fichier.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Une structure contenant des informations sur un travail d’impression ou Aperçu avant impression. Utilisé par `CView`architecture d’impression.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Gère la liste des éléments client OLE qui se trouvent dans un `CRichEditView`.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Fournit un accès côté client à OLE élément stocké dans un `CRichEditView`.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
