---
description: 'En savoir plus sur : classes liées aux contrôles RichEdit'
title: Classes associées aux contrôles RichEdit
ms.date: 11/04/2016
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
ms.openlocfilehash: b44c5a874c7f48c132f31483bf5ee73eafbe4da5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176676"
---
# <a name="classes-related-to-rich-edit-controls"></a>Classes associées aux contrôles RichEdit

Les classes [CRichEditView](reference/cricheditview-class.md), [CRichEditDoc](reference/cricheditdoc-class.md)et [CRichEditCntrItem](reference/cricheditcntritem-class.md) fournissent les fonctionnalités du contrôle Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) dans le contexte de l’architecture document/vue de MFC. `CRichEditView` conserve le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` conserve la liste des éléments du client OLE qui sont dans la vue. `CRichEditCntrItem` fournit un accès côté conteneur à l’élément client OLE. Pour modifier le contenu d’un `CRichEditView` , utilisez [CRichEditView :: GetRichEditCtrl](reference/cricheditview-class.md#getricheditctrl) pour accéder au contrôle Rich Edit sous-jacent.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Contrôles](controls-mfc.md)
