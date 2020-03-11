---
title: cancellation_token, classe
ms.date: 11/04/2016
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
ms.openlocfilehash: 34743ce48510eec9d8f7862e5ed951a722932962
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876072"
---
# <a name="cancellation_token-class"></a>cancellation_token, classe

La classe `cancellation_token` représente la capacité à déterminer si l'annulation d'une opération a été demandée. Un jeton donné peut être associé à un objet `task_group`, `structured_task_group` ou `task` pour entraîner une annulation implicite. Il peut également être sondé à la recherche d'une annulation ou comporter un rappel enregistré en cas d'annulation de la classe `cancellation_token_source` associée.

## <a name="syntax"></a>Syntaxe

```cpp
class cancellation_token;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[Destructeur ~ cancellation_token](#dtor)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Supprime un rappel précédemment enregistré à l'aide de la méthode `register` basée sur l'objet `cancellation_token_registration` retourné au moment de l'enregistrement.|
|[is_cancelable](#is_cancelable)|Indique si ce jeton peut être annulé ou non.|
|[is_canceled](#is_canceled)|Retourne la **valeur true** si le jeton a été annulé.|
|[Aucune](#none)|Retourne un jeton d'annulation qui ne pourra jamais faire l'objet d'une annulation.|
|[register_callback](#register_callback)|Enregistre une fonction de rappel avec le jeton. Le rappel est effectué si et lorsque le jeton est annulé. Notez que si le jeton est déjà annulé lorsque cette méthode est appelée, le rappel est effectué immédiatement et de manière synchrone.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`cancellation_token`

## <a name="requirements"></a>Spécifications

**En-tête :** pplcancellation_token. h

**Espace de noms :** concurrency

## <a name="dtor"></a>~ cancellation_token

```cpp
~cancellation_token();
```

## <a name="ctor"></a>cancellation_token

```cpp
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Cancellation_token à copier ou déplacer.

## <a name="deregister_callback"></a>deregister_callback

Supprime un rappel précédemment enregistré à l'aide de la méthode `register` basée sur l'objet `cancellation_token_registration` retourné au moment de l'enregistrement.

```cpp
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Paramètres

*_Registration*<br/>
Objet `cancellation_token_registration` correspondant au rappel dont l'enregistrement doit être annulé. Ce jeton doit avoir été précédemment retourné par un appel à la méthode `register`.

## <a name="is_cancelable"></a>is_cancelable

Indique si ce jeton peut être annulé ou non.

```cpp
bool is_cancelable() const;
```

### <a name="return-value"></a>Valeur de retour

Indique si ce jeton peut être annulé ou non.

## <a name="is_canceled"></a>is_canceled

Retourne la **valeur true** si le jeton a été annulé.

```cpp
bool is_canceled() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur **true** si le jeton a été annulé ; Sinon, la valeur **false**.

## <a name="none"></a>None

Retourne un jeton d'annulation qui ne pourra jamais faire l'objet d'une annulation.

```cpp
static cancellation_token none();
```

### <a name="return-value"></a>Valeur de retour

Jeton d'annulation qui ne peut pas être annulé.

## <a name="operator_neq"></a>opérateur ! =

```cpp
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
`cancellation_token` à comparer.

### <a name="return-value"></a>Valeur de retour

## <a name="operator_eq"></a>opérateur =

```cpp
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
`cancellation_token` à assigner.

### <a name="return-value"></a>Valeur de retour

## <a name="operator_eq_eq"></a>opérateur = =

```cpp
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
`cancellation_token` à comparer.

### <a name="return-value"></a>Valeur de retour

## <a name="register_callback"></a>register_callback

Enregistre une fonction de rappel avec le jeton. Le rappel est effectué si et lorsque le jeton est annulé. Notez que si le jeton est déjà annulé lorsque cette méthode est appelée, le rappel est effectué immédiatement et de manière synchrone.

```cpp
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l'objet de fonction qui est rappelé lorsque `cancellation_token` est annulé.

*_Func*<br/>
Objet de fonction qui est rappelé lorsque `cancellation_token` est annulé.

### <a name="return-value"></a>Valeur de retour

Objet `cancellation_token_registration` qui peut être utilisé dans la méthode `deregister` pour annuler l'enregistrement d'un rappel précédemment enregistré et l'empêcher d'être effectué. La méthode lève une exception [invalid_operation](invalid-operation-class.md) si elle est appelée sur un objet `cancellation_token` qui a été créé à l’aide de la méthode [cancellation_token :: None](#none) .

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
