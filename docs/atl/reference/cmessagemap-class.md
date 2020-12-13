---
description: 'En savoir plus sur : classe CMessageMap'
title: CMessageMap, classe
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: 90ecdc101071b84362d328558ff2e74cb9bbeb6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141438"
---
# <a name="cmessagemap-class"></a>CMessageMap, classe

Cette classe permet d’accéder aux tables des messages d’un objet par un autre objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMessageMap ::P rocessWindowMessage](#processwindowmessage)|Accède à une table des messages dans la `CMessageMap` classe dérivée de.|

## <a name="remarks"></a>Notes

`CMessageMap` est une classe de base abstraite qui permet d’accéder aux tables des messages d’un objet par un autre objet. Pour qu’un objet expose ses tables de messages, sa classe doit dériver de `CMessageMap` .

ATL utilise `CMessageMap` pour prendre en charge les fenêtres contenues et le chaînage dynamique des tables de messages. Par exemple, toute classe contenant un objet [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) doit dériver de `CMessageMap` . Le code suivant est extrait de l’exemple de sous- [modification](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) . Via [CComControl](../../atl/reference/ccomcontrol-class.md), la `CAtlEdit` classe dérive automatiquement de `CMessageMap` .

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Étant donné que la fenêtre contenue, `m_EditCtrl` , utilisera une table des messages dans la classe conteneur, `CAtlEdit` dérive de `CMessageMap` .

Pour plus d’informations sur les tables des messages, consultez [tables des messages](../../atl/message-maps-atl.md) dans l’article « classes de fenêtres ATL ».

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a> CMessageMap ::P rocessWindowMessage

Accède à la table des messages identifiée par *dwMsgMapID* dans une `CMessageMap` classe dérivée de.

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la fenêtre qui reçoit le message.

*uMsg*<br/>
dans Message envoyé à la fenêtre.

*wParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lResult*<br/>
à Résultat du traitement du message.

*dwMsgMapID*<br/>
dans Identificateur de la table des messages qui traitera le message. La table des messages par défaut, déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est identifiée par 0. Une autre table des messages, déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifiée par `msgMapID` .

### <a name="return-value"></a>Valeur renvoyée

TRUE si le message est entièrement géré ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelée par la procédure de fenêtre d’un objet [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) ou d’un objet qui est lié dynamiquement à la table des messages.

## <a name="see-also"></a>Voir aussi

[CDynamicChain, classe](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
