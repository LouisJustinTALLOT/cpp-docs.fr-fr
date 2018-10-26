---
title: accelerator_view, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b556a86506e3aae73f7ac4e1ac961b539364d6db
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053560"
---
# <a name="acceleratorview-class"></a>accelerator_view, classe

Représente une abstraction de périphérique virtuel sur un accélérateur de données parallèle C++ AMP.

### <a name="syntax"></a>Syntaxe

```
class accelerator_view;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[accelerator_view, constructeur](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view`.|
|[~ accelerator_view, destructeur](#dtor)|Détruit le `accelerator_view` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[create_marker](#create_marker)|Renvoie un futur pour suivre la fin de toutes les commandes soumises jusqu’alors à ce `accelerator_view` objet.|
|[flush](#flush)|Envoie toutes les commandes en attente en attente pour le `accelerator_view` objet de l’accélérateur pour l’exécution.|
|[get_accelerator](#get_accelerator)|Retourne l'objet `accelerator` de l'objet `accelerator_view`.|
|[get_is_auto_selection](#get_is_auto_selection)|Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque le `accelerator_view` objet est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Retourne une valeur booléenne qui indique si le `accelerator_view` objet a la couche DEBUG activée pour le rapport d’erreurs étendu.|
|[get_queuing_mode](#get_queuing_mode)|Retourne le mode de file d’attente pour le `accelerator_view` objet.|
|[get_version](#get_version)|Retourne la version de la `accelerator_view`.|
|[attente](#wait)|Attend que toutes les commandes soumises à la `accelerator_view` objet se termine.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[!=, opérateur](#operator_neq)|Compare cette `accelerator_view` objet avec un autre et retourne **false** si elles sont identiques ; sinon, retourne **true**.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `accelerator_view` objet dans celui-ci.|
|[operator==](#operator_eq_eq)|Compare cette `accelerator_view` objet avec un autre et retourne **true** si elles sont identiques ; sinon, retourne **false**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[accélérateur](#accelerator)|Obtient l'objet `accelerator` pour l'objet `accelerator_view`.|
|[is_auto_selection](#is_auto_selection)|Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque le `accelerator_view` objet est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Obtient une valeur booléenne qui indique si le `accelerator_view` objet a la couche DEBUG activée pour le rapport d’erreurs étendu.|
|[queuing_mode](#queuing_mode)|Obtient le mode de file d’attente pour le `accelerator_view` objet.|
|[version](#version)|Obtient la version de l’accélérateur.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`accelerator_view`

### <a name="remarks"></a>Notes

Un `accelerator_view` objet représente une vue logique et isolée d’un accélérateur. Un appareil physique de calcul peut avoir de nombreux logiques et isolés `accelerator_view` objets. Chaque accélérateur a une valeur par défaut `accelerator_view` objet. Supplémentaires `accelerator_view` objets peuvent être créés.

Les périphériques physiques peuvent être partagés entre nombreux threads clients. Threads clients peuvent utiliser coopération le même `accelerator_view` objet d’un accélérateur, ou chaque client peut communiquer avec un appareil de calcul via une indépendante `accelerator_view` objet pour l’isolement d’autres threads clients.

Un `accelerator_view` objet peut avoir une des deux [énumération queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) États. Si le mode de file d’attente est `immediate`, commandes telles que `copy` et `parallel_for_each` sont envoyées au périphérique accélérateur correspondant dès qu’elles renvoient à l’appelant. Si le mode de file d’attente est `deferred`, ces commandes sont la file d’attente sur une file d’attente de commande qui correspond à la `accelerator_view` objet. Commandes ne sont pas réellement envoyés à l’appareil jusqu'à ce que `flush()` est appelée.

## <a name="requirements"></a>Configuration requise

**En-tête :** amprt.h

**Espace de noms :** Concurrency

## <a name="accelerator"></a> accélérateur

Obtient l’objet d’accélérateur pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a> accelerator_view

Initialise une nouvelle instance de la classe accelerator_view en copiant une existante `accelerator_view` objet.

### <a name="syntax"></a>Syntaxe

```
accelerator_view( const accelerator_view & _Other );
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
Le `accelerator_view` objet à copier.

## <a name="accelerator_view__create_marker"></a> create_marker

Renvoie un futur pour suivre la fin de toutes les commandes soumises jusqu’alors à ce `accelerator_view` objet.

### <a name="syntax"></a>Syntaxe

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valeur de retour

Un futur pour enregistrer la complétion de toutes les commandes soumises jusqu’alors à ce `accelerator_view` objet.

## <a name="flush"></a> Vider

Envoie que toutes les commandes en attente en file d’attente à l’objet accelerator_view à l’accélérateur pour l’exécution.

### <a name="syntax"></a>Syntaxe

```
void flush();
```

### <a name="return-value"></a>Valeur de retour

Retourne `void`.

## <a name="accelerator_view__get_accelerator"></a> get_accelerator

Retourne l’objet d’accélérateur pour l’objet accelerator_view.
### <a name="syntax"></a>Syntaxe

```
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet accélérateur pour l’objet accelerator_view.

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection

Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le runtime sélectionne automatiquement un accélérateur approprié ; sinon, **false**.

## <a name="accelerator_view__get_is_debug"></a> get_is_debug

Retourne une valeur booléenne qui indique si l’objet accelerator_view a la couche DEBUG activée pour le rapport d’erreurs étendu.

### <a name="syntax"></a>Syntaxe

```
bool get_is_debug() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui indique si le `accelerator_view` objet a la couche DEBUG activée pour le rapport d’erreurs étendu.

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode

Retourne le mode de file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Valeur de retour

Le mode de file d’attente pour le `accelerator_view` objet.

## <a name="accelerator_view__get_version"></a> get_version

Retourne la version de l’accelerator_view.

### <a name="syntax"></a>Syntaxe

```
unsigned int get_version() const;
```

### <a name="return-value"></a>Valeur de retour

La version de la `accelerator_view`.

## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection

Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="accelerator_view__is_debug"></a> is_debug

Obtient une valeur booléenne qui indique si l’objet accelerator_view a la couche DEBUG activée pour le rapport d’erreurs étendu.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="accelerator_view__operator_neq"></a> opérateur ! =

Compare cet objet accelerator_view avec un autre et retourne **false** si elles sont identiques ; sinon, retourne **true**.

### <a name="syntax"></a>Syntaxe

```
bool operator!= (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
Le `accelerator_view` objet à comparer avec celle-ci.

### <a name="return-value"></a>Valeur de retour

**false** si les deux objets sont identiques ; sinon, **true**.

## <a name="accelerator_view__operator_eq"></a> opérateur =

Copie le contenu de l’objet accelerator_view spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```
accelerator_view & operator= (    const accelerator_view & _Other );
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
Le `accelerator_view` objet à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à la modification `accelerator_view` objet.

## <a name="accelerator_view__operator_eq_eq"></a> opérateur ==

Compare cet objet accelerator_view avec un autre et retourne **true** si elles sont identiques ; sinon, retourne **false**.

### <a name="syntax"></a>Syntaxe

```
bool operator= = (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>Paramètres

*_Autre*<br/>
Le `accelerator_view` objet à comparer avec celle-ci.

### <a name="return-value"></a>Valeur de retour

**true** si les deux objets sont identiques ; sinon, **false**.

## <a name="accelerator_view__queuing_mode"></a> queuing_mode

Obtient le mode de file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="accelerator_view__version"></a> Version

Obtient la version de l’accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="accelerator_view__wait"></a> attente

Attend que toutes les commandes soumises à l’objet accelerator_view à terminer.

### <a name="syntax"></a>Syntaxe

```
void wait();
```

#### <a name="return-value"></a>Valeur de retour

Retourne `void`.

#### <a name="remarks"></a>Notes

Si le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) est `immediate`, cette méthode retourne immédiatement sans blocage.

##  <a name="dtor"></a> ~ accelerator_view

Détruit l’objet accelerator_view.

#### <a name="syntax"></a>Syntaxe

```
~accelerator_view();
```

### <a name="return-value"></a>Valeur de retour

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
