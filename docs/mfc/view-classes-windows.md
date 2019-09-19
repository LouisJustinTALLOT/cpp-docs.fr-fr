---
title: Classes d'affichage (Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: f3e9ea2ebf3eb0ce04fde0339aaf0243686248a9
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096039"
---
# <a name="view-classes-windows"></a>Classes d'affichage (Windows)

`CView`et ses classes dérivées sont des fenêtres enfants qui représentent la zone cliente d’une fenêtre frame. Les vues affichent les données et acceptent les entrées d’un document.

Une classe de vue est associée à une classe de document et à une classe de fenêtre frame à l’aide d’un objet de modèle de document.

[CView](../mfc/reference/cview-class.md)<br/>
Classe de base pour les vues spécifiques à l’application des données d’un document. Les vues affichent les données et acceptent les entrées utilisateur pour modifier ou sélectionner les données. Dérivez votre classe d’affichage `CView`ou vos classes à partir de.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Classe de base pour les vues avec des fonctions de défilement. Dérivez votre classe `CScrollView` d’affichage de pour le défilement automatique.

## <a name="form-and-record-views"></a>Vues de formulaire et d’enregistrement

Les affichages de formulaire défilent également les vues. Ils sont basés sur un modèle de boîte de dialogue.

Les vues des enregistrements sont dérivées des modes formulaire. Outre le modèle de boîte de dialogue, ils disposent également d’une connexion à une base de données.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une `CFormView` classe de pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset d’objet d’accès aux données (DAO). Comme tous les affichages de `CDaoRecordView` formulaire, un est basé sur un modèle de boîte de dialogue. DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. 3,6 est la version finale et est considérée comme obsolète.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset Open Database Connectivity (ODBC). Comme tous les affichages de `CRecordView` formulaire, un est basé sur un modèle de boîte de dialogue.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Mode formulaire qui fournit les fonctionnalités de la plateforme d’édition HTML WebBrowser.

## <a name="control-views"></a>Vues de contrôle

Les vues de contrôle affichent un contrôle comme vue.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Classe de base pour toutes les vues associées aux contrôles Windows. Les vues basées sur les contrôles sont décrites ci-dessous.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Vue qui contient un contrôle d’édition standard Windows (consultez [CEdit](../mfc/reference/cedit-class.md)). Les contrôles d’édition prennent en charge la modification de texte, la recherche, le remplacement et les fonctions de défilement.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Vue qui contient un contrôle Rich Edit Windows (consultez [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Outre les fonctionnalités d’un contrôle d’édition, les contrôles RichEdit prennent en charge les polices, les couleurs, la mise en forme des paragraphes et les objets OLE incorporés.

[CListView](../mfc/reference/clistview-class.md)<br/>
Vue qui contient un contrôle de liste Windows (consultez [CListCtrl](../mfc/reference/clistctrl-class.md)). Un contrôle de liste affiche une collection d’éléments, chacun composé d’une icône et d’une étiquette, d’une manière similaire au volet droit de l’Explorateur de fichiers.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Vue qui contient un contrôle d’arborescence Windows (consultez [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un contrôle d’arborescence affiche une liste hiérarchique des icônes et des étiquettes organisées de manière similaire au volet gauche de l’Explorateur de fichiers.

## <a name="related-classes"></a>Classes connexes

`CSplitterWnd`vous permet d’avoir plusieurs vues dans une seule fenêtre frame. `CPrintDialog`et `CPrintInfo` prennent en charge la fonctionnalité d’impression et d’aperçu avant impression des vues. `CRichEditDoc`et `CRichEditCntrItem` sont utilisés avec `CRichEditView` pour implémenter des fonctionnalités de conteneur OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Fenêtre que l’utilisateur peut fractionner en plusieurs volets. Ces volets peuvent être redimensionnables par l’utilisateur ou par une taille fixe.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour l’impression d’un fichier.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Structure contenant des informations sur un travail d’impression ou d’aperçu avant impression. Utilisé par `CView`l’architecture d’impression de.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Gère la liste des éléments du client OLE qui se trouvent `CRichEditView`dans un.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Fournit l’accès côté client à un élément OLE stocké dans `CRichEditView`un.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
