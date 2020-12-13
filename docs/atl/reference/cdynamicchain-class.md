---
description: 'En savoir plus sur : classe CDynamicChain'
title: CDynamicChain, classe
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
ms.openlocfilehash: 5ada99b519900150afa2143fb1527245797fed98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141815"
---
# <a name="cdynamicchain-class"></a>CDynamicChain, classe

Cette classe fournit des méthodes qui prennent en charge le chaînage dynamique des tables des messages.

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
|[CDynamicChain :: ~ CDynamicChain](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Dirige un message Windows vers la table des messages d’un autre objet.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Supprime une entrée de la table des messages de la collection.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Ajoute une entrée de table des messages à la collection ou modifie une entrée existante.|

## <a name="remarks"></a>Notes

`CDynamicChain` gère une collection de tables de messages, ce qui permet de diriger un message Windows, au moment de l’exécution, vers la table des messages d’un autre objet.

Pour ajouter la prise en charge du Chaînage dynamique des tables de messages, procédez comme suit :

- Dérivez votre classe de `CDynamicChain` . Dans la table des messages, spécifiez la macro [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) à lier à la table des messages par défaut d’un autre objet.

- Dérivez chaque classe à partir de laquelle vous souhaitez effectuer une chaîne à partir de [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap` permet à un objet d’exposer ses tables de messages à d’autres objets.

- Appelez `CDynamicChain::SetChainEntry` pour identifier l’objet et la table de messages à utiliser pour la chaîne.

Par exemple, supposons que votre classe soit définie comme suit :

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Le client appelle ensuite `CMyWindow::SetChainEntry` :

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

où `chainedObj` est l’objet chaîné et est une instance d’une classe dérivée de `CMessageMap` . Désormais, si `myCtl` reçoit un message qui n’est pas géré par `OnPaint` ou `OnSetFocus` , la procédure de fenêtre dirige le message vers la `chainedObj` table des messages par défaut de.

Pour plus d’informations sur le chaînage des tables de messages, consultez [tables des messages](../../atl/message-maps-atl.md) dans l’article « classes de fenêtres ATL ».

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a> CDynamicChain::CallChain

Dirige le message Windows vers la table des messages d’un autre objet.

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

*dwChainID*<br/>
dans Identificateur unique associé à l’objet chaîné et à sa table des messages.

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

### <a name="return-value"></a>Valeur renvoyée

TRUE si le message est entièrement traité ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Pour que la procédure de fenêtre appelle `CallChain` , vous devez spécifier la macro [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) dans votre table des messages. Pour obtenir un exemple, consultez la vue d’ensemble de [CDynamicChain](../../atl/reference/cdynamicchain-class.md) .

`CallChain` requiert un appel précédent à [SetChainEntry](#setchainentry) pour associer la valeur *dwChainID* à un objet et à sa table des messages.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a> CDynamicChain::CDynamicChain

Constructeur.

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a> CDynamicChain :: ~ CDynamicChain

Destructeur.

```
~CDynamicChain();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a> CDynamicChain::RemoveChainEntry

Supprime la table des messages spécifiée de la collection.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Paramètres

*dwChainID*<br/>
dans Identificateur unique associé à l’objet chaîné et à sa table des messages. Vous définissez cette valeur à l’origine à l’aide d’un appel à [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Valeur renvoyée

TRUE si la table des messages a été correctement supprimée de la collection. Dans le cas contraire, la valeur est FALSE.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a> CDynamicChain::SetChainEntry

Ajoute la table des messages spécifiée à la collection.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Paramètres

*dwChainID*<br/>
dans Identificateur unique associé à l’objet chaîné et à sa table des messages.

*pObject*<br/>
dans Pointeur vers l’objet chaîné qui déclare la table des messages. Cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
dans Identificateur de la table des messages dans l’objet chaîné. La valeur par défaut est 0, qui identifie la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour spécifier une autre table des messages déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), Pass `msgMapID` .

### <a name="return-value"></a>Valeur renvoyée

TRUE si la table des messages est correctement ajoutée à la collection. Dans le cas contraire, la valeur est FALSE.

### <a name="remarks"></a>Notes

Si la valeur *dwChainID* existe déjà dans la collection, son objet et la table des messages associés sont remplacés par *pObject* et *dwMsgMapID*, respectivement. Dans le cas contraire, une nouvelle entrée est ajoutée.

## <a name="see-also"></a>Voir aussi

[CWindowImpl (classe)](../../atl/reference/cwindowimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
