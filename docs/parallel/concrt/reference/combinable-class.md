---
title: combinable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d544ac392e2eb227d7e1c37412110d09272f10d5
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162503"
---
# <a name="combinable-class"></a>combinable, classe

L'objet `combinable<T>` est destiné à fournir des copies privées de thread des données pour exécuter des sous-calculs locaux de thread sans verrou pendant des algorithmes parallèles. À la fin de l'opération parallèle, les sous-calculs privés de thread peuvent être fusionnées dans un résultat final. Cette classe peut être utilisée à la place d'une variable partagée et peut entraîner une amélioration des performances au cas où il y aurait beaucoup de conflit sur cette variable partagée.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class combinable;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données du résultat fusionné final. Le type doit avoir un constructeur de copie et un constructeur par défaut.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[combinable](#ctor)|Surchargé. Construit un nouvel `combinable` objet.|
|[~ combinable, destructeur](#dtor)|Détruit un objet `combinable`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[clear](#clear)|Efface les résultats de calcul intermédiaires d’une utilisation précédente.|
|[combine](#combine)|Calcule une valeur finale à partir de l’ensemble des sous-calculs locaux de thread en appelant la fonction d’association fournie.|
|[combine_each](#combine_each)|Calcule une valeur finale à partir de l’ensemble des sous-calculs locaux de thread en appelant la fonction d’association fournie une fois par calcul sous-chemin de thread local. Le résultat final est accumulé par l’objet de fonction.|
|[local](#local)|Surchargé. Retourne une référence au calcul secondaire privées de thread.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator=](#operator_eq)|Assigne à un `combinable` objet à partir d’un autre `combinable` objet.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [conteneurs et objets parallèles](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`combinable`

## <a name="requirements"></a>Configuration requise

**En-tête :** ppl.h

**Espace de noms :** concurrency

##  <a name="clear"></a> Effacer

Efface les résultats de calcul intermédiaires d’une utilisation précédente.

```
void clear();
```

##  <a name="ctor"></a> combinable

Construit un nouvel `combinable` objet.

```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de functor d’initialisation.

*_FnInitialize*<br/>
Une fonction qui sera appelée pour initialiser chaque nouvelle valeur de thread privée du type `T`. Il doit prendre en charge un opérateur d’appel de fonction avec la signature `T ()`.

*_Copier*<br/>
Un existant `combinable` objet doit être copié dans celui-ci.

### <a name="remarks"></a>Notes

Le premier constructeur initialise de nouveaux éléments avec le constructeur par défaut pour le type `T`.

Le deuxième constructeur initialise de nouveaux éléments à l’aide du functor d’initialisation fourni comme le `_FnInitialize` paramètre.

Le troisième constructeur est le constructeur de copie.

##  <a name="dtor"></a> ~ combinable

Détruit un objet `combinable`.

```
~combinable();
```

##  <a name="combine"></a> combiner

Calcule une valeur finale à partir de l’ensemble des sous-calculs locaux de thread en appelant la fonction d’association fournie.

```
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de fonction qui sera appelé pour combiner deux sous-calculs locaux de thread.

*_FnCombine*<br/>
Le functor qui est utilisé pour combiner les sous-calculs. Sa signature est `T (T, T)` ou `T (const T&, const T&)`, et il doit être associative et commutative.

### <a name="return-value"></a>Valeur de retour

Le résultat final de la combinaison de tous les sous-calculs privés de thread.

##  <a name="combine_each"></a> combine_each

Calcule une valeur finale à partir de l’ensemble des sous-calculs locaux de thread en appelant la fonction d’association fournie une fois par calcul sous-chemin de thread local. Le résultat final est accumulé par l’objet de fonction.

```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Paramètres

*_Function*<br/>
Le type de l’objet de fonction qui sera appelé pour combiner un calcul secondaire locales de thread unique.

*_FnCombine*<br/>
Le functor qui est utilisé pour combiner un calcul secondaire. Sa signature est `void (T)` ou `void (const T&)`et doit être associative et commutative.

##  <a name="local"></a> local

Retourne une référence au calcul secondaire privées de thread.

```
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Paramètres

*_Exists*<br/>
Une référence à une valeur booléenne. La valeur booléenne référencée par cet argument est fixée à **true** si le calcul secondaire existait déjà sur ce thread et la valeur **false** si c’était le premier calcul secondaire sur ce thread.

### <a name="return-value"></a>Valeur de retour

Une référence au calcul secondaire privées de thread.

##  <a name="operator_eq"></a> opérateur =

Assigne à un `combinable` objet à partir d’un autre `combinable` objet.

```
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Paramètres

*_Copier*<br/>
Un existant `combinable` objet doit être copié dans celui-ci.

### <a name="return-value"></a>Valeur de retour

Une référence à cet `combinable` objet.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
