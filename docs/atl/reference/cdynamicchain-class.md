---
title: Classe CDynamicChain
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327036"
---
# <a name="cdynamicchain-class"></a>Classe CDynamicChain

Cette classe fournit des méthodes de soutien à l’enchaînement dynamique des cartes de messages.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDynamicChain
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Constructeur.|
|[CDynamicChain::CDynamicChain](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Dirige un message Windows vers la carte de message d’un autre objet.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Supprime une entrée de carte de message de la collection.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Ajoute une entrée de carte de message à la collection ou modifie une entrée existante.|

## <a name="remarks"></a>Notes

`CDynamicChain`gère une collection de cartes de messages, permettant de diriger un message Windows, au moment de l’exécution, vers la carte de message d’un autre objet.

Pour ajouter de la prise en charge de l’enchaînement dynamique des cartes de messages, faites ce qui suit :

- Dérivez votre `CDynamicChain`classe de . Dans la carte des messages, spécifiez la [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro pour enchaîner à la carte de message par défaut d’un autre objet.

- Dérivez chaque classe que vous voulez enchaîner à partir de [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`permet à un objet d’exposer ses cartes de message à d’autres objets.

- Appelez `CDynamicChain::SetChainEntry` pour identifier l’objet et la carte de message que vous souhaitez enchaîner.

Supposons, par exemple, que votre classe soit définie comme suit :

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Le client `CMyWindow::SetChainEntry`appelle alors :

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

où `chainedObj` est l’objet enchaîné et est `CMessageMap`un exemple d’une classe dérivée de . Maintenant, `myCtl` si reçoit un message qui `OnPaint` `OnSetFocus`n’est pas manipulé `chainedObj`par ou , la procédure de fenêtre dirige le message à la carte de message par défaut de '.

Pour plus d’informations sur la chaîne de cartes de message, voir [Cartes de message](../../atl/message-maps-atl.md) dans l’article "ATL Window Classes."

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamicChain::CallChain

Dirige le message Windows vers la carte de message d’un autre objet.

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>Paramètres

*dwChainID dwChainID*<br/>
[dans] L’identifiant unique associé à l’objet enchaîné et à sa carte de message.

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

### <a name="return-value"></a>Valeur de retour

VRAI si le message est entièrement traité; autrement, FALSE.

### <a name="remarks"></a>Notes

Pour que la `CallChain`procédure de fenêtre invoque, vous devez spécifier la [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro dans votre carte de message. Par exemple, voir la vue d’ensemble [CDynamicChain.](../../atl/reference/cdynamicchain-class.md)

`CallChain`nécessite un appel précédent à [SetChainEntry](#setchainentry) pour associer la valeur *dwChainID* à un objet et à sa carte de message.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>CDynamicChain::CDynamicChain

Constructeur.

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>CDynamicChain::CDynamicChain

Destructeur.

```
~CDynamicChain();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamicChain::RemoveChainEntry

Supprime la carte de message spécifiée de la collection.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Paramètres

*dwChainID dwChainID*<br/>
[dans] L’identifiant unique associé à l’objet enchaîné et à sa carte de message. Vous définissez à l’origine cette valeur par un appel à [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Valeur de retour

VRAI si la carte de message est supprimée avec succès de la collection. Dans le cas contraire, la valeur est FALSE.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamicChain::SetChainEntry

Ajoute la carte de message spécifiée à la collection.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Paramètres

*dwChainID dwChainID*<br/>
[dans] L’identifiant unique associé à l’objet enchaîné et à sa carte de message.

*pObject*<br/>
[dans] Un pointeur à l’objet enchaîné déclarant la carte de message. Cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[dans] L’identifiant de la carte de message dans l’objet enchaîné. La valeur par défaut est de 0, ce qui identifie la carte de message par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour spécifier une carte de message alternative déclarée avec `msgMapID` [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), passez .

### <a name="return-value"></a>Valeur de retour

VRAI si la carte de message est ajoutée avec succès à la collection. Dans le cas contraire, la valeur est FALSE.

### <a name="remarks"></a>Notes

Si la valeur *dwChainID* existe déjà dans la collection, son objet associé et la carte des messages sont remplacés par *pObject* et *dwMsgMapID*, respectivement. Sinon, une nouvelle entrée est ajoutée.

## <a name="see-also"></a>Voir aussi

[Classe CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
