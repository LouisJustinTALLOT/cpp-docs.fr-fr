---
title: Interface IView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84ed9bfb8b0c8b5ab30af07d8f0448109161df51
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077762"
---
# <a name="iview-interface"></a>Interface IView

Implémente plusieurs méthodes qui [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utilise pour envoyer des notifications d’affichage à un contrôle géré.

## <a name="syntax"></a>Syntaxe

```
interface class IView
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Appelé par MFC lorsqu’une vue est activée ou désactivée.|
|[IView::OnInitialUpdate](#oninitialupdate)|Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.|
|[IView::OnUpdate](#onupdate)|Appelé par MFC, une fois que le document de la vue a été modifié ; Cette fonction permet l’affichage pour mettre à jour son affichage afin de refléter les modifications.|

## <a name="remarks"></a>Notes

`IView` implémente plusieurs méthodes qui `CWinFormsView` utilise pour transférer les notifications d’affichage communes à un contrôle géré hébergé. Il s’agit de [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) et [OnActivateView](#onactivateview).

`IView` est similaire à [CView](../../mfc/reference/cview-class.md), mais est utilisé uniquement avec des vues gérées et des contrôles.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Configuration requise

En-tête : les afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a> IView::OnActivateView

Appelé par MFC lorsqu’une vue est activée ou désactivée.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Paramètres

*Activer*<br/>
Indique si la vue est activée ou désactivée.

## <a name="oninitialupdate"></a> IView::OnInitialUpdate

Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate

Appelé par MFC, une fois que le document de la vue a été modifié.
```
void OnUpdate();
```

## <a name="remarks"></a>Notes

Cette fonction permet l’affichage pour mettre à jour son affichage afin de refléter les modifications.

## <a name="see-also"></a>Voir aussi

[CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)
