---
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
ms.openlocfilehash: 4075051ec07fc1331d815534a715c0411160fe14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405636"
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
|[wait](#wait)|Attend que toutes les commandes soumises à la `accelerator_view` objet se termine.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[!=, opérateur](#operator_neq)|Compare cette `accelerator_view` objet avec un autre et retourne **false** si elles sont identiques ; sinon, retourne **true**.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `accelerator_view` objet dans celui-ci.|
|[operator==](#operator_eq_eq)|Compare cette `accelerator_view` objet avec un autre et retourne **true** si elles sont identiques ; sinon, retourne **false**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[accelerator](#accelerator)|Obtient l'objet `accelerator` pour l'objet `accelerator_view`.|
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

**Espace de noms :** Concurrence

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
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Le `accelerator_view` objet à copier.

## <a name="createmarker"></a>create_marker

Renvoie un futur pour suivre la fin de toutes les commandes soumises jusqu’alors à ce `accelerator_view` objet.

### <a name="syntax"></a>Syntaxe

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valeur de retour

Un futur pour enregistrer la complétion de toutes les commandes soumises jusqu’alors à ce `accelerator_view` objet.

## <a name="flush"></a>flush

Envoie que toutes les commandes en attente en file d’attente à l’objet accelerator_view à l’accélérateur pour l’exécution.

### <a name="syntax"></a>Syntaxe

```
void flush();
```

### <a name="return-value"></a>Valeur de retour

Retourne `void`.

## <a name="getaccelerator"></a>get_accelerator

Retourne l’objet d’accélérateur pour l’objet accelerator_view.
### <a name="syntax"></a>Syntaxe

```
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet accélérateur pour l’objet accelerator_view.

## <a name="getisautoselection"></a>get_is_auto_selection

Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le runtime sélectionne automatiquement un accélérateur approprié ; sinon, **false**.

## <a name="getisdebug"></a>get_is_debug

Retourne une valeur booléenne qui indique si l’objet accelerator_view a la couche DEBUG activée pour le rapport d’erreurs étendu.

### <a name="syntax"></a>Syntaxe

```
bool get_is_debug() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui indique si le `accelerator_view` objet a la couche DEBUG activée pour le rapport d’erreurs étendu.

## <a name="getqueuingmode"></a>get_queuing_mode

Retourne le mode de file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Valeur de retour

Le mode de file d’attente pour le `accelerator_view` objet.

## <a name="getversion"></a>get_version

Retourne la version de l’accelerator_view.

### <a name="syntax"></a>Syntaxe

```
unsigned int get_version() const;
```

### <a name="return-value"></a>Valeur de retour

La version de la `accelerator_view`.

## <a name="isautoselection"></a>is_auto_selection

Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="isdebug"></a>is_debug

Obtient une valeur booléenne qui indique si l’objet accelerator_view a la couche DEBUG activée pour le rapport d’erreurs étendu.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a> operator!=

Compare cet objet accelerator_view avec un autre et retourne **false** si elles sont identiques ; sinon, retourne **true**.

### <a name="syntax"></a>Syntaxe

```
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Le `accelerator_view` objet à comparer avec celle-ci.

### <a name="return-value"></a>Valeur de retour

**false** si les deux objets sont identiques ; sinon, **true**.

## <a name="operator_eq"></a> operator=

Copie le contenu de l’objet accelerator_view spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Le `accelerator_view` objet à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à la modification `accelerator_view` objet.

## <a name="operator_eq_eq"></a> operator==

Compare cet objet accelerator_view avec un autre et retourne **true** si elles sont identiques ; sinon, retourne **false**.

### <a name="syntax"></a>Syntaxe

```
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Le `accelerator_view` objet à comparer avec celle-ci.

### <a name="return-value"></a>Valeur de retour

**true** si les deux objets sont identiques ; sinon, **false**.

## <a name="queuingmode"></a>queuing_mode

Obtient le mode de file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Obtient la version de l’accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>attente

Attend que toutes les commandes soumises à l’objet accelerator_view à terminer.

### <a name="syntax"></a>Syntaxe

```
void wait();
```

### <a name="return-value"></a>Valeur de retour

Retourne `void`.

### <a name="remarks"></a>Notes

Si le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) est `immediate`, cette méthode retourne immédiatement sans blocage.

##  <a name="dtor"></a> ~accelerator_view

Détruit l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```
~accelerator_view();
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
