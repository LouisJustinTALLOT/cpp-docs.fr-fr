---
title: Macros de mappage des messages (ATL)
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: bedef3a8563e27f72017720530e3b7addb78ec3d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290376"
---
# <a name="message-map-macros-atl"></a>Macros de mappage des messages (ATL)

Ces macros définissent des tables des messages et des entrées.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Marque le début d’une autre table des messages.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Marque le début de la table des messages par défaut.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Est lié à une autre table des messages dans la classe de base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Est lié à une autre table des messages dans un membre de données de la classe.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Est lié à la table des messages par défaut dans la classe de base.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Est lié à la table des messages dans une autre classe au moment de l’exécution.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Est lié à la table des messages par défaut dans un membre de données de la classe.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon le code de notification.|
|[COMMAND_HANDLER](#command_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon le code de notification et l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon le code de notification et une plage contiguë d’identificateurs de contrôle.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon une plage contiguë d’identificateurs de contrôle.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implémente un mappage de message vide.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Fournit un gestionnaire par défaut pour les messages réfléchis ne sont pas gérées dans le cas contraire.|
|[END_MSG_MAP](#end_msg_map)|Marque la fin d’une table des messages.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Transfère les messages de notification à la fenêtre parente.|
|[MESSAGE_HANDLER](#message_handler)|Mappe un message Windows à une fonction gestionnaire.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mappe une plage contiguë de Windows aux messages à une fonction gestionnaire.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon le code de notification.|
|[NOTIFY_HANDLER](#notify_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon le code de notification et l’identificateur du contrôle.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon l’identificateur du contrôle.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon le code de notification et une plage contiguë d’identificateurs de contrôle.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon une plage contiguë d’identificateurs de contrôle.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Reflète les messages de notification à la fenêtre qui les a envoyés.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon le code de notification.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon le code de notification et l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon le code de notification et une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon le code de notification.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon le code de notification et l’identificateur du contrôle.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon l’identificateur du contrôle.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon le code de notification et une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon une plage contiguë d’identificateurs de contrôle.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="alt_msg_map"></a>  ALT_MSG_MAP

Marque le début d’une autre table des messages.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Paramètres

*msgMapID*<br/>
[in] Identificateur de plan de message.

### <a name="remarks"></a>Notes

ATL identifie chaque mappage de message par un nombre. La table des messages par défaut (déclarée avec la macro BEGIN_MSG_MAP) est identifiée par 0. Une autre table des messages est identifiée par *msgMapID*.

Tables des messages sont utilisés pour traiter les messages envoyés à une fenêtre. Par exemple, [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vous permet de spécifier l’identificateur d’une table des messages dans l’objet conteneur. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) utilise ensuite cette table des messages pour diriger les messages de la fenêtre de relation contenant-contenu à la fonction gestionnaire approprié ou à une autre table des messages. Pour obtenir la liste des macros qui déclarent des fonctions gestionnaires, consultez [BEGIN_MSG_MAP](#begin_msg_map).

Commencent toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer les tables des messages de remplacement suivants.

Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Notez qu’il est toujours exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

L’exemple suivant montre la table des messages par défaut et une autre table des messages, chacun contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux mappages de messages de remplacement. La table des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="begin_msg_map"></a>  BEGIN_MSG_MAP

Marque le début de la table des messages par défaut.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
[in] Le nom de la classe contenant la table des messages.

### <a name="remarks"></a>Notes

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) utilise la table des messages par défaut pour traiter les messages envoyés à la fenêtre. La table des messages dirige les messages à la fonction gestionnaire approprié ou à une autre table des messages.

Les macros suivantes mappent un message à une fonction gestionnaire. Cette fonction doit être définie dans *theClass*.

|Macro|Description|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mappe un message Windows à une fonction gestionnaire.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mappe une plage contiguë de Windows aux messages à une fonction gestionnaire.|
|[COMMAND_HANDLER](#command_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon le code de notification et l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, selon le code de notification.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mappe une plage contiguë de WM_COMMAND aux messages à une fonction de gestionnaire, selon l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[NOTIFY_HANDLER](#notify_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon le code de notification et l’identificateur du contrôle.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon l’identificateur du contrôle.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, selon le code de notification.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mappe une plage contiguë de WM_NOTIFY aux messages à une fonction de gestionnaire, selon l’identificateur du contrôle.|

Les macros suivantes dirigent les messages vers une autre table des messages. Ce processus est appelé « chaînage ».

|Macro|Description|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Est lié à la table des messages par défaut dans la classe de base.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Est lié à la table des messages par défaut dans un membre de données de la classe.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Est lié à une autre table des messages dans la classe de base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Est lié à une autre table des messages dans un membre de données de la classe.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Est lié à la table des messages par défaut dans une autre classe au moment de l’exécution.|

Les macros suivantes dirigent les messages de « reflétées » à partir de la fenêtre parente. Par exemple, un contrôle normalement envoie des messages de notification à sa fenêtre parente pour traitement, mais la fenêtre parente peut refléter le message au contrôle.

|Macro|Description|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon le code de notification et l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon l’identificateur de l’élément de menu, un contrôle ou un accélérateur.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon le code de notification.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mappe un message WM_COMMAND réfléchi à une fonction de gestionnaire, selon le code de notification et une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon le code de notification et l’identificateur du contrôle.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon l’identificateur du contrôle.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon le code de notification.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mappe un message WM_NOTIFY réfléchi à une fonction de gestionnaire, selon le code de notification et une plage contiguë d’identificateurs de contrôle.|

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Quand un `CMyExtWindow` objet reçoit un message WM_PAINT, le message est dirigé vers `CMyExtWindow::OnPaint` pour le traitement réel. Si `OnPaint` indique le message nécessite un traitement supplémentaire, le message est ensuite dirigé vers la table des messages par défaut dans `CMyBaseWindow`.

En plus de la table des messages par défaut, vous pouvez définir une autre table des messages avec [ALT_MSG_MAP](#alt_msg_map). Commencent toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer les tables des messages de remplacement suivants. L’exemple suivant montre la table des messages par défaut et une autre table des messages, chacun contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux mappages de messages de remplacement. La table des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Notez qu’il est toujours exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="chain_msg_map_alt"></a>  CHAIN_MSG_MAP_ALT

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Paramètres

*theChainClass*<br/>
[in] Le nom de la classe de base contenant la table des messages.

*msgMapID*<br/>
[in] Identificateur de plan de message.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_ALT dirige les messages vers une autre table des messages dans une classe de base. Vous devez avez déclaré cette autre table des messages avec [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Pour diriger les messages vers la table des messages par défaut d’une classe de base (déclaré avec [BEGIN_MSG_MAP](#begin_msg_map)), utilisez CHAIN_MSG_MAP. Pour obtenir un exemple, consultez [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
>  Commencent toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec ALT_MSG_MAP. Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="chain_msg_map_alt_member"></a>  CHAIN_MSG_MAP_ALT_MEMBER

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Paramètres

*theChainMember*<br/>
[in] Le nom du membre de données contenant la table des messages.

*msgMapID*<br/>
[in] Identificateur de plan de message.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_ALT_MEMBER dirige les messages vers une autre table des messages dans un membre de données. Vous devez avez déclaré cette autre table des messages avec [ALT_MSG_MAP(msgMapID)](#alt_msg_map). Pour diriger les messages vers la table des messages d’un membre de données par défaut (déclaré avec [BEGIN_MSG_MAP](#begin_msg_map)), utilisez CHAIN_MSG_MAP_MEMBER. Pour obtenir un exemple, consultez [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
>  Commencent toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec ALT_MSG_MAP. Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="chain_msg_map"></a>  CHAIN_MSG_MAP

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Paramètres

*theChainClass*<br/>
[in] Le nom de la classe de base contenant la table des messages.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP dirige les messages vers la table des messages par défaut d’une classe de base (déclaré avec [BEGIN_MSG_MAP](#begin_msg_map)). Pour diriger les messages au mappage des messages de remplacement d’une classe de base (déclaré avec [ALT_MSG_MAP](#alt_msg_map)), utilisez [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
>  Commencent toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec ALT_MSG_MAP. Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Cet exemple illustre les éléments suivants :

- Si à l’aide d’une procédure de fenêtre `CMyClass`de table des messages par défaut et `OnPaint` ne pas handle d’un message, le message est dirigé vers `CMyBaseClass`de table des messages par défaut pour le traitement.

- Si une procédure de fenêtre à l’aide de la première table des messages secondaire dans `CMyClass`, tous les messages sont dirigés vers `CMyBaseClass`de table des messages par défaut.

- Si à l’aide d’une procédure de fenêtre `CMyClass`de mapper de deuxième message alternatifs et `OnChar` ne pas handle d’un message, le message est dirigé vers la table des messages de remplacement spécifié dans `CMyBaseClass`. `CMyBaseClass` doit avoir déclaré cette table des messages avec ALT_MSG_MAP(1).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="chain_msg_map_dynamic"></a>  CHAIN_MSG_MAP_DYNAMIC

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Paramètres

*dynaChainID*<br/>
[in] Identificateur unique pour la table des messages d’un objet.

### <a name="remarks"></a>Notes

Macro CHAIN_MSG_MAP_DYNAMIC dirige les messages, en cours d’exécution, à la table des messages par défaut dans un autre objet. L’objet et sa table des messages associés *dynaChainID*, que vous définissez via [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Vous devez dériver votre classe de `CDynamicChain` pour pouvoir utiliser la macro CHAIN_MSG_MAP_DYNAMIC. Pour obtenir un exemple, consultez le [CDynamicChain](../../atl/reference/cdynamicchain-class.md) vue d’ensemble.

> [!NOTE]
>  Toujours commencer avec une table des messages [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec ALT_MSG_MAP. Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="chain_msg_map_member"></a>  CHAIN_MSG_MAP_MEMBER

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Paramètres

*theChainMember*<br/>
[in] Le nom du membre de données contenant la table des messages.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_MEMBER dirige les messages vers la table des messages d’un membre de données par défaut (déclaré avec [BEGIN_MSG_MAP](#begin_msg_map)). Pour diriger les messages au mappage des messages de remplacement d’un membre de données (déclaré avec [ALT_MSG_MAP](#alt_msg_map)), utilisez [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
>  Commencent toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec ALT_MSG_MAP. Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Cet exemple illustre les éléments suivants :

- Si à l’aide d’une procédure de fenêtre `CMyClass`de table des messages par défaut et `OnPaint` ne pas handle d’un message, le message est dirigé vers `m_obj`de table des messages par défaut pour le traitement.

- Si une procédure de fenêtre à l’aide de la première table des messages secondaire dans `CMyClass`, tous les messages sont dirigés vers `m_obj`de table des messages par défaut.

- Si à l’aide d’une procédure de fenêtre `CMyClass`de mapper de deuxième message alternatifs et `OnChar` ne pas handle d’un message, le message est dirigé vers la table des messages de remplacement spécifié de `m_obj`. Classe `CMyContainedClass` cette table des messages avec ALT_MSG_MAP(1) est déclarée.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="command_code_handler"></a>  COMMAND_CODE_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe un [WM_COMMAND](/windows/desktop/menurc/wm-command) message basé uniquement sur le code de notification.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Paramètres

*code*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="command_handler"></a>  COMMAND_HANDLER

Définit une entrée dans une table des messages.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur de l’élément de menu, un contrôle ou un accélérateur.

*code*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

COMMAND_HANDLER mappe un [WM_COMMAND](/windows/desktop/menurc/wm-command) message à la fonction de gestionnaire spécifié, selon le code de notification et l’identificateur du contrôle. Exemple :

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

N’importe quelle fonction spécifiée dans une macro COMMAND_HANDLER doit être définie comme suit :

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

Les jeux de mappage de message `bHandled` sur TRUE avant `CommandHandler` est appelée. Si `CommandHandler` ne gère pas entièrement le message, il doit définir `bHandled` à FALSE pour indiquer que le message nécessite un traitement supplémentaire.

> [!NOTE]
>  Toujours commencer avec une table des messages [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec [ALT_MSG_MAP](#alt_msg_map). Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Outre COMMAND_HANDLER, vous pouvez utiliser [MESSAGE_HANDLER](#message_handler) pour mapper un message WM_COMMAND sans tenir compte d’un identificateur ou le code. Dans ce cas, `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` dirigera tous les messages WM_COMMAND `OnHandlerFunction`.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="command_id_handler"></a>  COMMAND_ID_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe un [WM_COMMAND](/windows/desktop/menurc/wm-command) basées sur des messages uniquement sur l’identificateur de l’élément de menu, un contrôle ou un accélérateur.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] Identificateur de l’élément de menu, le contrôle ou l’accélérateur d’envoi du message.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="command_range_code_handler"></a>  COMMAND_RANGE_CODE_HANDLER

Semblable à [COMMAND_RANGE_HANDLER](#command_range_handler), mais mappe [WM_COMMAND](/windows/desktop/menurc/wm-command) messages avec un code de notification spécifique à partir d’un éventail de contrôles à une seule fonction gestionnaire.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*code*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur de l’élément de menu, le contrôle ou l’accélérateur d’envoi du message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="command_range_handler"></a>  COMMAND_RANGE_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe [WM_COMMAND](/windows/desktop/menurc/wm-command) messages à partir d’un éventail de contrôles à une seule fonction gestionnaire.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur de l’élément de menu, le contrôle ou l’accélérateur d’envoi du message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="declare_empty_msg_map"></a>  DECLARE_EMPTY_MSG_MAP

Déclare un mappage de message vide.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Notes

DECLARE_EMPTY_MSG_MAP est une macro pratique qui appelle les macros [BEGIN_MSG_MAP](#begin_msg_map) et [END_MSG_MAP](#end_msg_map) pour créer une table des messages vide :

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>  DEFAULT_REFLECTION_HANDLER

Fournit un gestionnaire par défaut pour la fenêtre enfant (contrôle) qui recevra les messages ; réfléchis le gestionnaire passe correctement des messages non gérées à `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="end_msg_map"></a>  END_MSG_MAP

Marque la fin d’une table des messages.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Notes

Utilisez toujours le [BEGIN_MSG_MAP](#begin_msg_map) macro pour marquer le début d’une table des messages. Utilisez [ALT_MSG_MAP](#alt_msg_map) pour déclarer les tables des messages de remplacement suivants.

Notez qu’il est toujours exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

L’exemple suivant montre la table des messages par défaut et une autre table des messages, chacun contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux mappages de messages de remplacement. La table des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="forward_notifications"></a>  FORWARD_NOTIFICATIONS

Transfère les messages de notification à la fenêtre parente.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Notes

Spécifiez cette macro en tant que partie de votre table des messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="message_handler"></a>  MESSAGE_HANDLER

Définit une entrée dans une table des messages.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Paramètres

*msg*<br/>
[in] Le message Windows.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

MESSAGE_HANDLER mappe un message Windows à la fonction de gestionnaire spécifié.

N’importe quelle fonction spécifiée dans une macro MESSAGE_HANDLER doit être définie comme suit :

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

Les jeux de mappage de message `bHandled` sur TRUE avant `MessageHandler` est appelée. Si `MessageHandler` ne gère pas entièrement le message, il doit définir `bHandled` à FALSE pour indiquer que le message nécessite un traitement supplémentaire.

> [!NOTE]
>  Toujours commencer avec une table des messages [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec [ALT_MSG_MAP](#alt_msg_map). Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Outre MESSAGE_HANDLER, vous pouvez utiliser [COMMAND_HANDLER](#command_handler) et [NOTIFY_HANDLER](#notify_handler) pour mapper [WM_COMMAND](/windows/desktop/menurc/wm-command) et [WM_NOTIFY](/windows/desktop/controls/wm-notify) messages , respectivement.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="message_range_handler"></a>  MESSAGE_RANGE_HANDLER

Semblable à [MESSAGE_HANDLER](#message_handler), mais correspond à une plage de Windows des messages à une seule fonction gestionnaire.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Paramètres

*msgFirst*<br/>
[in] Marque le début d’une plage contiguë de messages.

*msgLast*<br/>
[in] Marque la fin d’une plage contiguë de messages.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="notify_code_handler"></a>  NOTIFY_CODE_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe un [WM_NOTIFY](/windows/desktop/controls/wm-notify) message basé uniquement sur le code de notification.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Paramètres

*cd*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="notify_handler"></a>  NOTIFY_HANDLER

Définit une entrée dans une table des messages.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur du contrôle qui envoie le message.

*cd*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

NOTIFY_HANDLER mappe un [WM_NOTIFY](/windows/desktop/controls/wm-notify) message à la fonction de gestionnaire spécifié, selon le code de notification et l’identificateur du contrôle.

N’importe quelle fonction spécifiée dans une macro NOTIFY_HANDLER doit être définie comme suit :

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

Les jeux de mappage de message `bHandled` sur TRUE avant `NotifyHandler` est appelée. Si `NotifyHandler` ne gère pas entièrement le message, il doit définir `bHandled` à FALSE pour indiquer que le message nécessite un traitement supplémentaire.

> [!NOTE]
>  Toujours commencer avec une table des messages [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer les tables des messages de remplacement suivants avec [ALT_MSG_MAP](#alt_msg_map). Le [END_MSG_MAP](#end_msg_map) macro marque la fin de la table des messages. Chaque mappage de message doit avoir exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Outre NOTIFY_HANDLER, vous pouvez utiliser [MESSAGE_HANDLER](#message_handler) pour mapper un message WM_NOTIFY sans tenir compte d’un identificateur ou le code. Dans ce cas, `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` dirigera tous les messages WM_NOTIFY à `OnHandlerFunction`.

Pour plus d’informations sur l’utilisation des tables des messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="notify_id_handler"></a>  NOTIFY_ID_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe un [WM_NOTIFY](/windows/desktop/controls/wm-notify) basées sur des messages uniquement sur l’identificateur du contrôle.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur du contrôle qui envoie le message.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="notify_range_code_handler"></a>  NOTIFY_RANGE_CODE_HANDLER

Semblable à [NOTIFY_RANGE_HANDLER](#notify_range_handler), mais mappe [WM_NOTIFY](/windows/desktop/controls/wm-notify) messages avec un code de notification spécifique à partir d’un éventail de contrôles à une seule fonction gestionnaire.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*cd*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur du contrôle qui envoie le message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="notify_range_handler"></a>  NOTIFY_RANGE_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe [WM_NOTIFY](/windows/desktop/controls/wm-notify) messages à partir d’un éventail de contrôles à une seule fonction gestionnaire.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur du contrôle qui envoie le message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflect_notifications"></a>  REFLECT_NOTIFICATIONS

Reflète les messages de notification à la fenêtre enfant (contrôle) qui les a envoyés.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Notes

Spécifiez cette macro en tant que partie de la table des messages de la fenêtre parente.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_command_code_handler"></a>  REFLECTED_COMMAND_CODE_HANDLER

Semblable à [COMMAND_CODE_HANDLER](#command_code_handler), mais mappe des commandes réfléchies à partir de la fenêtre parente.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Paramètres

*code*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_command_handler"></a>  REFLECTED_COMMAND_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe des commandes réfléchies à partir de la fenêtre parente.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur de l’élément de menu, un contrôle ou un accélérateur.

*code*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_command_id_handler"></a>  REFLECTED_COMMAND_ID_HANDLER

Semblable à [COMMAND_ID_HANDLER](#command_id_handler), mais mappe des commandes réfléchies à partir de la fenêtre parente.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur de l’élément de menu, un contrôle ou un accélérateur.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_command_range_code_handler"></a>  REFLECTED_COMMAND_RANGE_CODE_HANDLER

Semblable à [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), mais mappe des commandes réfléchies à partir de la fenêtre parente.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*code*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_command_range_handler"></a>  REFLECTED_COMMAND_RANGE_HANDLER

Semblable à [COMMAND_RANGE_HANDLER](#command_range_handler), mais mappe des commandes réfléchies à partir de la fenêtre parente.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_notify_code_handler"></a>  REFLECTED_NOTIFY_CODE_HANDLER

Semblable à [NOTIFY_CODE_HANDLER](#notify_code_handler), mais mappe les notifications réfléchies à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Paramètres

*cd*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_notify_handler"></a>  REFLECTED_NOTIFY_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe les notifications réfléchies à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur de l’élément de menu, un contrôle ou un accélérateur.

*cd*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_notify_id_handler"></a>  REFLECTED_NOTIFY_ID_HANDLER

Semblable à [NOTIFY_ID_HANDLER](#notify_id_handler), mais mappe les notifications réfléchies à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
[in] L’identificateur de l’élément de menu, un contrôle ou un accélérateur.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_notify_range_code_handler"></a>  REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Semblable à [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), mais mappe les notifications réfléchies à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*cd*<br/>
[in] Le code de notification.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="reflected_notify_range_handler"></a>  REFLECTED_NOTIFY_RANGE_HANDLER

Semblable à [NOTIFY_RANGE_HANDLER](#notify_range_handler), mais mappe les notifications réfléchies à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[in] Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
[in] Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
[in] Le nom de la fonction de gestionnaire de messages.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
