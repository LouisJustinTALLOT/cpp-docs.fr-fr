---
title: Dérivées des Classes d’affichage disponibles dans MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f8d058891b361b3747caafd9c4bd279c7626856
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426913"
---
# <a name="derived-view-classes-available-in-mfc"></a>Classes d'affichage dérivées disponibles dans MFC

Le tableau suivant présente les classes d’affichage de MFC et leurs relations entre eux. Les fonctionnalités de votre classe d’affichage dépendant de la classe de vue MFC à partir de laquelle elle dérive.

### <a name="view-classes"></a>Classes d’affichage

|Classe|Description|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Classe de base de toutes les vues.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Classe de base du `CTreeView`, `CListView`, `CEditView`, et `CRichEditView`. Ces classes vous permettent d’utiliser l’architecture document/vue avec les contrôles communs Windows indiqués.|
|[CEditView](../mfc/reference/ceditview-class.md)|Une vue simple basée sur le Windows contrôle de zone d’édition. Permet d’entrer et de modifier le texte et peut être utilisé comme base pour un éditeur de texte simple. Voir aussi `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Une vue contenant une [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) objet. Cette classe est analogue à `CEditView`, mais contrairement à `CEditView`, `CRichEditView` handles texte mis en forme.|
|[CListView](../mfc/reference/clistview-class.md)|Une vue contenant une [CListCtrl](../mfc/reference/clistctrl-class.md) objet.|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Une vue contenant une [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objet, pour les vues qui ressemblent à la fenêtre Explorateur de solutions dans Visual C++.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Classe de base du `CFormView`, `CRecordView`, et `CDaoRecordView`. Implémente le défilement du contenu de la vue.|
|[CFormView](../mfc/reference/cformview-class.md)|Une vue de formulaire, une vue qui contient les contrôles. Une application basée sur les formulaires fournit une ou plusieurs de ces interfaces formulaire.|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Une vue de navigateur Web avec laquelle l’utilisateur peut parcourir les sites sur le World Wide Web, ainsi que les dossiers du système de fichiers local et sur un réseau. La vue du navigateur Web peut également fonctionner comme un conteneur de documents actifs.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Une vue de formulaire qui affiche les enregistrements de base de données ODBC dans des contrôles. Si vous sélectionnez la prise en charge ODBC dans votre projet, la classe de base de la vue est `CRecordView`. La vue est connectée à un `CRowset` objet.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Une vue de formulaire qui affiche les enregistrements de base de données DAO dans des contrôles. Si vous sélectionnez la prise en charge DAO dans votre projet, la classe de base de la vue est `CDaoRecordView`. La vue est connectée à un `CDaoRecordset` objet.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Une vue de formulaire qui affiche les enregistrements OLE DB dans des contrôles. Si vous sélectionnez la prise en charge OLE DB dans votre projet, la classe de base de la vue est `COleDBRecordView`. La vue est connectée à un `CRowset` objet.|

> [!NOTE]
>  Depuis la version 4.0, MFC `CEditView` est dérivée de `CCtrlView`.

Pour utiliser ces classes dans votre application, dérivent les classes d’affichage de l’application. Pour plus d’informations, consultez [défilement et mise à l’échelle des vues](../mfc/scrolling-and-scaling-views.md). Pour plus d’informations sur les classes de base de données, consultez [vue d’ensemble : programmation de base de données](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de vues](../mfc/using-views.md)

