---
title: concurrency, opérateur de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 97553276a7c4ff687dd8bea4627f943d5666b2e9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836009"
---
# <a name="concurrency-namespace-operators"></a>concurrency, opérateur de l’espace de noms

:::row:::
   :::column span="":::
      [`operator||`](#operator_lor)\
      [`operator&&`](#operator_amp_amp)
   :::column-end:::
   :::column span="":::
      [`operator==`](#operator_eq_eq)\
      [`operator!=`](#operator_neq)
   :::column-end:::
   :::column span="":::
      [`operator<`](#operator_lt)\
      [`operator<=`](#operator_lt_eq)
   :::column-end:::
   :::column span="":::
      [`operator>`](#operator_gt)\
      [`operator>=`](#operator_gt_eq)
   :::column-end:::
:::row-end:::

## <a name="operator124124-operator"></a><a name="operator_lor"></a> Operator&#124;&#124; , opérateur

Crée une tâche qui s’effectue correctement quand l’une des tâches fournies en tant qu’arguments s’effectue correctement.

```cpp
template<typename ReturnType>
task<ReturnType> operator||(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void> operator||(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Paramètres

*ReturnType*<br/>
Type de la tâche retournée.

*LHS*<br/>
Première tâche à associer à la tâche obtenue.

*rhs*<br/>
Seconde tâche à associer à la tâche obtenue.

### <a name="return-value"></a>Valeur renvoyée

Tâche qui se termine correctement lorsque l’une des tâches d’entrée s’est terminée avec succès. Si les tâches d’entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>`. Si les tâches d’entrée sont de type **`void`** , la tâche de sortie sera également `task<void>` .

### <a name="remarks"></a>Notes

Si les deux tâches sont annulées ou lèvent des exceptions, la tâche retournée se termine à l’état annulé, et l’une des exceptions, le cas échéant, est levée lorsque vous appelez `get()` ou `wait()` sur cette tâche.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>opérateur &amp; Operator &amp;

Crée une tâche qui s’effectue correctement lorsque les deux tâches fournies comme arguments se terminent correctement.

```cpp
template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<ReturnType>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,
    const task<std::vector<ReturnType>>& rhs);

template<typename ReturnType>
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,
    const task<std::vector<ReturnType>>& rhs);

inline task<void>  operator&&(
    const task<void>& lhs,
    const task<void>& rhs);
```

### <a name="parameters"></a>Paramètres

*ReturnType*<br/>
Type de la tâche retournée.

*LHS*<br/>
Première tâche à associer à la tâche obtenue.

*rhs*<br/>
Seconde tâche à associer à la tâche obtenue.

### <a name="return-value"></a>Valeur renvoyée

Tâche qui s'effectue correctement lorsque les deux tâches d'entrée se sont correctement déroulées. Si les tâches d’entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>>`. Si les tâches d’entrée sont de type **`void`** , la tâche de sortie sera également `task<void>` .

### <a name="remarks"></a>Notes

Si l’une des tâches est annulée ou lève une exception, la tâche retournée se termine plus tôt, à l’état annulé, et l’exception, le cas échéant, est levée si vous appelez `get()` ou `wait()` sur cette tâche.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a> Operator = =, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur simultané à gauche de l’opérateur est égal au vecteur simultané sur le côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Deux vecteurs simultanés sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Cette méthode n’est pas sécurisée pour l’accès concurrentiel par rapport à d’autres méthodes qui peuvent modifier l’un ou l’autre des vecteurs simultanés `_A` ou `_B` .

## <a name="operator-operator"></a><a name="operator_neq"></a> Operator ! =, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur n'est pas égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les vecteurs simultanés ne sont pas égaux ; **`false`** si les vecteurs simultanés sont égaux.

### <a name="remarks"></a>Notes

Deux vecteurs simultanés sont égaux s’ils ont le même nombre d’éléments et si leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Cette méthode n’est pas sécurisée pour l’accès concurrentiel par rapport à d’autres méthodes qui peuvent modifier l’un ou l’autre des vecteurs simultanés `_A` ou `_B` .

## <a name="operatorlt-operator"></a><a name="operator_lt"></a> opérateur &lt; Operator

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur simultané sur le côté gauche de l’opérateur est inférieur au vecteur simultané sur le côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans l' `std` espace de noms.

Cette méthode n’est pas sécurisée pour l’accès concurrentiel par rapport à d’autres méthodes qui peuvent modifier l’un ou l’autre des vecteurs simultanés `_A` ou `_B` .

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a> Operator &lt; =, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur ou égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur simultané à gauche de l’opérateur est inférieur ou égal au vecteur simultané sur le côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans l' `std` espace de noms.

Cette méthode n’est pas sécurisée pour l’accès concurrentiel par rapport à d’autres méthodes qui peuvent modifier l’un ou l’autre des vecteurs simultanés `_A` ou `_B` .

## <a name="operatorgt-operator"></a><a name="operator_gt"></a> opérateur &gt; Operator

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur simultané à gauche de l’opérateur est supérieur au vecteur simultané sur le côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans l' `std` espace de noms.

Cette méthode n’est pas sécurisée pour l’accès concurrentiel par rapport à d’autres méthodes qui peuvent modifier l’un ou l’autre des vecteurs simultanés `_A` ou `_B` .

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a> Operator &gt; =, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur ou égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le vecteur simultané à gauche de l’opérateur est supérieur ou égal au vecteur simultané sur le côté droit de l’opérateur ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans l' `std` espace de noms.

Cette méthode n’est pas sécurisée pour l’accès concurrentiel par rapport à d’autres méthodes qui peuvent modifier l’un ou l’autre des vecteurs simultanés `_A` ou `_B` .

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
