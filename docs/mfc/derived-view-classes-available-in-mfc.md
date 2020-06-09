---
title: Classes d'affichage dérivées disponibles dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: dc0f0b10ea291db32c576a7d36b7fc19728fa6ce
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616982"
---
# <a name="derived-view-classes-available-in-mfc"></a>Classes d'affichage dérivées disponibles dans MFC

Le tableau suivant montre les classes d’affichage MFC et leurs relations les unes aux autres. Les fonctionnalités de votre classe d’affichage dépendent de la classe de vue MFC dont elle est dérivée.

### <a name="view-classes"></a>Classes d’affichage

|Class|Description|
|-----------|-----------------|
|[CView](reference/cview-class.md)|Classe de base de toutes les vues.|
|[CCtrlView](reference/cctrlview-class.md)|Classe de base de `CTreeView` ,, `CListView` `CEditView` et `CRichEditView` . Ces classes vous permettent d’utiliser l’architecture document/vue avec les contrôles communs Windows indiqués.|
|[CEditView](reference/ceditview-class.md)|Affichage simple basé sur le contrôle de zone d’édition Windows. Permet d’entrer et de modifier du texte et peut être utilisé comme base pour une application d’éditeur de texte simple. Voir aussi `CRichEditView`.|
|[CRichEditView](reference/cricheditview-class.md)|Vue contenant un objet [CRichEditCtrl](reference/cricheditctrl-class.md) . Cette classe est analogue à `CEditView` , mais contrairement à `CEditView` , `CRichEditView` gère le texte mis en forme.|
|[CListView](reference/clistview-class.md)|Vue contenant un objet [CListCtrl](reference/clistctrl-class.md) .|
|[CTreeView](reference/ctreeview-class.md)|Vue contenant un objet [CTreeCtrl](reference/ctreectrl-class.md) , pour les affichages qui ressemblent à la fenêtre de Explorateur de solutions dans Visual C++.|
|[CScrollView](reference/cscrollview-class.md)|Classe de base de `CFormView` , `CRecordView` et `CDaoRecordView` . Implémente le défilement du contenu de la vue.|
|[CFormView](reference/cformview-class.md)|Mode formulaire, vue qui contient des contrôles. Une application basée sur les formulaires fournit une ou plusieurs interfaces de formulaire de ce type.|
|[CHtmlView](reference/chtmlview-class.md)|Vue de navigateur Web avec laquelle l’utilisateur de l’application peut parcourir les sites du World Wide Web, ainsi que les dossiers dans le système de fichiers local et sur un réseau. La vue du navigateur Web peut également fonctionner comme un conteneur de documents actifs.|
|[CRecordView](reference/crecordview-class.md)|Mode formulaire qui affiche des enregistrements de base de données ODBC dans des contrôles. Si vous sélectionnez la prise en charge ODBC dans votre projet, la classe de base de la vue est `CRecordView` . La vue est connectée à un `CRowset` objet.|
|[CDaoRecordView](reference/cdaorecordview-class.md)|Mode formulaire qui affiche les enregistrements de base de données DAO dans les contrôles. Si vous sélectionnez la prise en charge de DAO dans votre projet, la classe de base de la vue est `CDaoRecordView` . La vue est connectée à un `CDaoRecordset` objet.|
|[COleDBRecordView](reference/coledbrecordview-class.md)|Mode formulaire qui affiche OLE DB enregistrements dans des contrôles. Si vous sélectionnez OLE DB la prise en charge dans votre projet, la classe de base de la vue est `COleDBRecordView` . La vue est connectée à un `CRowset` objet.|

> [!NOTE]
> À partir de la version 4,0 de MFC, `CEditView` est dérivée de `CCtrlView` .

Pour utiliser ces classes dans votre application, dérivez les classes d’affichage de l’application à partir de celles-ci. Pour obtenir des informations connexes, consultez [défilement et mise à l’échelle des vues](scrolling-and-scaling-views.md). Pour plus d’informations sur les classes de base de données, consultez [vue d’ensemble : programmation de base de données](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des vues](using-views.md)
