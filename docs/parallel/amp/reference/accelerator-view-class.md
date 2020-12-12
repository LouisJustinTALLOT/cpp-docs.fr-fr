---
description: 'En savoir plus sur : classe accelerator_view'
title: accelerator_view, classe
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 2d17c856b988ffd759c73e2f4c039cbdf8b5d24f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254506"
---
# <a name="accelerator_view-class"></a>accelerator_view, classe

Représente une abstraction d’appareil virtuel sur une C++ AMP accélérateur parallèle de données.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur accelerator_view](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view`.|
|[Destructeur ~ accelerator_view](#dtor)|Détruit l' `accelerator_view` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[create_marker](#create_marker)|Retourne un futur pour suivre l’achèvement de toutes les commandes soumises jusqu’à présent à cet `accelerator_view` objet.|
|[postconsommation](#flush)|Envoie toutes les commandes en attente à l' `accelerator_view` objet vers l’accélérateur en vue de leur exécution.|
|[get_accelerator](#get_accelerator)|Retourne l'objet `accelerator` de l'objet `accelerator_view`.|
|[get_is_auto_selection](#get_is_auto_selection)|Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l' `accelerator_view` objet est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Retourne une valeur booléenne qui indique si la `accelerator_view` couche de débogage de l’objet est activée pour le rapport d’erreurs étendu.|
|[get_queuing_mode](#get_queuing_mode)|Retourne le mode de mise en file d’attente pour l' `accelerator_view` objet.|
|[get_version](#get_version)|Retourne la version de `accelerator_view` .|
|[wait](#wait)|Attend la fin de toutes les commandes soumises à l' `accelerator_view` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur ! =](#operator_neq)|Compare cet `accelerator_view` objet à un autre et retourne **`false`** s’ils sont identiques ; sinon, retourne **`true`** .|
|[opérateur =](#operator_eq)|Copie le contenu de l’objet spécifié dans celui- `accelerator_view` ci.|
|[opérateur = =](#operator_eq_eq)|Compare cet `accelerator_view` objet à un autre et retourne **`true`** s’ils sont identiques ; sinon, retourne **`false`** .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[accélérateur](#accelerator)|Obtient l'objet `accelerator` pour l'objet `accelerator_view`.|
|[is_auto_selection](#is_auto_selection)|Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l' `accelerator_view` objet est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Obtient une valeur booléenne qui indique si la `accelerator_view` couche de débogage de l’objet est activée pour le rapport d’erreurs étendu.|
|[queuing_mode](#queuing_mode)|Obtient le mode de mise en file d’attente pour l' `accelerator_view` objet.|
|[version](#version)|Obtient la version de l’accélérateur.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`accelerator_view`

### <a name="remarks"></a>Notes

Un `accelerator_view` objet représente une vue logique et isolée d’un accélérateur. Un seul appareil de calcul physique peut avoir de nombreux objets logiques et isolés `accelerator_view` . Chaque accélérateur a un objet par défaut `accelerator_view` . Des `accelerator_view` objets supplémentaires peuvent être créés.

Les appareils physiques peuvent être partagés entre plusieurs threads clients. Les threads clients peuvent utiliser de manière coopérative le même `accelerator_view` objet d’accélérateur, ou chaque client peut communiquer avec un appareil de calcul via un `accelerator_view` objet indépendant pour l’isolation d’autres threads clients.

Un `accelerator_view` objet peut avoir l’un des deux queuing_mode États d' [énumération](concurrency-namespace-enums-amp.md#queuing_mode) . Si le mode de mise en file d’attente est `immediate` , les commandes telles que `copy` et `parallel_for_each` sont envoyées à l’appareil accélérateur correspondant dès qu’elles retournent à l’appelant. Si le mode de mise en file d’attente est `deferred` , ces commandes sont mises en file d’attente dans une file d’attente de commandes qui correspond à l' `accelerator_view` objet. Les commandes ne sont pas réellement envoyées à l’appareil tant que `flush()` n’est pas appelé.

## <a name="requirements"></a>Spécifications

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="accelerator"></a><a name="accelerator"></a> accélérateur

Obtient l’objet d’accélérateur pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a> accelerator_view

Initialise une nouvelle instance de la classe accelerator_view en copiant un objet existant `accelerator_view` .

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Objet `accelerator_view` à copier.

## <a name="create_marker"></a><a name="create_marker"></a> create_marker

Retourne un futur pour suivre l’achèvement de toutes les commandes soumises jusqu’à présent à cet `accelerator_view` objet.

### <a name="syntax"></a>Syntaxe

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valeur de retour

Un futur pour suivre l’achèvement de toutes les commandes soumises jusqu’à présent à cet `accelerator_view` objet.

## <a name="flush"></a>flush

Soumet toutes les commandes en attente à l’objet accelerator_view à l’accélérateur en vue de leur exécution.

### <a name="syntax"></a>Syntaxe

```cpp
void flush();
```

### <a name="return-value"></a>Valeur de retour

Retourne **`void`** .

## <a name="get_accelerator"></a><a name="get_accelerator"></a> get_accelerator

Retourne l’objet d’accélérateur pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Valeur de retour

Objet d’accélérateur pour l’objet accelerator_view.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a> get_is_auto_selection

Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque le accelerator_view est passé à une [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si le runtime sélectionne automatiquement un accélérateur approprié ; Sinon, **`false`** .

## <a name="get_is_debug"></a><a name="get_is_debug"></a> get_is_debug

Retourne une valeur booléenne qui indique si la couche de débogage de l’objet accelerator_view est activée pour le rapport d’erreurs étendu.

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui indique si la `accelerator_view` couche de débogage de l’objet est activée pour le rapport d’erreurs étendu.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a> get_queuing_mode

Retourne le mode de mise en file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Valeur de retour

Mode de mise en file d’attente pour l' `accelerator_view` objet.

## <a name="get_version"></a><a name="get_version"></a> get_version

Retourne la version de la accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Valeur de retour

Version du `accelerator_view`.

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a> is_auto_selection

Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque le accelerator_view est passé à une [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a> is_debug

Obtient une valeur booléenne qui indique si la couche de débogage de l’objet accelerator_view est activée pour le rapport d’erreurs étendu.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a> opérateur ! =

Compare cet objet accelerator_view avec un autre et retourne **`false`** s’ils sont identiques ; sinon, retourne **`true`** .

### <a name="syntax"></a>Syntaxe

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
`accelerator_view`Objet à comparer à celui-ci.

### <a name="return-value"></a>Valeur renvoyée

**`false`** Si les deux objets sont identiques ; Sinon, **`true`** .

## <a name="operator"></a><a name="operator_eq"></a> opérateur =

Copie le contenu de l’objet accelerator_view spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
`accelerator_view`Objet à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet modifié `accelerator_view` .

## <a name="operator"></a><a name="operator_eq_eq"></a> opérateur = =

Compare cet objet accelerator_view avec un autre et retourne **`true`** s’ils sont identiques ; sinon, retourne **`false`** .

### <a name="syntax"></a>Syntaxe

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
`accelerator_view`Objet à comparer à celui-ci.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les deux objets sont identiques ; Sinon, **`false`** .

## <a name="queuing_mode"></a><a name="queuing_mode"></a> queuing_mode

Obtient le mode de mise en file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Obtient la version de la accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>wait

Attend la fin de toutes les commandes soumises à l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
void wait();
```

### <a name="return-value"></a>Valeur de retour

Retourne **`void`** .

### <a name="remarks"></a>Notes

Si le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) est `immediate` , cette méthode retourne immédiatement une valeur sans se bloquer.

## <a name="accelerator_view"></a><a name="dtor"></a> ~ accelerator_view

Détruit l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
