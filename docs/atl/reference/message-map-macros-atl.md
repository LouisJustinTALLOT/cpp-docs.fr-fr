---
title: Message Map Macros (ATL)
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
ms.openlocfilehash: 157812fa6625869c86dd8a27156a2970a3dc8d4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326231"
---
# <a name="message-map-macros-atl"></a>Message Map Macros (ATL)

Ces macros définissent les cartes et les entrées des messages.

|||
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|Marque le début d’une carte de message alternative.|
|[BEGIN_MSG_MAP](#begin_msg_map)|Marque le début de la carte des messages par défaut.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Chaînes à une carte de message alternative dans la classe de base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Chaînes à une carte de message alternative dans un membre de données de la classe.|
|[CHAIN_MSG_MAP](#chain_msg_map)|Chaînes à la carte de message par défaut dans la classe de base.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Chaînes à la carte de message dans une autre classe au moment de l’exécution.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Chaînes à la carte de message par défaut dans un membre de données de la classe.|
|[COMMAND_CODE_HANDLER](#command_code_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, basé sur le code de notification.|
|[COMMAND_HANDLER](#command_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification et de l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, en fonction de l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, basé sur le code de notification et une gamme contigu d’identifiants de contrôle.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, basé sur une gamme contigu d’identifiants de contrôle.|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|Implémente une carte de message vide.|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|Fournit un gestionnaire par défaut pour les messages réfléchis qui ne sont pas traités autrement.|
|[END_MSG_MAP](#end_msg_map)|Marque la fin d’une carte de message.|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|Transmette les messages de notification à la fenêtre parente.|
|[MESSAGE_HANDLER](#message_handler)|Cartographiez un message Windows à une fonction de gestionnaire.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Cartographiez une gamme contigue de messages Windows à une fonction de gestionnaire.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, basé sur le code de notification.|
|[NOTIFY_HANDLER](#notify_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, basé sur le code de notification et l’identifiant de contrôle.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, en fonction de l’identifiant de contrôle.|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, basé sur le code de notification et une gamme contigu d’identifiants de contrôle.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, basé sur une gamme contigu d’identifiants de contrôle.|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|Reflète les messages de notification vers la fenêtre qui les a envoyés.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur le code de notification.|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur le code de notification et l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur le code de notification et une gamme contigu d’identifiants de contrôle.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur une gamme contigu d’identifiants de contrôle.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur le code de notification.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur le code de notification et l’identifiant de contrôle.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur l’identifiant de contrôle.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur le code de notification et une gamme contigu d’identifiants de contrôle.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur une gamme contigu d’identifiants de contrôle.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a>ALT_MSG_MAP

Marque le début d’une carte de message alternative.

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>Paramètres

*msgMapID msgMapID*<br/>
[dans] L’identifiant de carte de message.

### <a name="remarks"></a>Notes

ATL identifie chaque carte de message par un numéro. La carte de message par défaut (déclarée avec la macro BEGIN_MSG_MAP) est identifiée par 0. Une carte de message alternative est identifiée par *msgMapID*.

Les cartes de messages sont utilisées pour traiter les messages envoyés à une fenêtre. Par exemple, [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vous permet de spécifier l’identifiant d’une carte de message dans l’objet contenant. [CContainedWindow::WindowProc](ccontainedwindowt-class.md#windowproc) utilise ensuite cette carte de message pour diriger les messages de la fenêtre contenue soit vers la fonction de gestionnaire appropriée ou vers une autre carte de message. Pour une liste de macros qui déclarent les fonctions de gestionnaire, voir [BEGIN_MSG_MAP](#begin_msg_map).

Commencez toujours une carte de message avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer d’autres cartes de messages.

La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Notez qu’il y a toujours exactement un exemple de BEGIN_MSG_MAP et de END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

L’exemple suivant montre la carte des messages par défaut et une carte de message alternative, chacune contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux autres cartes de messages. La carte des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a>BEGIN_MSG_MAP

Marque le début de la carte des messages par défaut.

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
[dans] Le nom de la classe contenant la carte de message.

### <a name="remarks"></a>Notes

[CWindowImpl::WindowProc](cwindowimpl-class.md#windowproc) utilise la carte de message par défaut pour traiter les messages envoyés à la fenêtre. La carte de message dirige les messages soit vers la fonction de gestionnaire appropriée, soit vers une autre carte de message.

Les macros suivantes cartographient un message à une fonction de gestionnaire. Cette fonction doit être définie dans *la Classe*.

|Macro|Description|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|Cartographiez un message Windows à une fonction de gestionnaire.|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|Cartographiez une gamme contigue de messages Windows à une fonction de gestionnaire.|
|[COMMAND_HANDLER](#command_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, en fonction du code de notification et de l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_ID_HANDLER](#command_id_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, en fonction de l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[COMMAND_CODE_HANDLER](#command_handler)|Cartographiez un message WM_COMMAND à une fonction de gestionnaire, basé sur le code de notification.|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|Cartographiez une gamme contigue de messages WM_COMMAND à une fonction de gestionnaire, en fonction de l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[NOTIFY_HANDLER](#notify_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, basé sur le code de notification et l’identifiant de contrôle.|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, en fonction de l’identifiant de contrôle.|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|Cartographiez un message WM_NOTIFY à une fonction de gestionnaire, basé sur le code de notification.|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|Cartographiez une gamme contigue de messages WM_NOTIFY à une fonction de gestionnaire, basée sur l’identifiant de contrôle.|

Les macros suivantes dirigent les messages vers une autre carte de message. Ce processus est appelé « chaîne ».

|Macro|Description|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|Chaînes à la carte de message par défaut dans la classe de base.|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|Chaînes à la carte de message par défaut dans un membre de données de la classe.|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|Chaînes à une carte de message alternative dans la classe de base.|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|Chaînes à une carte de message alternative dans un membre de données de la classe.|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|Chaînes à la carte de message par défaut dans une autre classe au moment de l’exécution.|

Les macros suivantes ont directement les messages « réfléchis » de la fenêtre parente. Par exemple, un contrôle envoie normalement des messages de notification à sa fenêtre parente pour le traitement, mais la fenêtre parente peut refléter le message de nouveau au contrôle.

|Macro|Description|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur le code de notification et l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur l’identifiant de l’élément de menu, du contrôle ou de l’accélérateur.|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur le code de notification.|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur une gamme contigu d’identifiants de contrôle.|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|Cartographiez un message WM_COMMAND réfléchi à une fonction de gestionnaire, basé sur le code de notification et une gamme contigu d’identifiants de contrôle.|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur le code de notification et l’identifiant de contrôle.|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur l’identifiant de contrôle.|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur le code de notification.|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur une gamme contigu d’identifiants de contrôle.|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|Cartographiez un message WM_NOTIFY réfléchi à une fonction de gestionnaire, basé sur le code de notification et une gamme contigu d’identifiants de contrôle.|

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

Lorsqu’un `CMyExtWindow` objet reçoit un message WM_PAINT, le `CMyExtWindow::OnPaint` message est dirigé vers le traitement réel. Si `OnPaint` le message indique qu’il faut traiter davantage, le `CMyBaseWindow`message sera ensuite dirigé vers la carte des messages par défaut .

En plus de la carte des messages par défaut, vous pouvez définir une carte de message alternative avec [ALT_MSG_MAP](#alt_msg_map). Commencez toujours une carte de message avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer d’autres cartes de messages. L’exemple suivant montre la carte des messages par défaut et une carte de message alternative, chacune contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux autres cartes de messages. La carte des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Notez qu’il y a toujours exactement un exemple de BEGIN_MSG_MAP et de END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a>CHAIN_MSG_MAP_ALT

Définit une entrée dans une carte de message.

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>Paramètres

*theChainClass*<br/>
[dans] Le nom de la classe de base contenant la carte de message.

*msgMapID msgMapID*<br/>
[dans] L’identifiant de carte de message.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_ALT dirige les messages vers une carte de message alternative dans une classe de base. Vous devez avoir déclaré cette carte de message alternative avec [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Pour diriger les messages vers la carte de message par défaut d’une classe de base (déclarée avec [BEGIN_MSG_MAP),](#begin_msg_map)utilisez CHAIN_MSG_MAP. Par exemple, voir [CHAIN_MSG_MAP](#chain_msg_map).

> [!NOTE]
> Commencez toujours une carte de message avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer d’autres cartes de messages ultérieures avec ALT_MSG_MAP. La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a>CHAIN_MSG_MAP_ALT_MEMBER

Définit une entrée dans une carte de message.

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>Paramètres

*theChainMember*<br/>
[dans] Le nom du membre des données contenant la carte de message.

*msgMapID msgMapID*<br/>
[dans] L’identifiant de carte de message.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_ALT_MEMBER dirige les messages vers une carte de message alternative dans un membre des données. Vous devez avoir déclaré cette carte de message alternative avec [ALT_MSG_MAP (msgMapID)](#alt_msg_map). Pour diriger les messages vers la carte de message par défaut d’un membre des données (déclarée avec [BEGIN_MSG_MAP),](#begin_msg_map)utilisez CHAIN_MSG_MAP_MEMBER. Par exemple, voir [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member).

> [!NOTE]
> Commencez toujours une carte de message avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer d’autres cartes de messages ultérieures avec ALT_MSG_MAP. La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a>CHAIN_MSG_MAP

Définit une entrée dans une carte de message.

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>Paramètres

*theChainClass*<br/>
[dans] Le nom de la classe de base contenant la carte de message.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP dirige les messages vers la carte de message par défaut d’une classe de base (déclarée avec [BEGIN_MSG_MAP](#begin_msg_map)). Pour diriger les messages vers la carte de message alternative d’une classe de base (déclarée avec [ALT_MSG_MAP),](#alt_msg_map)utilisez [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt).

> [!NOTE]
> Commencez toujours une carte de message avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer d’autres cartes de messages ultérieures avec ALT_MSG_MAP. La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

Cet exemple illustre ce qui suit :

- Si une procédure `CMyClass`de fenêtre utilise `OnPaint` la carte de message par défaut `CMyBaseClass`de l’agence et ne gère pas un message, le message est dirigé vers la carte de message par défaut de traitement.

- Si une procédure de fenêtre utilise `CMyClass`la première carte `CMyBaseClass`de message alternative, tous les messages sont dirigés vers la carte de message par défaut de '.

- Si une procédure `CMyClass`de fenêtre utilise la `OnChar` deuxième carte de message alternative de 's et `CMyBaseClass`ne gère pas un message, le message est dirigé vers la carte de message alternative spécifiée dans . `CMyBaseClass`doit avoir déclaré cette carte de message avec ALT_MSG_MAP(1).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a>CHAIN_MSG_MAP_DYNAMIC

Définit une entrée dans une carte de message.

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>Paramètres

*dynaChainID*<br/>
[dans] L’identifiant unique pour la carte de message d’un objet.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_DYNAMIC dirige les messages, au moment de l’exécution, vers la carte de message par défaut d’un autre objet. L’objet et sa carte de message sont associés à *dynaChainID*, que vous définissez via [CDynamicChain::SetChainEntry](cdynamicchain-class.md#setchainentry). Vous devez tirer `CDynamicChain` votre classe de afin d’utiliser CHAIN_MSG_MAP_DYNAMIC. Par exemple, voir la vue d’ensemble [CDynamicChain.](../../atl/reference/cdynamicchain-class.md)

> [!NOTE]
> Commencez toujours une carte de message avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer d’autres cartes de messages ultérieures avec ALT_MSG_MAP. La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a>CHAIN_MSG_MAP_MEMBER

Définit une entrée dans une carte de message.

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>Paramètres

*theChainMember*<br/>
[dans] Le nom du membre des données contenant la carte de message.

### <a name="remarks"></a>Notes

CHAIN_MSG_MAP_MEMBER dirige les messages vers la carte de message par défaut d’un membre des données (déclarée avec [BEGIN_MSG_MAP](#begin_msg_map)). Pour adresser des messages à la carte de message alternative d’un membre des données (déclaré avec [ALT_MSG_MAP),](#alt_msg_map)utilisez [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member).

> [!NOTE]
> Commencez toujours une carte de message avec BEGIN_MSG_MAP. Vous pouvez ensuite déclarer d’autres cartes de messages ultérieures avec ALT_MSG_MAP. La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

Cet exemple illustre ce qui suit :

- Si une procédure `CMyClass`de fenêtre utilise `OnPaint` la carte de message par défaut `m_obj`de l’agence et ne gère pas un message, le message est dirigé vers la carte de message par défaut de traitement.

- Si une procédure de fenêtre utilise `CMyClass`la première carte `m_obj`de message alternative, tous les messages sont dirigés vers la carte de message par défaut de '.

- Si une procédure `CMyClass`de fenêtre utilise la `OnChar` deuxième carte de message alternative de «suppléant et ne gère pas un message, le message est dirigé vers la carte de message alternative spécifiée de `m_obj`. La `CMyContainedClass` classe doit avoir déclaré cette carte de message avec ALT_MSG_MAP(1).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="command_code_handler"></a><a name="command_code_handler"></a>COMMAND_CODE_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais cartographie un [message WM_COMMAND](/windows/win32/menurc/wm-command) basé uniquement sur le code de notification.

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>Paramètres

*Code*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="command_handler"></a><a name="command_handler"></a>COMMAND_HANDLER

Définit une entrée dans une carte de message.

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant de l’élément de menu, le contrôle ou l’accélérateur.

*Code*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

COMMAND_HANDLER cartographie un message [WM_COMMAND](/windows/win32/menurc/wm-command) à la fonction de gestionnaire spécifié, en fonction du code de notification et de l’identifiant de contrôle. Par exemple :

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

Toute fonction spécifiée dans une macro COMMAND_HANDLER doit être définie comme suit :

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

La carte `bHandled` de message `CommandHandler` se définit vers TRUE avant est appelée. S’il `CommandHandler` ne gère pas entièrement `bHandled` le message, il doit être réglé sur FALSE pour indiquer que le message doit être traité davantage.

> [!NOTE]
> Commencez toujours une carte de message avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des cartes de messages alternatifs ultérieures avec [ALT_MSG_MAP](#alt_msg_map). La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

En plus de COMMAND_HANDLER, vous pouvez utiliser [MESSAGE_HANDLER](#message_handler) pour cartographier un message WM_COMMAND sans égard à un identifiant ou un code. Dans ce `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` cas, dirigera tous les `OnHandlerFunction`messages WM_COMMAND à .

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="command_id_handler"></a><a name="command_id_handler"></a>COMMAND_ID_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais cartographie un [message WM_COMMAND](/windows/win32/menurc/wm-command) basé uniquement sur l’identifiant de l’élément de menu, le contrôle ou l’accélérateur.

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant de l’élément de menu, le contrôle ou l’accélérateur envoyant le message.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a>COMMAND_RANGE_CODE_HANDLER

Semblable à [COMMAND_RANGE_HANDLER](#command_range_handler), mais les cartes [WM_COMMAND](/windows/win32/menurc/wm-command) messages avec un code de notification spécifique à partir d’une gamme de contrôles à une fonction de gestionnaire unique.

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Code*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identifiant de l’élément du menu, le contrôle ou l’accélérateur envoyant le message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="command_range_handler"></a><a name="command_range_handler"></a>COMMAND_RANGE_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais les cartes [WM_COMMAND](/windows/win32/menurc/wm-command) messages d’une gamme de contrôles à une fonction de gestionnaire unique.

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identifiant de l’élément du menu, le contrôle ou l’accélérateur envoyant le message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a>DECLARE_EMPTY_MSG_MAP

Déclare une carte de message vide.

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>Notes

DECLARE_EMPTY_MSG_MAP est une macro de commodité qui appelle les macros [BEGIN_MSG_MAP](#begin_msg_map) et [END_MSG_MAP](#end_msg_map) pour créer une carte de message vide:

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a>DEFAULT_REFLECTION_HANDLER

Fournit un gestionnaire par défaut pour la fenêtre de l’enfant (contrôle) qui recevra des messages réfléchis; le gestionnaire transmettra correctement les messages `DefWindowProc`non manipulés à .

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="end_msg_map"></a><a name="end_msg_map"></a>END_MSG_MAP

Marque la fin d’une carte de message.

```
END_MSG_MAP()
```

### <a name="remarks"></a>Notes

Utilisez toujours la [BEGIN_MSG_MAP](#begin_msg_map) macro pour marquer le début d’une carte de message. Utilisez [ALT_MSG_MAP](#alt_msg_map) pour déclarer d’autres cartes de messages ultérieures.

Notez qu’il y a toujours exactement un exemple de BEGIN_MSG_MAP et de END_MSG_MAP.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

L’exemple suivant montre la carte des messages par défaut et une carte de message alternative, chacune contenant une fonction de gestionnaire :

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

L’exemple suivant montre deux autres cartes de messages. La carte des messages par défaut est vide.

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="forward_notifications"></a><a name="forward_notifications"></a>FORWARD_NOTIFICATIONS

Transmette les messages de notification à la fenêtre parente.

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>Notes

Spécifiez cette macro dans votre carte de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="message_handler"></a><a name="message_handler"></a>MESSAGE_HANDLER

Définit une entrée dans une carte de message.

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>Paramètres

*Msg*<br/>
[dans] Le message Windows.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

MESSAGE_HANDLER cartographie un message Windows à la fonction de gestionnaire spécifiée.

Toute fonction spécifiée dans une macro MESSAGE_HANDLER doit être définie comme suit :

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

La carte `bHandled` de message `MessageHandler` se définit vers TRUE avant est appelée. S’il `MessageHandler` ne gère pas entièrement `bHandled` le message, il doit être réglé sur FALSE pour indiquer que le message doit être traité davantage.

> [!NOTE]
> Commencez toujours une carte de message avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des cartes de messages alternatifs ultérieures avec [ALT_MSG_MAP](#alt_msg_map). La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

En plus de MESSAGE_HANDLER, vous pouvez utiliser [COMMAND_HANDLER](#command_handler) et [NOTIFY_HANDLER](#notify_handler) pour cartographier [les messages WM_COMMAND](/windows/win32/menurc/wm-command) et [WM_NOTIFY,](/windows/win32/controls/wm-notify) respectivement.

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="message_range_handler"></a><a name="message_range_handler"></a>MESSAGE_RANGE_HANDLER

Semblable à [MESSAGE_HANDLER](#message_handler), mais cartographie une gamme de messages Windows à une fonction de gestionnaire unique.

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>Paramètres

*msgFirst*<br/>
[dans] Marque le début d’une gamme contigu de messages.

*msgLast msgLast*<br/>
[dans] Marque la fin d’une gamme contigu de messages.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a>NOTIFY_CODE_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais cartographie un [message WM_NOTIFY](/windows/win32/controls/wm-notify) basé uniquement sur le code de notification.

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>Paramètres

*Cd*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="notify_handler"></a><a name="notify_handler"></a>NOTIFY_HANDLER

Définit une entrée dans une carte de message.

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant du contrôle envoyant le message.

*Cd*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

NOTIFY_HANDLER cartographie un message [WM_NOTIFY](/windows/win32/controls/wm-notify) à la fonction de gestionnaire spécifié, en fonction du code de notification et de l’identifiant de contrôle.

Toute fonction spécifiée dans une macro NOTIFY_HANDLER doit être définie comme suit :

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

La carte `bHandled` de message `NotifyHandler` se définit vers TRUE avant est appelée. S’il `NotifyHandler` ne gère pas entièrement `bHandled` le message, il doit être réglé sur FALSE pour indiquer que le message doit être traité davantage.

> [!NOTE]
> Commencez toujours une carte de message avec [BEGIN_MSG_MAP](#begin_msg_map). Vous pouvez ensuite déclarer des cartes de messages alternatifs ultérieures avec [ALT_MSG_MAP](#alt_msg_map). La [macro END_MSG_MAP](#end_msg_map) marque la fin de la carte de message. Chaque carte de message doit avoir exactement un exemple de BEGIN_MSG_MAP et END_MSG_MAP.

En plus de NOTIFY_HANDLER, vous pouvez utiliser [MESSAGE_HANDLER](#message_handler) pour cartographier un message WM_NOTIFY sans égard à un identifiant ou un code. Dans ce `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` cas, dirigera tous les `OnHandlerFunction`messages WM_NOTIFY à .

Pour plus d’informations sur l’utilisation des cartes de messages dans ATL, voir [Cartes des messages](../../atl/message-maps-atl.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a>NOTIFY_ID_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais cartographie un [message WM_NOTIFY](/windows/win32/controls/wm-notify) basé uniquement sur l’identifiant de contrôle.

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant du contrôle envoyant le message.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a>NOTIFY_RANGE_CODE_HANDLER

Semblable à [NOTIFY_RANGE_HANDLER](#notify_range_handler), mais les cartes [WM_NOTIFY](/windows/win32/controls/wm-notify) messages avec un code de notification spécifique à partir d’une gamme de contrôles à une fonction de gestionnaire unique.

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Cd*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identifiant du contrôle envoyant le message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a>NOTIFY_RANGE_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais les cartes [WM_NOTIFY](/windows/win32/controls/wm-notify) messages d’une gamme de contrôles à une fonction de gestionnaire unique.

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="remarks"></a>Notes

Cette plage est basée sur l’identifiant du contrôle envoyant le message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a>REFLECT_NOTIFICATIONS

Reflète les messages de notification vers la fenêtre de l’enfant (contrôle) qui les a envoyés.

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>Notes

Spécifier cette macro dans le cadre de la carte de message de la fenêtre parente.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a>REFLECTED_COMMAND_CODE_HANDLER

Semblable à [COMMAND_CODE_HANDLER](#command_code_handler), mais les commandes de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>Paramètres

*Code*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a>REFLECTED_COMMAND_HANDLER

Semblable à [COMMAND_HANDLER](#command_handler), mais les commandes de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant de l’élément de menu, le contrôle ou l’accélérateur.

*Code*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a>REFLECTED_COMMAND_ID_HANDLER

Semblable à [COMMAND_ID_HANDLER](#command_id_handler), mais les commandes de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant de l’élément de menu, le contrôle ou l’accélérateur.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a>REFLECTED_COMMAND_RANGE_CODE_HANDLER

Semblable à [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler), mais les commandes de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Code*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a>REFLECTED_COMMAND_RANGE_HANDLER

Semblable à [COMMAND_RANGE_HANDLER](#command_range_handler), mais les commandes de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a>REFLECTED_NOTIFY_CODE_HANDLER

Semblable à [NOTIFY_CODE_HANDLER](#notify_code_handler), mais les notifications de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>Paramètres

*Cd*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a>REFLECTED_NOTIFY_HANDLER

Semblable à [NOTIFY_HANDLER](#notify_handler), mais les notifications de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant de l’élément de menu, le contrôle ou l’accélérateur.

*Cd*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a>REFLECTED_NOTIFY_ID_HANDLER

Semblable à [NOTIFY_ID_HANDLER](#notify_id_handler), mais les notifications de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] L’identifiant de l’élément de menu, le contrôle ou l’accélérateur.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a>REFLECTED_NOTIFY_RANGE_CODE_HANDLER

Semblable à [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler), mais les notifications de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Cd*<br/>
[dans] Le code de notification.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

### <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a>REFLECTED_NOTIFY_RANGE_HANDLER

Semblable à [NOTIFY_RANGE_HANDLER](#notify_range_handler), mais les notifications de cartes reflétées à partir de la fenêtre parente.

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>Paramètres

*idFirst*<br/>
[dans] Marque le début d’une gamme contigue d’identifiants de contrôle.

*idLast (en)*<br/>
[dans] Marque la fin d’une gamme contigue d’identifiants de contrôle.

*Func*<br/>
[dans] Le nom de la fonction de gestionnaire de message.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
