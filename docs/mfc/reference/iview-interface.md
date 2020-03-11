---
title: Interface IView
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78872446"
---
# <a name="iview-interface"></a>Interface IView

Implémente plusieurs méthodes que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utilise pour envoyer des notifications d’affichage à un contrôle managé.

## <a name="syntax"></a>Syntaxe

```
interface class IView
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IView :: OnActivateView](#onactivateview)|Appelée par MFC lorsqu’une vue est activée ou désactivée.|
|[IView :: OnInitialUpdate](#oninitialupdate)|Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.|
|[IView :: OnUpdate](#onupdate)|Appelé par MFC après la modification du document de la vue ; Cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.|

## <a name="remarks"></a>Notes

`IView` implémente plusieurs méthodes que `CWinFormsView` utilise pour transférer des notifications d’affichage courantes à un contrôle managé hébergé. Il s’agit des [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) et [OnActivateView](#onactivateview).

`IView` est similaire à [CView](../../mfc/reference/cview-class.md), mais est utilisé uniquement avec les vues et les contrôles managés.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Spécifications

En-tête : afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a>IView :: OnActivateView

Appelée par MFC lorsqu’une vue est activée ou désactivée.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Paramètres

*activate*<br/>
Indique si la vue est en cours d’activation ou de désactivation.

## <a name="oninitialupdate"></a>IView :: OnInitialUpdate

Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView :: OnUpdate

Appelée par MFC après la modification du document de la vue.
```
void OnUpdate();
```

## <a name="remarks"></a>Notes

Cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.

## <a name="see-also"></a>Voir aussi

[CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)
