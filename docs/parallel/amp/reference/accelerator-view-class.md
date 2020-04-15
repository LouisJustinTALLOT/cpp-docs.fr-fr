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
ms.openlocfilehash: f3be8cc3ab9a0f36027cc38c88f026570d1fdb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370887"
---
# <a name="accelerator_view-class"></a>accelerator_view, classe

Représente une abstraction d’appareils virtuels sur un accélérateur de données parallèle DE l’AMP.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[accelerator_view Constructeur](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view`.|
|[Accelerator_view Destructor](#dtor)|Détruit l’objet. `accelerator_view`|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[create_marker](#create_marker)|Retourne un avenir pour suivre l’achèvement de `accelerator_view` toutes les commandes soumises jusqu’à présent à cet objet.|
|[Rincer](#flush)|Soumet toutes les commandes en `accelerator_view` attente en file d’attente à l’objet à l’accélérateur pour l’exécution.|
|[get_accelerator](#get_accelerator)|Retourne l'objet `accelerator` de l'objet `accelerator_view`.|
|[get_is_auto_selection](#get_is_auto_selection)|Retourne une valeur Boolean qui indique si le temps `accelerator_view` d’exécution sélectionnera automatiquement un accélérateur approprié lorsque l’objet est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Renvoie une valeur Boolean `accelerator_view` qui indique si l’objet a la couche DEBUG activée pour des rapports d’erreur étendues.|
|[get_queuing_mode](#get_queuing_mode)|Retourne le mode de `accelerator_view` file d’attente pour l’objet.|
|[get_version](#get_version)|Retourne la version `accelerator_view`de la .|
|[Attendre](#wait)|Attend que toutes les commandes `accelerator_view` soumises à l’objet se terminent.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur!](#operator_neq)|Compare cet `accelerator_view` objet avec un autre et retourne **faux** s’ils sont les mêmes; sinon, retourne **vrai**.|
|[opérateur](#operator_eq)|Copie le contenu `accelerator_view` de l’objet spécifié dans celui-ci.|
|[opérateur](#operator_eq_eq)|Compare cet `accelerator_view` objet avec un autre et retourne **vrai** s’ils sont les mêmes; sinon, retourne **faux**.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[Accélérateur](#accelerator)|Obtient l'objet `accelerator` pour l'objet `accelerator_view`.|
|[is_auto_selection](#is_auto_selection)|Obtient une valeur Boolean qui indique si le temps `accelerator_view` d’exécution sélectionnera automatiquement un accélérateur approprié lorsque l’objet est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Obtient une valeur Boolean `accelerator_view` qui indique si l’objet a la couche DEBUG activée pour les rapports d’erreur étendues.|
|[queuing_mode](#queuing_mode)|Obtient le mode de `accelerator_view` file d’attente pour l’objet.|
|[version](#version)|Obtient la version de l’accélérateur.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`accelerator_view`

### <a name="remarks"></a>Notes

Un `accelerator_view` objet représente une vue logique et isolée d’un accélérateur. Un seul dispositif de calcul physique peut `accelerator_view` avoir de nombreux objets logiques et isolés. Chaque accélérateur dispose `accelerator_view` d’un objet par défaut. Des `accelerator_view` objets supplémentaires peuvent être créés.

Les appareils physiques peuvent être partagés entre de nombreux threads clients. Les fils des clients peuvent `accelerator_view` utiliser en coopération le même objet d’un accélérateur, `accelerator_view` ou chaque client peut communiquer avec un appareil de calcul via un objet indépendant pour l’isolement des autres threads du client.

Un `accelerator_view` objet peut avoir l’un des deux [états d’énumération queuing_mode.](concurrency-namespace-enums-amp.md#queuing_mode) Si le mode de `immediate`file d’attente est, les commandes comme `copy` et `parallel_for_each` sont envoyés à l’appareil d’accélérateur correspondant dès qu’ils retournent à l’appelant. Si le mode de `deferred`file d’attente est, ces commandes sont alignées sur une file d’attente de commande qui correspond à l’objet. `accelerator_view` Les commandes ne sont pas `flush()` envoyées à l’appareil jusqu’à ce qu’elle soit appelée.

## <a name="requirements"></a>Spécifications

**En-tête:** amprt.h

**Espace de noms :** Concurrency

## <a name="accelerator"></a><a name="accelerator"></a>Accélérateur

Obtient l’objet d’accélérateur pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

Initialise une nouvelle instance de la classe accelerator_view en `accelerator_view` copiant un objet existant.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Objet `accelerator_view` à copier.

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

Retourne un avenir pour suivre l’achèvement de `accelerator_view` toutes les commandes soumises jusqu’à présent à cet objet.

### <a name="syntax"></a>Syntaxe

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valeur de retour

Un avenir pour suivre l’achèvement de toutes `accelerator_view` les commandes soumises jusqu’à présent à cet objet.

## <a name="flush"></a>flush

Soumet toutes les commandes en attente en file d’attente à l’objet accelerator_view à l’accélérateur pour exécution.

### <a name="syntax"></a>Syntaxe

```cpp
void flush();
```

### <a name="return-value"></a>Valeur de retour

Retourne `void`.

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

Retourne l’objet d’accélérateur pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet d’accélérateur pour l’objet accelerator_view.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

Retourne une valeur Boolean qui indique si le temps d’exécution sélectionnera automatiquement un accélérateur approprié lorsque le accelerator_view est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si le temps d’exécution sélectionnera automatiquement un accélérateur approprié; autrement, **faux**.

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Renvoie une valeur Boolean qui indique si l’objet accelerator_view a la couche DEBUG activée pour les rapports d’erreur étendues.

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur Boolean qui `accelerator_view` indique si l’objet a la couche DEBUG activée pour les rapports d’erreur étendues.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

Retourne le mode de file d’attente pour l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Valeur de retour

Le mode de file `accelerator_view` d’attente pour l’objet.

## <a name="get_version"></a><a name="get_version"></a>get_version

Retourne la version du accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Valeur de retour

Version du `accelerator_view`.

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

Obtient une valeur Boolean qui indique si le temps d’exécution sélectionnera automatiquement un accélérateur approprié lorsque le accelerator_view est passé à un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Obtient une valeur Boolean qui indique si l’objet accelerator_view a la couche DEBUG activée pour les rapports d’erreur étendues.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>opérateur!

Compare cet objet accelerator_view avec un autre et retourne **faux** s’ils sont les mêmes; sinon, retourne **vrai**.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
L’objet `accelerator_view` à comparer avec celui-ci.

### <a name="return-value"></a>Valeur de retour

**faux** si les deux objets sont les mêmes; autrement, **vrai**.

## <a name="operator"></a><a name="operator_eq"></a>opérateur

Copie le contenu de l’objet accelerator_view spécifié dans celui-ci.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
L’objet `accelerator_view` à copier.

### <a name="return-value"></a>Valeur de retour

Une référence à `accelerator_view` l’objet modifié.

## <a name="operator"></a><a name="operator_eq_eq"></a>opérateur

Compare cet objet accelerator_view avec un autre et retourne **vrai** si elles sont les mêmes; sinon, retourne **faux**.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
L’objet `accelerator_view` à comparer avec celui-ci.

### <a name="return-value"></a>Valeur de retour

**vrai** si les deux objets sont les mêmes; autrement, **faux**.

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

Obtient le mode de file d’attente pour l’objet accelerator_view.

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

Attend toutes les commandes soumises à l’objet accelerator_view pour finir.

### <a name="syntax"></a>Syntaxe

```cpp
void wait();
```

### <a name="return-value"></a>Valeur de retour

Retourne `void`.

### <a name="remarks"></a>Notes

Si le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) est, `immediate`cette méthode revient immédiatement sans blocage.

## <a name="accelerator_view"></a><a name="dtor"></a>accelerator_view

Détruit l’objet accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
