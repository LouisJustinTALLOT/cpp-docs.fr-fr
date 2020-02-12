---
title: combinable, classe
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: a1954cd3a69233deed053da5b5fdef0dbc183b80
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141429"
---
# <a name="combinable-class"></a>combinable, classe

L'objet `combinable<T>` est destiné à fournir des copies privées de thread des données pour exécuter des sous-calculs locaux de thread sans verrou pendant des algorithmes parallèles. À la fin de l'opération parallèle, les sous-calculs privés de thread peuvent être fusionnées dans un résultat final. Cette classe peut être utilisée à la place d'une variable partagée et peut entraîner une amélioration des performances au cas où il y aurait beaucoup de conflit sur cette variable partagée.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données du résultat fusionné final. Le type doit avoir un constructeur de copie et un constructeur par défaut.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[combinable](#ctor)|Surchargé. Construit un nouvel objet `combinable`.|
|[~ Destructeur combinable](#dtor)|Détruit un objet `combinable`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[clear](#clear)|Efface tous les résultats de calcul intermédiaires d’une utilisation précédente.|
|[combine](#combine)|Calcule une valeur finale à partir de l’ensemble de sous-calculs locaux de thread en appelant le functor de combinaison fourni.|
|[combine_each](#combine_each)|Calcule une valeur finale à partir de l’ensemble de sous-calculs locaux de thread en appelant le functor de combinaison fourni une fois par sous-calcul local de thread. Le résultat final est accumulé par l’objet de fonction.|
|[local](#local)|Surchargé. Retourne une référence au sous-calcul thread-Private.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Assigne à un objet `combinable` à partir d’un autre objet `combinable`.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`combinable`

## <a name="requirements"></a>Spécifications

**En-tête :** ppl. h

**Espace de noms :** concurrency

## <a name="clear"></a>effacé

Efface tous les résultats de calcul intermédiaires d’une utilisation précédente.

```cpp
void clear();
```

## <a name="ctor"></a>combinable

Construit un nouvel objet `combinable`.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet functor d’initialisation.

*_FnInitialize*<br/>
Fonction qui sera appelée pour initialiser chaque nouvelle valeur de thread-Private du type `T`. Il doit prendre en charge un opérateur d’appel de fonction avec la signature `T ()`.

*_Copy*<br/>
Objet `combinable` existant à copier dans celui-ci.

### <a name="remarks"></a>Notes

Le premier constructeur initialise de nouveaux éléments avec le constructeur par défaut pour le type `T`.

Le deuxième constructeur initialise de nouveaux éléments à l’aide du functor d’initialisation fourni comme paramètre `_FnInitialize`.

Le troisième constructeur est le constructeur de copie.

## <a name="dtor"></a>~ combinable

Détruit un objet `combinable`.

```cpp
~combinable();
```

## <a name="combine"></a>Mixer

Calcule une valeur finale à partir de l’ensemble de sous-calculs locaux de thread en appelant le functor de combinaison fourni.

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet de fonction qui sera appelé pour combiner deux sous-calculs locaux de thread.

*_FnCombine*<br/>
Functor utilisé pour combiner les sous-calculs. Sa signature est `T (T, T)` ou `T (const T&, const T&)`et doit être associative et commutative.

### <a name="return-value"></a>Valeur de retour

Résultat final de la combinaison de tous les sous-calculs privés de thread.

## <a name="combine_each"></a>combine_each

Calcule une valeur finale à partir de l’ensemble de sous-calculs locaux de thread en appelant le functor de combinaison fourni une fois par sous-calcul local de thread. Le résultat final est accumulé par l’objet de fonction.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Type de l’objet de fonction qui sera appelé pour combiner un sous-calcul local de thread unique.

*_FnCombine*<br/>
Functor utilisé pour combiner un sous-calcul. Sa signature est `void (T)` ou `void (const T&)`et doit être associative et commutative.

## <a name="local"></a>localisé

Retourne une référence au sous-calcul thread-Private.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Paramètres

*_Exists*<br/>
Référence à une valeur booléenne. La valeur booléenne référencée par cet argument aura la valeur **true** si le sous-calcul existait déjà sur ce thread, et a la valeur **false** s’il s’agit du premier sous-calcul sur ce thread.

### <a name="return-value"></a>Valeur de retour

Référence au sous-calcul thread-Private.

## <a name="operator_eq"></a>opérateur =

Assigne à un objet `combinable` à partir d’un autre objet `combinable`.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Paramètres

*_Copy*<br/>
Objet `combinable` existant à copier dans celui-ci.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `combinable`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
