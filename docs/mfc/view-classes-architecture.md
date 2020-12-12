---
description: 'En savoir plus sur : classes d’affichage (architecture)'
title: Classes d'affichage (Architecture)
ms.date: 09/17/2019
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: fe883c34ad8bd3948ee65ecec25151cc4dd2416c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143128"
---
# <a name="view-classes-architecture"></a>Classes d'affichage (Architecture)

`CView` et ses classes dérivées sont des fenêtres enfants qui représentent la zone cliente d’une fenêtre frame. Les vues affichent les données et acceptent les entrées d’un document.

Une classe de vue est associée à une classe de document et à une classe de fenêtre frame à l’aide d’un objet de modèle de document.

[CView](../mfc/reference/cview-class.md)<br/>
Classe de base pour les vues spécifiques à l’application des données d’un document. Les vues affichent les données et acceptent les entrées utilisateur pour modifier ou sélectionner les données. Dérivez vos classes d’affichage de `CView` .

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Classe de base pour les vues avec des fonctions de défilement. Dérivez votre classe d’affichage de `CScrollView` pour le défilement automatique.

## <a name="form-and-record-views"></a>Vues de formulaire et d’enregistrement

Les affichages de formulaire défilent également les vues. Ils sont basés sur un modèle de boîte de dialogue.

Les vues des enregistrements sont dérivées des modes formulaire. Outre le modèle de boîte de dialogue, ils disposent également d’une connexion à une base de données.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset d’objet d’accès aux données (DAO). Comme tous les affichages de formulaire, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue. DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
Prend en charge un contrôle pour la navigation Web dans une application. Le contrôle prend en charge le code HTML dynamique dans MFC.

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
Fournit la prise en charge des OLE DB MFC pour les vues de formulaire.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset Open Database Connectivity (ODBC). Comme tous les affichages de formulaire, un `CRecordView` est basé sur un modèle de boîte de dialogue.

## <a name="control-views"></a>Vues de contrôle

Les vues de contrôle affichent un contrôle comme vue.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
Classe de base pour toutes les vues associées aux contrôles Windows. Les vues basées sur les contrôles sont décrites ci-dessous.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Vue qui contient un contrôle d’édition standard Windows (consultez [CEdit](../mfc/reference/cedit-class.md)). Les contrôles d’édition prennent en charge la modification de texte, la recherche, le remplacement et les fonctions de défilement.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Vue qui contient un contrôle Rich Edit Windows (consultez [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Outre les fonctionnalités d’un contrôle d’édition, les contrôles RichEdit prennent en charge les polices, les couleurs, la mise en forme des paragraphes et les objets OLE incorporés.

[CListView](../mfc/reference/clistview-class.md)<br/>
Vue qui contient un contrôle de liste Windows (consultez [CListCtrl](../mfc/reference/clistctrl-class.md)). Un contrôle de liste affiche des icônes et des chaînes d’une manière similaire au volet droit de l’Explorateur de fichiers.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Vue qui contient un contrôle d’arborescence Windows (consultez [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un contrôle d’arborescence affiche des icônes et des chaînes organisées dans une hiérarchie d’une manière similaire au volet gauche de l’Explorateur de fichiers.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../mfc/class-library-overview.md)
