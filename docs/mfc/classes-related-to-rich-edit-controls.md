---
title: Les classes liées aux contrôles RichEdit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee7b6400dcd5c91d054b31153c21008d5302bd0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401262"
---
# <a name="classes-related-to-rich-edit-controls"></a>Classes associées aux contrôles RichEdit

Le [CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) classes fournissent les fonctionnalités du contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) dans le contexte de l’architecture document/vue de MFC. `CRichEditView` gère le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` gère la liste des éléments client OLE qui se trouvent dans la vue. `CRichEditCntrItem` fournit l’accès côté conteneur à l’élément client OLE. Pour modifier le contenu d’un `CRichEditView`, utilisez [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) pour accéder aux sous-jacent contrôle rich edit.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

