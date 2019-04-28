---
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
ms.openlocfilehash: 617b7b4592c96625b44fbe5c2b93da971a423128
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258531"
---
# <a name="cmessagemap-class"></a>CMessageMap, classe

Cette classe autorise que les messages d’un objet est mappé pour être accessibles par un autre objet.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Accède à une table des messages dans la `CMessageMap`-classe dérivée.|

## <a name="remarks"></a>Notes

`CMessageMap` est une classe de base abstraite qui permet les messages d’un objet est mappé pour être accessible par un autre objet. Dans l’ordre pour un objet d’exposer ses tables des messages, sa classe doit dériver de `CMessageMap`.

ATL utilise `CMessageMap` contenu de support de windows et le chaînage de carte dynamique des messages. Par exemple, toute classe qui contient un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objet doit dériver de `CMessageMap`. Le code suivant provient de la [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) exemple. Via [CComControl](../../atl/reference/ccomcontrol-class.md), le `CAtlEdit` classe dérive automatiquement `CMessageMap`.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Étant donné que la fenêtre de relation contenant-contenue, `m_EditCtrl`, utilise une table des messages dans la classe de conteneur, `CAtlEdit` dérive `CMessageMap`.

Pour plus d’informations sur les tables des messages, consultez [tables des messages](../../atl/message-maps-atl.md) dans l’article « Classes de fenêtre ATL ».

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage

Accède à la table des messages identifiée par *dwMsgMapID* dans un `CMessageMap`-classe dérivée.

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
[in] Le handle vers la fenêtre de réception du message.

*uMsg*<br/>
[in] Le message est envoyé à la fenêtre.

*wParam*<br/>
[in] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[in] Informations supplémentaires spécifiques au message.

*lResult*<br/>
[out] Le résultat du traitement du message.

*dwMsgMapID*<br/>
[in] Identificateur de la table des messages qui traitera le message. La table des messages par défaut, déclaré avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est identifié par 0. Une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifié par `msgMapID`.

### <a name="return-value"></a>Valeur de retour

TRUE si le message est entièrement géré ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Appelée par la procédure de fenêtre un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) de l’objet d’un objet qui est dynamiquement le chaînage des ou à la table des messages.

## <a name="see-also"></a>Voir aussi

[CDynamicChain, classe](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
