---
title: Windows Messages Macros
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329411"
---
# <a name="windows-messages-macros"></a>Windows Messages Macros

Cette macro transmet les messages de fenêtre.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Utilisez pour transmettre un message reçu par une fenêtre à une autre fenêtre pour le traitement.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

Cette macro transmet un message reçu par une fenêtre à une autre fenêtre pour le traitement.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le message a été traité, zéro sinon.

### <a name="remarks"></a>Notes

Utilisez WM_FORWARDMSG pour transmettre un message reçu par une fenêtre à une autre fenêtre pour le traitement. Les paramètres LPARAM et WPARAM sont utilisés comme suit :

|Paramètre|Usage|
|---------------|-----------|
|Wparam|Données définies par l’utilisateur|
|Lparam|Un pointeur `MSG` vers une structure qui contient des informations sur un message|

### <a name="example"></a>Exemple

Dans l’exemple `m_hWndOther` suivant, représente l’autre fenêtre qui reçoit ce message.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
