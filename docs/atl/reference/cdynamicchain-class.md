---
title: Classe de CDynamicChain | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs:
- C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f57da02b764c1cbce6a97ecbea8aa84e4ffcce9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicchain-class"></a>Classe de CDynamicChain
Cette classe fournit des méthodes de prise en charge le chaînage dynamique des tables des messages.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
|[CDynamicChain::CallChain](#callchain)|Indique un message Windows à la table des messages d’un autre objet.|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Supprime une entrée de mappage de message de la collection.|  
|[CDynamicChain::SetChainEntry](#setchainentry)|Ajoute une entrée de mappage de message à la collection ou modifie une entrée existante.|  
  
## <a name="remarks"></a>Notes  
 `CDynamicChain`gère une collection de tables des messages, l’activation d’un message Windows à diriger, au moment de l’exécution à la table des messages d’un autre objet.  
  
 Pour prendre en charge le chaînage dynamique des tables des messages, procédez comme suit :  
  
-   Dérivez votre classe de `CDynamicChain`. Dans la table des messages, spécifiez la [macro CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro en chaîne de la table des messages par défaut d’un autre objet.  
  
-   Dériver de chaque classe que vous souhaitez figure dans la chaîne à partir de [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`permet à un objet d’exposer ses tables des messages à d’autres objets.  
  
-   Appelez `CDynamicChain::SetChainEntry` pour identifier l’objet et mapper les messages vous souhaitez de la chaîne.  
  
 Par exemple, supposons que votre classe est définie comme suit :  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 Le client appelle ensuite `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 où `chainedObj` est l’objet de chaîne et est une instance d’une classe dérivée de `CMessageMap`. Maintenant, si `myCtl` reçoit un message qui n’est pas géré par `OnPaint` ou `OnSetFocus`, la procédure de fenêtre achemine le message vers `chainedObj`de table des messages par défaut.  
  
 Pour plus d’informations sur le chaînage de mappage de message, consultez [tables des messages](../../atl/message-maps-atl.md) dans l’article « Classes de fenêtre ATL ».  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlwin.h  
  
##  <a name="callchain"></a>CDynamicChain::CallChain  
 Dirige le message Windows à la table des messages d’un autre objet.  
  
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
 `dwChainID`  
 [in] Identificateur unique associé à l’objet chaînée et sa table des messages.  
  
 `hWnd`  
 [in] Descripteur de la fenêtre de réception du message.  
  
 `uMsg`  
 [in] Le message est envoyé à la fenêtre.  
  
 `wParam`  
 [in] Plus d’informations spécifique au message.  
  
 `lParam`  
 [in] Plus d’informations spécifique au message.  
  
 `lResult`  
 [out] Le résultat du traitement du message.  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si le message est entièrement traité ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Pour appeler la procédure de fenêtre `CallChain`, vous devez spécifier le [macro CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro dans votre table des messages. Pour obtenir un exemple, consultez la [CDynamicChain](../../atl/reference/cdynamicchain-class.md) vue d’ensemble.  
  
 `CallChain`nécessite un appel précédent à [SetChainEntry](#setchainentry) pour associer le `dwChainID` valeur avec un objet et sa table des messages.  
  
##  <a name="cdynamicchain"></a>CDynamicChain::CDynamicChain  
 Constructeur.  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>CDynamicChain :: ~ CDynamicChain  
 Destructeur.  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources attribuées.  
  
##  <a name="removechainentry"></a>CDynamicChain::RemoveChainEntry  
 Supprime la table des messages spécifié de la collection.  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwChainID`  
 [in] Identificateur unique associé à l’objet chaînée et sa table des messages. Vous définissez à l’origine de cette valeur via un appel à [SetChainEntry](#setchainentry).  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la table des messages est correctement supprimée de la collection. Dans le cas contraire, **FALSE**.  
  
##  <a name="setchainentry"></a>CDynamicChain::SetChainEntry  
 Ajoute la table des messages spécifié à la collection.  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwChainID`  
 [in] Identificateur unique associé à l’objet chaînée et sa table des messages.  
  
 `pObject`  
 [in] Pointeur vers l’objet chaînée déclaration de la table des messages. Cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] Identificateur de la table des messages dans l’objet chaînée. La valeur par défaut est 0, qui identifie la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour spécifier une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), passer `msgMapID`.  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la table des messages est correctement ajoutée à la collection. Dans le cas contraire, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Si le `dwChainID` valeur existe déjà dans la collection, son objet associé et la table des messages sont remplacés par `pObject` et `dwMsgMapID`, respectivement. Sinon, une nouvelle entrée est ajoutée.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
