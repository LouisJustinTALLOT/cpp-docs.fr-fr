---
title: CMessageMap, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae6f41c2e8e8d142ee143d7ba0829751e1c230a3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572357"
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
 *hWnd*  
 [in] Le handle vers la fenêtre de réception du message.  
  
 *uMsg*  
 [in] Le message est envoyé à la fenêtre.  
  
 *wParam*  
 [in] Informations supplémentaires spécifiques au message.  
  
 *lParam*  
 [in] Informations supplémentaires spécifiques au message.  
  
 *lResult*  
 [out] Le résultat du traitement du message.  
  
 *dwMsgMapID*  
 [in] Identificateur de la table des messages qui traitera le message. La table des messages par défaut, déclaré avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est identifié par 0. Une autre table des messages déclarée avec [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifié par `msgMapID`.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le message est entièrement géré ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Appelée par la procédure de fenêtre un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) de l’objet d’un objet qui est dynamiquement le chaînage des ou à la table des messages.  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicChain, classe](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
