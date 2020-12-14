---
description: 'En savoir plus sur : IView interface'
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
ms.openlocfilehash: e0229d61d12638935d7e4d928626a4bd7f5a830a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219445"
---
# <a name="iview-interface"></a>Interface IView

Implémente plusieurs méthodes que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utilise pour envoyer des notifications d’affichage à un contrôle managé.

## <a name="syntax"></a>Syntaxe

```
interface class IView
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IView :: OnActivateView](#onactivateview)|Appelée par MFC lorsqu’une vue est activée ou désactivée.|
|[IView :: OnInitialUpdate](#oninitialupdate)|Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.|
|[IView :: OnUpdate](#onupdate)|Appelé par MFC après la modification du document de la vue ; Cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.|

### <a name="remarks"></a>Notes

`IView` implémente plusieurs méthodes qui `CWinFormsView` utilisent pour transférer les notifications d’affichage courantes à un contrôle managé hébergé. Il s’agit des [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) et [OnActivateView](#onactivateview).

`IView` est semblable à [CView](../../mfc/reference/cview-class.md), mais est utilisé uniquement avec les vues et les contrôles managés.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Spécifications

En-tête : afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a> IView :: OnActivateView

Appelée par MFC lorsqu’une vue est activée ou désactivée.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Paramètres

*déclencher*<br/>
Indique si la vue est en cours d’activation ou de désactivation.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a> IView :: OnInitialUpdate

Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a> IView :: OnUpdate

Appelée par MFC après la modification du document de la vue.

```cpp
void OnUpdate();
```

### <a name="remarks"></a>Notes

Cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.

## <a name="see-also"></a>Voir aussi

[CWinFormsView (classe)](../../mfc/reference/cwinformsview-class.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)
