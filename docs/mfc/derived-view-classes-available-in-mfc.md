---
title: Classes d'affichage dérivées disponibles dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373501"
---
# <a name="derived-view-classes-available-in-mfc"></a>Classes d'affichage dérivées disponibles dans MFC

Le tableau suivant montre les classes de vision de MFC et leurs relations les uns avec les autres. Les capacités de votre classe de vue dépendent de la classe de vue MFC à partir de laquelle elle dérive.

### <a name="view-classes"></a>Afficher les classes

|Classe|Description|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Classe de base de toutes les vues.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Catégorie de `CTreeView` `CListView`base `CEditView`de `CRichEditView`, , , et . Ces classes vous permettent d’utiliser l’architecture de document/vue avec les contrôles communs Windows indiqués.|
|[CEditView](../mfc/reference/ceditview-class.md)|Une vue simple basée sur le contrôle de la boîte de modification Windows. Permet d’entrer et d’éditer du texte et peut être utilisé comme base pour une simple application d’éditeur de texte. Voir aussi `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Une vue contenant un objet [CRichEditCtrl.](../mfc/reference/cricheditctrl-class.md) Cette classe est `CEditView`analogue à `CEditView` `CRichEditView` , mais contrairement , gère le texte formaté.|
|[CListView](../mfc/reference/clistview-class.md)|Une vue contenant un objet [CListCtrl.](../mfc/reference/clistctrl-class.md)|
|[CTreeView (en)](../mfc/reference/ctreeview-class.md)|Une vue contenant un objet [CTreeCtrl,](../mfc/reference/ctreectrl-class.md) pour des vues qui ressemblent à la fenêtre Solution Explorer dans Visual C.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Catégorie de `CFormView` `CRecordView`base `CDaoRecordView`de , , et . Implémente le fait de faire défiler le contenu de la vue.|
|[CFormView](../mfc/reference/cformview-class.md)|Une vue de formulaire, une vue qui contient des contrôles. Une application basée sur des formulaires fournit une ou plusieurs interfaces de formulaire de ce type.|
|[CHtmlView (en anglais)](../mfc/reference/chtmlview-class.md)|Une vue de navigateur Web avec laquelle l’utilisateur de l’application peut parcourir des sites sur le World Wide Web, ainsi que des dossiers dans le système de fichiers local et sur un réseau. La vue du navigateur Web peut également fonctionner comme un conteneur de documents actifs.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Une vue de formulaire qui affiche les enregistrements de base de données ODBC dans les contrôles. Si vous sélectionnez le support ODBC dans votre `CRecordView`projet, la classe de base de la vue est . La vue est `CRowset` connectée à un objet.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Une vue de formulaire qui affiche les enregistrements de base de données DAO dans les contrôles. Si vous sélectionnez le support DAO dans votre `CDaoRecordView`projet, la classe de base de la vue est . La vue est `CDaoRecordset` connectée à un objet.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Une vue de formulaire qui affiche les enregistrements OLE DB dans les contrôles. Si vous sélectionnez le support OLE DB dans `COleDBRecordView`votre projet, la classe de base de la vue est . La vue est `CRowset` connectée à un objet.|

> [!NOTE]
> En date de MFC version `CEditView` 4.0, est dérivé de `CCtrlView`.

Pour utiliser ces classes dans votre application, en tirer les classes de vue de l’application. Pour plus d’informations connexes, voir [Scrolling and Scaling Views](../mfc/scrolling-and-scaling-views.md). Pour plus d’informations sur les classes de base de données, voir [Aperçu: Programmation de base de données](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des vues](../mfc/using-views.md)
