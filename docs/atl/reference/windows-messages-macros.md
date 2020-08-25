---
title: Macros de messages Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: b4cd3c2eea24449eb17050b147d9c59560d8358f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834438"
---
# <a name="windows-messages-macros"></a>Macros de messages Windows

Cette macro transfère les messages de fenêtre.

|Nom|Description|
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Utilisez pour transférer un message reçu par une fenêtre à une autre fenêtre en vue de son traitement.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase. h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a> WM_FORWARDMSG

Cette macro transfère un message reçu par une fenêtre à une autre fenêtre pour traitement.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le message a été traité, zéro dans le cas contraire.

### <a name="remarks"></a>Notes

Utilisez WM_FORWARDMSG pour transférer un message reçu par une fenêtre à une autre fenêtre en vue de son traitement. Les paramètres LPARAM et WPARAM sont utilisés comme suit :

|Paramètre|Usage|
|---------------|-----------|
|WPARAM|Données définies par l’utilisateur|
|LPARAM|Pointeur vers une `MSG` structure qui contient des informations à propos d’un message|

### <a name="example"></a>Exemple

Dans l’exemple suivant, `m_hWndOther` représente l’autre fenêtre qui reçoit ce message.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
