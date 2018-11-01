---
title: Classes d'affichage (Architecture)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: 7855f152e340b488d64f01dbf290034e1bdbc9b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647293"
---
# <a name="view-classes-architecture"></a>Classes d'affichage (Architecture)

`CView` et ses classes dérivées sont des fenêtres enfants qui représentent la zone cliente d’une fenêtre frame. Vues affichent les données et acceptent l’entrée pour un document.

Une classe d’affichage est associée à une classe de document et une classe de fenêtre frame à l’aide d’un objet de modèle de document.

[CView](../mfc/reference/cview-class.md)<br/>
La classe de base pour les vues de données d’un document spécifique à l’application. Vues affichent des données et acceptent l’entrée d’utilisateur pour modifier ou sélectionner les données. Dériver vos classes de vue à partir de `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
La classe de base pour les vues avec des fonctionnalités de défilement. Dérivez votre classe de vue de `CScrollView` pour le défilement automatique.

## <a name="form-and-record-views"></a>Formulaire et les vues d’enregistrements

Vues de formulaire sont également faire défiler les vues. Ils sont basés sur un modèle de boîte de dialogue.

Vues des enregistrements sont dérivées des vues de formulaire. Outre le modèle de boîte de dialogue, ils ont également une connexion à une base de données.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Une vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Fournit un formulaire de vue directement connecté à un objet de jeu d’enregistrements d’objet DAO (Data Access). Comme toutes les vues de formulaire, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue.

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
Prend en charge un contrôle pour la navigation au sein d’une application Web. Le contrôle prend en charge HTML dynamique dans MFC.

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
Fournit la prise en charge MFC OLE DB pour les modes formulaire.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Fournit un formulaire de vue directement connecté à un objet de jeu d’enregistrements Open Database Connectivity (ODBC). Comme toutes les vues de formulaire, un `CRecordView` est basé sur un modèle de boîte de dialogue.

## <a name="control-views"></a>Vues de contrôle

Vues de contrôle affichent un contrôle comme leur affichage.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La classe de base pour toutes les vues associées aux contrôles de Windows. Les vues basées sur les contrôles sont décrits ci-dessous.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Contrôle d’édition une vue qui contient un standard de Windows (voir [CEdit](../mfc/reference/cedit-class.md)). Modifier l’édition de texte de prise en charge des contrôles, la recherche, en remplaçant et possibilités de défilement.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Contrôle d’édition une vue qui contient un riche de Windows (voir [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Outre les fonctionnalités d’un contrôle d’édition, la propriété RichEdit tient compte des contrôles prise en charge des polices, couleurs, mise en forme et les objets OLE incorporés.

[CListView](../mfc/reference/clistview-class.md)<br/>
Une vue qui contient un contrôle de liste Windows (consultez [CListCtrl](../mfc/reference/clistctrl-class.md)). Un contrôle de liste affiche les icônes et les chaînes de manière similaire à la partie droite de l’Explorateur de fichiers.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Une vue qui contient un contrôle d’arborescence Windows (consultez [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un contrôle d’arborescence affiche des icônes et les chaînes organisés dans une hiérarchie d’une manière similaire dans le volet de gauche de l’Explorateur de fichiers.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

