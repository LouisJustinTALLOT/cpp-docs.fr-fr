---
title: espace de noms d’accès concurrentiel opérateurs
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 5982ae0ec3baff38b43b0ce504a47d512559390d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521607"
---
# <a name="concurrency-namespace-operators"></a>espace de noms d’accès concurrentiel opérateurs

||||
|-|-|-|
|[!=, opérateur](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator&#124;&#124;](#operator_lor)| |

##  <a name="operator_lor"></a>  opérateur&#124; &#124; opérateur

Crée une tâche qui s’effectue correctement quand l’une des tâches fournies en tant qu’arguments s’effectue correctement.

```
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

*terme de droite*<br/>
Seconde tâche à associer à la tâche obtenue.

### <a name="return-value"></a>Valeur de retour

Une tâche qui s’effectue correctement lorsqu’une des tâches d’entrée est bien terminée. Si les tâches d’entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>`. Si les tâches d’entrée sont de type `void`, la tâche de sortie sera également `task<void>`.

### <a name="remarks"></a>Notes

Si les deux tâches sont annulées ou lever des exceptions, la tâche retournée se terminera dans l’état annulé, et l’une des exceptions, si vous les rencontrez, sera levée lorsque vous appelez `get()` ou `wait()` sur la tâche.

##  <a name="operator_amp_amp"></a>  opérateur&amp; &amp; opérateur

Crée une tâche qui s’effectue correctement lorsque les deux tâches fournies comme arguments se déroulent correctement.

```
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

*terme de droite*<br/>
Seconde tâche à associer à la tâche obtenue.

### <a name="return-value"></a>Valeur de retour

Tâche qui s’effectue correctement lorsque les deux tâches d’entrée se sont correctement déroulées. Si les tâches d'entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>>`. Si les tâches d’entrée sont de type `void`, la tâche de sortie sera également `task<void>`.

### <a name="remarks"></a>Notes

Si une des tâches est annulée ou lève une exception, la tâche retournée se terminera prématurément, à l’état Annulé, et l’exception, s’il y en a une, sera levée si vous appelez `get()` ou `wait()` pour cette tâche.

##  <a name="operator_eq_eq"></a>  opérateur ==, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est égal à l'objet `concurrent_vector` situé à droite.

```
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Le type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur simultané sur le côté gauche de l’opérateur est égal au vecteur simultané sur le côté droit de l’opérateur ; sinon **false**.

### <a name="remarks"></a>Notes

Deux vecteurs simultanés sont égaux s’ils ont le même nombre d’éléments et de leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Cette méthode n’est pas d’accès concurrentiel-safe en ce qui concerne les autres méthodes qui pourraient modifier un des vecteurs simultanés `_A` ou `_B`.

##  <a name="operator_neq"></a>  opérateur ! =, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur n'est pas égal à l'objet `concurrent_vector` situé à droite.

```
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Le type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**true** si les vecteurs simultanées ne sont pas égaux ; **false** si les vecteurs simultanés sont égaux.

### <a name="remarks"></a>Notes

Deux vecteurs simultanés sont égaux s’ils ont le même nombre d’éléments et de leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Cette méthode n’est pas d’accès concurrentiel-safe en ce qui concerne les autres méthodes qui pourraient modifier un des vecteurs simultanés `_A` ou `_B`.

##  <a name="operator_lt"></a>  opérateur&lt; opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur à l'objet `concurrent_vector` situé à droite.

```
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Le type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur simultané sur le côté gauche de l’opérateur est inférieur au vecteur simultané sur le côté droit de l’opérateur ; sinon **false**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans le `std` espace de noms.

Cette méthode n’est pas d’accès concurrentiel-safe en ce qui concerne les autres méthodes qui pourraient modifier un des vecteurs simultanés `_A` ou `_B`.

##  <a name="operator_lt_eq"></a>  opérateur&lt;=, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur ou égal à l'objet `concurrent_vector` situé à droite.

```
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Le type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur simultané sur le côté gauche de l’opérateur est inférieur ou égal au vecteur simultané sur le côté droit de l’opérateur, ; sinon **false**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans le `std` espace de noms.

Cette méthode n’est pas d’accès concurrentiel-safe en ce qui concerne les autres méthodes qui pourraient modifier un des vecteurs simultanés `_A` ou `_B`.

##  <a name="operator_gt"></a>  opérateur&gt; opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur à l'objet `concurrent_vector` situé à droite.

```
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Le type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur simultané sur le côté gauche de l’opérateur est supérieur au vecteur simultané sur le côté droit de l’opérateur ; sinon **false**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans le `std` espace de noms.

Cette méthode n’est pas d’accès concurrentiel-safe en ce qui concerne les autres méthodes qui pourraient modifier un des vecteurs simultanés `_A` ou `_B`.

##  <a name="operator_gt_eq"></a>  opérateur&gt;=, opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur ou égal à l'objet `concurrent_vector` situé à droite.

```
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs simultanés.

*A1*<br/>
Le type d’allocateur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’allocateur du deuxième `concurrent_vector` objet.

*_A*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**true** si le vecteur simultané sur le côté gauche de l’opérateur est supérieur ou égal au vecteur simultané sur le côté droit de l’opérateur ; sinon **false**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique à l’opérateur équivalent pour la `vector` classe dans le `std` espace de noms.

Cette méthode n’est pas d’accès concurrentiel-safe en ce qui concerne les autres méthodes qui pourraient modifier un des vecteurs simultanés `_A` ou `_B`.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
