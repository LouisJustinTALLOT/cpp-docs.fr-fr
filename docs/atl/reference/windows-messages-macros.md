---
title: Macros de Messages Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 7bb5e2fa265c3a5dcabcc16d8343d5b86a4aaf42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273910"
---
# <a name="windows-messages-macros"></a>Macros de Messages Windows

Cette macro transfère les messages de fenêtre.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Permet de transférer un message reçu par une fenêtre à une autre fenêtre pour le traitement.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

Cette macro transfère un message reçu par une fenêtre à une autre fenêtre pour le traitement.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message a été traité, zéro dans le cas contraire.

### <a name="remarks"></a>Notes

Utilisez WM_FORWARDMSG pour transférer un message reçu par une fenêtre à une autre fenêtre pour le traitement. Les paramètres LPARAM et WPARAM sont utilisées comme suit :

|Paramètre|Utilisation|
|---------------|-----------|
|WPARAM|Données définies par l’utilisateur|
|LPARAM|Un pointeur vers un `MSG` structure qui contient des informations sur un message|

### <a name="example"></a>Exemple

Dans l’exemple suivant, `m_hWndOther` représente l’autre fenêtre qui reçoit ce message.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
