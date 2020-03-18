---
title: Macros de table des messages (ATL)
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
ms.openlocfilehash: 42fdc7a3f09568b641229e897a2a493994a7ba8a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417592"
---
# <a name="message-map-macros-atl"></a>Macros de table des messages (ATL)

Ces macros définissent les entrées et les tables des messages.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Marque le début d’une autre table des messages.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Marque le début de la table des messages par défaut.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Chaîne à une autre table des messages dans la classe de base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Chaîne à une autre table des messages dans un membre de données de la classe.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Chaînes à la table des messages par défaut dans la classe de base.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Chaînes à la table des messages dans une autre classe au moment de l’exécution.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Chaîne à la table des messages par défaut dans un membre de données de la classe.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification.|
|[COMMAND_HANDLER](#command_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification et d’une plage contiguë d’identificateurs de contrôle.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction d’une plage contiguë d’identificateurs de contrôle.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implémente une table des messages vide.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Fournit un gestionnaire par défaut pour les messages réfléchis qui ne sont pas gérés dans le cas contraire.|
|[END_MSG_MAP](#end_msg_map)|Marque la fin d’une table des messages.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Transfère les messages de notification à la fenêtre parente.|
|[MESSAGE_HANDLER](#message_handler)|Mappe un message Windows à une fonction de gestionnaire.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mappe une plage contiguë de messages Windows à une fonction de gestionnaire.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction du code de notification.|
|[NOTIFY_HANDLER](#notify_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de contrôle.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction de l’identificateur de contrôle.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction du code de notification et d’une plage contiguë d’identificateurs de contrôle.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Reflète les messages de notification à la fenêtre qui les a envoyés.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction du code de notification.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction du code de notification et d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction du code de notification.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de contrôle.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction de l’identificateur de contrôle.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction du code de notification et d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction d’une plage contiguë d’identificateurs de contrôle.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="alt_msg_map"></a>ALT_MSG_MAP

Marque le début d’une autre table des messages.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Paramètres

*msgMapID*<br/>
dans Identificateur de la table des messages.

### <a name="remarks"></a>Notes

ATL identifie chaque table des messages par un nombre. La table des messages par défaut (déclarée avec la macro BEGIN_MSG_MAP) est identifiée par 0. Une autre table des messages est identifiée par *msgMapID*.

Les tables des messages sont utilisées pour traiter les messages envoyés à une fenêtre. Par exemple, [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vous permet de spécifier l’identificateur d’une table des messages dans l’objet conteneur. [CContainedWindow :: WindowProc](ccontainedwindowt-class.md#windowproc) utilise ensuite cette table des messages pour diriger les messages de la fenêtre contenue vers la fonction de gestionnaire appropriée ou vers une autre table des messages. Pour obtenir la liste des macros qui déclarent des fonctions de gestionnaire, consultez [BEGIN_MSG_MAP](#begin_msg_map).

Commencez toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer des tables de messages secondaires suivantes.

La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Notez qu’il y a toujours exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

L’exemple suivant illustre la table des messages par défaut et une autre table des messages de remplacement, chacun contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux tables de messages de remplacement. La table des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="begin_msg_map"></a>BEGIN_MSG_MAP

Marque le début de la table des messages par défaut.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
dans Nom de la classe contenant la table des messages.

### <a name="remarks"></a>Notes

[CWindowImpl :: WindowProc](cwindowimpl-class.md#windowproc) utilise la table des messages par défaut pour traiter les messages envoyés à la fenêtre. La table des messages dirige les messages vers la fonction de gestionnaire appropriée ou vers une autre table des messages.

Les macros suivantes mappent un message à une fonction de gestionnaire. Cette fonction doit être définie dans *les*.

|Macro|Description|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Mappe un message Windows à une fonction de gestionnaire.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Mappe une plage contiguë de messages Windows à une fonction de gestionnaire.|
|[COMMAND_HANDLER](#command_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_CODE_HANDLER](#command_handler)|Mappe un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Mappe une plage contiguë de messages WM_COMMAND à une fonction de gestionnaire, en fonction de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[NOTIFY_HANDLER](#notify_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de contrôle.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction de l’identificateur de contrôle.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Mappe un message WM_NOTIFY à une fonction de gestionnaire, en fonction du code de notification.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Mappe une plage contiguë de messages WM_NOTIFY à une fonction de gestionnaire, en fonction de l’identificateur de contrôle.|

Les macros suivantes dirigent les messages vers une autre table des messages. Ce processus est appelé « chaînage ».

|Macro|Description|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Chaînes à la table des messages par défaut dans la classe de base.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Chaîne à la table des messages par défaut dans un membre de données de la classe.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Chaîne à une autre table des messages dans la classe de base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Chaîne à une autre table des messages dans un membre de données de la classe.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Chaîne à la table des messages par défaut dans une autre classe au moment de l’exécution.|

Les macros suivantes dirigent les messages « reflétés » à partir de la fenêtre parente. Par exemple, un contrôle envoie normalement des messages de notification à sa fenêtre parente pour traitement, mais la fenêtre parente peut répercuter le message dans le contrôle.

|Macro|Description|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction du code de notification.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Mappe un message de WM_COMMAND réfléchi à une fonction de gestionnaire, en fonction du code de notification et d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction du code de notification et de l’identificateur de contrôle.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction de l’identificateur de contrôle.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction du code de notification.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction d’une plage contiguë d’identificateurs de contrôle.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Mappe un message de WM_NOTIFY réfléchi à une fonction de gestionnaire, en fonction du code de notification et d’une plage contiguë d’identificateurs de contrôle.|

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Lorsqu’un objet `CMyExtWindow` reçoit un message de WM_PAINT, le message est dirigé vers `CMyExtWindow::OnPaint` pour le traitement réel. Si `OnPaint` indique que le message nécessite un traitement supplémentaire, le message est ensuite dirigé vers la table des messages par défaut dans `CMyBaseWindow`.

En plus de la table des messages par défaut, vous pouvez définir une autre table des messages avec [ALT_MSG_MAP](#alt_msg_map). Commencez toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer des tables de messages secondaires suivantes. L’exemple suivant illustre la table des messages par défaut et une autre table des messages de remplacement, chacun contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux tables de messages de remplacement. La table des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Notez qu’il y a toujours exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Paramètres

*theChainClass*<br/>
dans Nom de la classe de base contenant la table des messages.

*msgMapID*<br/>
dans Identificateur de la table des messages.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_ALT dirige les messages vers une autre table des messages dans une classe de base. Vous devez avoir déclaré cette table de messages de remplacement avec [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Pour diriger les messages vers la table des messages par défaut d’une classe de base (déclarée avec [BEGIN_MSG_MAP](#begin_msg_map)), utilisez CHAIN_MSG_MAP. Pour obtenir un exemple, consultez [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
>  Commencez toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Paramètres

*theChainMember*<br/>
dans Nom du membre de données contenant la table des messages.

*msgMapID*<br/>
dans Identificateur de la table des messages.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_ALT_MEMBER dirige les messages vers une autre table des messages d’un membre de données. Vous devez avoir déclaré cette table de messages de remplacement avec [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Pour diriger les messages vers la table des messages par défaut d’un membre de données (déclarée avec [BEGIN_MSG_MAP](#begin_msg_map)), utilisez CHAIN_MSG_MAP_MEMBER. Pour obtenir un exemple, consultez [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
>  Commencez toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="chain_msg_map"></a>CHAIN_MSG_MAP

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Paramètres

*theChainClass*<br/>
dans Nom de la classe de base contenant la table des messages.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP dirige les messages vers la table des messages par défaut d’une classe de base (déclarée avec [BEGIN_MSG_MAP](#begin_msg_map)). Pour diriger les messages vers la table des messages de remplacement d’une classe de base (déclarée avec [ALT_MSG_MAP](#alt_msg_map)), utilisez [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
>  Commencez toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Cet exemple illustre les éléments suivants :

- Si une procédure de fenêtre utilise la table des messages par défaut de `CMyClass`et que `OnPaint` ne gère pas un message, le message est dirigé vers la table des messages par défaut de `CMyBaseClass`pour traitement.

- Si une procédure de fenêtre utilise la première table des messages de remplacement dans `CMyClass`, tous les messages sont dirigés vers la table des messages par défaut de `CMyBaseClass`.

- Si une procédure de fenêtre utilise `CMyClass`deuxième table des messages de remplacement et que `OnChar` ne gère pas un message, le message est dirigé vers la table des messages alternatifs spécifiée dans `CMyBaseClass`. `CMyBaseClass` devez avoir déclaré cette table des messages avec ALT_MSG_MAP (1).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Paramètres

*dynaChainID*<br/>
dans Identificateur unique de la table des messages d’un objet.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_DYNAMIC dirige les messages au moment de l’exécution vers la table des messages par défaut d’un autre objet. L’objet et sa table des messages sont associés à *dynaChainID*, que vous définissez par le biais de [CDynamicChain :: SetChainEntry](cdynamicchain-class.md#setchainentry). Vous devez dériver votre classe de `CDynamicChain` pour pouvoir utiliser CHAIN_MSG_MAP_DYNAMIC. Pour obtenir un exemple, consultez la vue d’ensemble de [CDynamicChain](../../atl/reference/cdynamicchain-class.md) .

> [!NOTE]
>  Commencez toujours une table des messages avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Définit une entrée dans une table des messages.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Paramètres

*theChainMember*<br/>
dans Nom du membre de données contenant la table des messages.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_MEMBER dirige les messages vers la table des messages par défaut d’un membre de données (déclarée avec [BEGIN_MSG_MAP](#begin_msg_map)). Pour diriger les messages vers la table des messages de remplacement d’un membre de données (déclarée avec [ALT_MSG_MAP](#alt_msg_map)), utilisez [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
>  Commencez toujours une table des messages avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec ALT_MSG_MAP. La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Cet exemple illustre les éléments suivants :

- Si une procédure de fenêtre utilise la table des messages par défaut de `CMyClass`et que `OnPaint` ne gère pas un message, le message est dirigé vers la table des messages par défaut de `m_obj`pour traitement.

- Si une procédure de fenêtre utilise la première table des messages de remplacement dans `CMyClass`, tous les messages sont dirigés vers la table des messages par défaut de `m_obj`.

- Si une procédure de fenêtre utilise `CMyClass`deuxième table des messages de remplacement et que `OnChar` ne gère pas un message, le message est dirigé vers l’autre table des messages de `m_obj`spécifiée. La classe `CMyContainedClass` doit avoir déclaré cette table des messages avec ALT_MSG_MAP (1).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe un message [WM_COMMAND](/windows/win32/menurc/wm-command) basé uniquement sur le code de notification.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Paramètres

*code*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="command_handler"></a>COMMAND_HANDLER

Définit une entrée dans une table des messages.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

*code*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

COMMAND_HANDLER mappe un message [WM_COMMAND](/windows/win32/menurc/wm-command) à la fonction de gestionnaire spécifiée, en fonction du code de notification et de l’identificateur de contrôle. Par exemple :

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Toute fonction spécifiée dans une macro COMMAND_HANDLER doit être définie comme suit :

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

La table des messages définit `bHandled` à TRUE avant l’appel de `CommandHandler`. Si `CommandHandler` ne gère pas complètement le message, il doit affecter à `bHandled` la valeur FALSe pour indiquer que le message doit être traité ultérieurement.

> [!NOTE]
>  Commencez toujours une table des messages avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec [ALT_MSG_MAP](#alt_msg_map). La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

En plus de COMMAND_HANDLER, vous pouvez utiliser [MESSAGE_HANDLER](#message_handler) pour mapper un WM_COMMAND message sans tenir compte d’un identificateur ou d’un code. Dans ce cas, `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` dirige tous les messages WM_COMMAND vers `OnHandlerFunction`.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="command_id_handler"></a>COMMAND_ID_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe un message [WM_COMMAND](/windows/win32/menurc/wm-command) uniquement en fonction de l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur de l’élément de menu, du contrôle ou de l’accélérateur qui envoie le message.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Semblable à [COMMAND_RANGE_HANDLER](#command_range_handler), mais mappe [WM_COMMAND](/windows/win32/menurc/wm-command) messages avec un code de notification spécifique d’une plage de contrôles à une fonction de gestionnaire unique.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*code*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur qui envoie le message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais mappe [WM_COMMAND](/windows/win32/menurc/wm-command) messages d’une plage de contrôles à une fonction de gestionnaire unique.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur de l’élément de menu, du contrôle ou de l’accélérateur qui envoie le message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Déclare une table des messages vide.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Notes

DECLARE_EMPTY_MSG_MAP est une macro pratique qui appelle les macros [BEGIN_MSG_MAP](#begin_msg_map) et [END_MSG_MAP](#end_msg_map) pour créer une table des messages vide :

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

##  <a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Fournit un gestionnaire par défaut pour la fenêtre enfant (contrôle) qui recevra les messages reflétés ; le gestionnaire passera correctement les messages non gérés à `DefWindowProc`.

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="end_msg_map"></a>END_MSG_MAP

Marque la fin d’une table des messages.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Notes

Utilisez toujours la macro [BEGIN_MSG_MAP](#begin_msg_map) pour marquer le début d’une table des messages. Utilisez [ALT_MSG_MAP](#alt_msg_map) pour déclarer d’autres tables de messages secondaires.

Notez qu’il y a toujours exactement une instance de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

L’exemple suivant illustre la table des messages par défaut et une autre table des messages de remplacement, chacun contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux tables de messages de remplacement. La table des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Transfère les messages de notification à la fenêtre parente.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Notes

Spécifiez cette macro dans le cadre de votre table des messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="message_handler"></a>MESSAGE_HANDLER

Définit une entrée dans une table des messages.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Paramètres

*fragment*<br/>
dans Message Windows.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

MESSAGE_HANDLER mappe un message Windows à la fonction de gestionnaire spécifiée.

Toute fonction spécifiée dans une macro MESSAGE_HANDLER doit être définie comme suit :

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

La table des messages définit `bHandled` à TRUE avant l’appel de `MessageHandler`. Si `MessageHandler` ne gère pas complètement le message, il doit affecter à `bHandled` la valeur FALSe pour indiquer que le message doit être traité ultérieurement.

> [!NOTE]
>  Commencez toujours une table des messages avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec [ALT_MSG_MAP](#alt_msg_map). La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

En plus de MESSAGE_HANDLER, vous pouvez utiliser [COMMAND_HANDLER](#command_handler) et [NOTIFY_HANDLER](#notify_handler) pour mapper les messages [WM_COMMAND](/windows/win32/menurc/wm-command) et [WM_NOTIFY](/windows/win32/controls/wm-notify) , respectivement.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Semblable à [MESSAGE_HANDLER](#message_handler), mais mappe une plage de messages Windows à une fonction de gestionnaire unique.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Paramètres

*msgFirst*<br/>
dans Marque le début d’une plage de messages contiguë.

*msgLast*<br/>
dans Marque la fin d’une plage de messages contiguë.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe un message [WM_NOTIFY](/windows/win32/controls/wm-notify) basé uniquement sur le code de notification.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Paramètres

*cd*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="notify_handler"></a>NOTIFY_HANDLER

Définit une entrée dans une table des messages.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur du contrôle qui envoie le message.

*cd*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

NOTIFY_HANDLER mappe un message [WM_NOTIFY](/windows/win32/controls/wm-notify) à la fonction de gestionnaire spécifiée, en fonction du code de notification et de l’identificateur de contrôle.

Toute fonction spécifiée dans une macro NOTIFY_HANDLER doit être définie comme suit :

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

La table des messages définit `bHandled` à TRUE avant l’appel de `NotifyHandler`. Si `NotifyHandler` ne gère pas complètement le message, il doit affecter à `bHandled` la valeur FALSe pour indiquer que le message doit être traité ultérieurement.

> [!NOTE]
>  Commencez toujours une table des messages avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des tables de messages secondaires suivantes avec [ALT_MSG_MAP](#alt_msg_map). La macro [END_MSG_MAP](#end_msg_map) marque la fin de la table des messages. Chaque table des messages doit avoir une seule instance de BEGIN_MSG_MAP et END_MSG_MAP.

En plus de NOTIFY_HANDLER, vous pouvez utiliser [MESSAGE_HANDLER](#message_handler) pour mapper un WM_NOTIFY message sans tenir compte d’un identificateur ou d’un code. Dans ce cas, `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` dirige tous les messages WM_NOTIFY vers `OnHandlerFunction`.

Pour plus d’informations sur l’utilisation des tables de messages dans ATL, consultez [tables des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe un message [WM_NOTIFY](/windows/win32/controls/wm-notify) uniquement en fonction de l’identificateur du contrôle.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur du contrôle qui envoie le message.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Semblable à [NOTIFY_RANGE_HANDLER](#notify_range_handler), mais mappe [WM_NOTIFY](/windows/win32/controls/wm-notify) messages avec un code de notification spécifique d’une plage de contrôles à une fonction de gestionnaire unique.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*cd*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur du contrôle qui envoie le message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais mappe [WM_NOTIFY](/windows/win32/controls/wm-notify) messages d’une plage de contrôles à une fonction de gestionnaire unique.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identificateur du contrôle qui envoie le message.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Reflète les messages de notification à la fenêtre enfant (contrôle) qui les a envoyés.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Notes

Spécifiez cette macro dans le cadre de la table des messages de la fenêtre parente.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Semblable à [COMMAND_CODE_HANDLER](#command_code_handler), mais les commandes Maps sont reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Paramètres

*code*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais les commandes Maps sont reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

*code*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Semblable à [COMMAND_ID_HANDLER](#command_id_handler), mais les commandes Maps sont reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Semblable à [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), mais les commandes Maps sont reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*code*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Semblable à [COMMAND_RANGE_HANDLER](#command_range_handler), mais les commandes Maps sont reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Semblable à [NOTIFY_CODE_HANDLER](#notify_code_handler), mais les notifications de mappage sont reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Paramètres

*cd*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais les notifications de mappage sont reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

*cd*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Semblable à [NOTIFY_ID_HANDLER](#notify_id_handler), mais les notifications de mappage sont reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identificateur de l’élément de menu, du contrôle ou de l’accélérateur.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Semblable à [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), mais les notifications de mappage sont reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*cd*<br/>
dans Code de notification.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Semblable à [NOTIFY_RANGE_HANDLER](#notify_range_handler), mais les notifications de mappage sont reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
dans Marque le début d’une plage contiguë d’identificateurs de contrôle.

*idLast*<br/>
dans Marque la fin d’une plage contiguë d’identificateurs de contrôle.

*func*<br/>
dans Nom de la fonction de gestionnaire de messages.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
