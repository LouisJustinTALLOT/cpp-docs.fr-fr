---
title: Classe CMessageMap
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
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326720"
---
# <a name="cmessagemap-class"></a>Classe CMessageMap

Cette classe permet d’accéder aux cartes de message d’un objet par un autre objet.

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
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Accéde à une `CMessageMap`carte de message dans la classe dérivée.|

## <a name="remarks"></a>Notes

`CMessageMap`est une classe de base abstraite qui permet d’accéder aux cartes de messages d’un objet par un autre objet. Pour qu’un objet expose ses cartes de `CMessageMap`message, sa classe doit dériver de .

ATL `CMessageMap` utilise pour prendre en charge les fenêtres contenues et l’enchaînement dynamique de carte de message. Par exemple, toute classe contenant un objet [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) doit dériver de `CMessageMap`. Le code suivant est prélevé sur l’échantillon [SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) Grâce [à CComControl](../../atl/reference/ccomcontrol-class.md), la `CAtlEdit` classe dérive automatiquement de `CMessageMap`.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Parce que la `m_EditCtrl`fenêtre contenue, , va utiliser `CAtlEdit` une `CMessageMap`carte de message dans la classe contenant, dérive de .

Pour plus d’informations sur les cartes de messages, voir [Cartes de messages](../../atl/message-maps-atl.md) dans l’article "ATL Window Classes."

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage

Accéde à la carte de message identifiée par `CMessageMap` *dwMsgMapID* dans une classe dérivée.

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
[dans] La poignée à la fenêtre recevant le message.

*uMsg*<br/>
[dans] Le message envoyé à la fenêtre.

*wParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

*lResult*<br/>
[out] Le résultat du traitement du message.

*dwMsgMapID*<br/>
[dans] L’identifiant de la carte de message qui traitera le message. La carte de message par défaut, déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est identifiée par 0. Une carte de message alternative, déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifiée par `msgMapID`.

### <a name="return-value"></a>Valeur de retour

VRAI si le message est entièrement manipulé; autrement, FALSE.

### <a name="remarks"></a>Notes

Appelé par la procédure de fenêtre d’un objet [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) ou d’un objet qui est dynamiquement enchaîné à la carte de message.

## <a name="see-also"></a>Voir aussi

[Classe CDynamicChain](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
