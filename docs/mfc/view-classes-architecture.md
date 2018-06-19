---
title: Affichage de Classes (Architecture) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.view
dev_langs:
- C++
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11bb3d9e551089a156d255f7b27fb55cbe87bdbe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383745"
---
# <a name="view-classes-architecture"></a>Classes d'affichage (Architecture)
`CView` et ses classes dérivées sont des fenêtres enfants qui représentent la zone cliente d’une fenêtre frame. Vues affichent les données et acceptent l’entrée d’un document.  
  
 Une classe d’affichage est associée à une classe de document et une classe de fenêtre frame à l’aide d’un objet de modèle de document.  
  
 [CView](../mfc/reference/cview-class.md)  
 La classe de base pour les vues de données d’un document spécifique à l’application. Vues affichent les données et acceptent l’entrée d’utilisateur pour modifier ou sélectionner les données. Dériver les classes à partir de votre vue `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 La classe de base pour les vues avec des possibilités de défilement. Dérivez votre classe de vue de `CScrollView` pour le défilement automatique.  
  
## <a name="form-and-record-views"></a>Formulaire et les vues des enregistrements  
 Vues du formulaire sont également faire défiler les vues. Ils sont basés sur un modèle de boîte de dialogue.  
  
 Vues des enregistrements sont dérivées des modes formulaire. Outre le modèle de boîte de dialogue, ils ont également une connexion à une base de données.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Une vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Fournit une forme vue directement connectée à un objet de jeu d’enregistrements d’objet DAO (Data Access). Comme toutes les vues de l’écran, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue.  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 Prend en charge un contrôle pour la navigation au sein d’une application Web. Le contrôle prend en charge dynamic HTML dans MFC.  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 Fournit la prise en charge MFC OLE DB pour les modes formulaire.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Fournit une forme vue directement connectée à un objet de jeu d’enregistrements de base de données ODBC (Open Connectivity). Comme toutes les vues de l’écran, un `CRecordView` est basé sur un modèle de boîte de dialogue.  
  
## <a name="control-views"></a>Vues de contrôle  
 Vues de contrôle affichent un contrôle comme son affichage.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La classe de base pour toutes les vues associées aux contrôles de Windows. Les vues basées sur des contrôles sont décrits ci-dessous.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Contrôle d’édition une vue qui contient un Windows standard (consultez [CEdit](../mfc/reference/cedit-class.md)). Modifier l’édition de texte de prise en charge des contrôles, la recherche, en remplaçant et possibilités de défilement.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Contrôle d’édition une vue qui contient un riche de Windows (voir [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Outre les fonctionnalités d’un contrôle d’édition, la propriété RichEdit tient compte des contrôles prise en charge des polices, couleurs, mise en forme et les objets OLE incorporés.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Une vue qui contient un contrôle de liste de Windows (voir [CListCtrl](../mfc/reference/clistctrl-class.md)). Un contrôle de liste affiche les icônes et les chaînes d’une manière semblable au volet de droite de l’Explorateur de fichiers.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Une vue qui contient un contrôle d’arborescence Windows (consultez [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un contrôle d’arborescence affiche des icônes et les chaînes organisés dans une hiérarchie de façon similaire dans le volet de gauche de l’Explorateur de fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

