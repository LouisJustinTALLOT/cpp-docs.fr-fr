---
title: IView, interface
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
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751285"
---
# <a name="iview-interface"></a>IView, interface

Implémente plusieurs méthodes utilisées [par CWinFormsView](../../mfc/reference/cwinformsview-class.md) pour envoyer des notifications de vue à un contrôle géré.

## <a name="syntax"></a>Syntaxe

```
interface class IView
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Appelé par MFC lorsqu’une vue est activée ou désactivée.|
|[IView::OnInitialUpdate](#oninitialupdate)|Appelé par le cadre après la vue est d’abord attaché au document, mais avant que la vue est initialement affichée.|
|[IView::OnUpdate](#onupdate)|Appelé par MFC après que le document de la vue a été modifié; cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.|

## <a name="remarks"></a>Notes

`IView`implémente `CWinFormsView` plusieurs méthodes qui utilisent pour transmettre des notifications de vue communes à un contrôle géré hébergé. Ce sont [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) et [OnActivateView](#onactivateview).

`IView`est similaire à [CView](../../mfc/reference/cview-class.md), mais n’est utilisé qu’avec des vues et des contrôles gérés.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Spécifications

En-tête: afxwinforms.h (défini dans l’assemblage atlmfc-lib-mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView

Appelé par MFC lorsqu’une vue est activée ou désactivée.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Paramètres

*Activer*<br/>
Indique si la vue est activée ou désactivée.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate

Appelé par le cadre après la vue est d’abord attaché au document, mais avant que la vue est initialement affichée.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate

Appelé par MFC après que le document de la vue a été modifié.

```cpp
void OnUpdate();
```

## <a name="remarks"></a>Notes

Cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.

## <a name="see-also"></a>Voir aussi

[CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)
