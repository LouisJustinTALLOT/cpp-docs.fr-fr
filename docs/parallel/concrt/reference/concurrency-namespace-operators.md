---
title: concurrency, opérateur de l’espace de noms
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374381"
---
# <a name="concurrency-namespace-operators"></a>concurrency, opérateur de l’espace de noms

||||
|-|-|-|
|[opérateur!](#operator_neq)|[Opérateur&amp;&amp;](#operator_amp_amp)|[Opérateur&gt;](#operator_gt)|
|[Opérateur&gt;=](#operator_gt_eq)|[Opérateur&lt;](#operator_lt)|[Opérateur&lt;=](#operator_lt_eq)|
|[opérateur](#operator_eq_eq)|[&#124;&#124;de l’opérateur](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>opérateur&#124;&#124; Opérateur

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

*ReturnType (en)*<br/>
Type de la tâche retournée.

*Lhs*<br/>
Première tâche à associer à la tâche obtenue.

*rhs*<br/>
Seconde tâche à associer à la tâche obtenue.

### <a name="return-value"></a>Valeur de retour

Une tâche qui se termine avec succès lorsque l’une ou l’autre des tâches d’entrée a été accomplie avec succès. Si les tâches d’entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>`. Si les tâches d’entrée sont de type `void`, la tâche de sortie sera également `task<void>`.

### <a name="remarks"></a>Notes

Si les deux tâches sont annulées ou jettent des exceptions, la tâche retournée sera terminée dans l’état annulé, et l’une des exceptions, le cas échéant, sera lancée lorsque vous appelez `get()` ou `wait()` sur cette tâche.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>&amp; opérateur&amp;

Crée une tâche qui se terminera avec succès lorsque les deux tâches fournies que les arguments complètent avec succès.

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

*ReturnType (en)*<br/>
Type de la tâche retournée.

*Lhs*<br/>
Première tâche à associer à la tâche obtenue.

*rhs*<br/>
Seconde tâche à associer à la tâche obtenue.

### <a name="return-value"></a>Valeur de retour

Tâche qui s'effectue correctement lorsque les deux tâches d'entrée se sont correctement déroulées. Si les tâches d’entrée sont de type `T`, le résultat de cette fonction sera `task<std::vector<T>>`. Si les tâches d’entrée sont de type `void`, la tâche de sortie sera également `task<void>`.

### <a name="remarks"></a>Notes

Si l’une des tâches est annulée ou jette une exception, la tâche retournée se terminera tôt, dans l’état `get()` `wait()` annulé, et l’exception, si l’on se produit, sera jetée si vous appelez ou sur cette tâche.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>opérateurMD

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*A1*<br/>
Le type d’alloueur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’alloueur du deuxième `concurrent_vector` objet.

*_a*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**vrai** si le vecteur concomitant sur le côté gauche de l’opérateur est égal au vecteur concurrent sur le côté droit de l’opérateur; autrement **faux**.

### <a name="remarks"></a>Notes

Deux vecteurs simultanés sont égaux s’ils ont le même nombre d’éléments et leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Cette méthode n’est pas conforme à la sécurité en ce qui `_A` concerne `_B`d’autres méthodes qui pourraient modifier l’un ou l’autre des vecteurs concomitants ou .

## <a name="operator-operator"></a><a name="operator_neq"></a>opérateur!MD Opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur n'est pas égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*A1*<br/>
Le type d’alloueur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’alloueur du deuxième `concurrent_vector` objet.

*_a*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**vrai** si les vecteurs simultanés ne sont pas égaux; **faux** si les vecteurs simultanés sont égaux.

### <a name="remarks"></a>Notes

Deux vecteurs simultanés sont égaux s’ils ont le même nombre d’éléments et leurs éléments respectifs ont les mêmes valeurs. Sinon, elles sont inégales.

Cette méthode n’est pas conforme à la sécurité en ce qui `_A` concerne `_B`d’autres méthodes qui pourraient modifier l’un ou l’autre des vecteurs concomitants ou .

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>&lt; opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*A1*<br/>
Le type d’alloueur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’alloueur du deuxième `concurrent_vector` objet.

*_a*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**vrai** si le vecteur concomitant sur le côté gauche de l’opérateur est inférieur au vecteur concurrent sur le côté droit de l’opérateur; autrement **faux**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique `vector` à `std` l’opérateur équivalent pour la classe dans l’espace de nom.

Cette méthode n’est pas conforme à la sécurité en ce qui `_A` concerne `_B`d’autres méthodes qui pourraient modifier l’un ou l’autre des vecteurs concomitants ou .

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>opérateur&lt;et opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est inférieur ou égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*A1*<br/>
Le type d’alloueur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’alloueur du deuxième `concurrent_vector` objet.

*_a*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**vrai** si le vecteur concomitant sur le côté gauche de l’opérateur est inférieur ou égal au vecteur con concurrent sur le côté droit de l’opérateur; autrement **faux**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique `vector` à `std` l’opérateur équivalent pour la classe dans l’espace de nom.

Cette méthode n’est pas conforme à la sécurité en ce qui `_A` concerne `_B`d’autres méthodes qui pourraient modifier l’un ou l’autre des vecteurs concomitants ou .

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>&gt; opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*A1*<br/>
Le type d’alloueur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’alloueur du deuxième `concurrent_vector` objet.

*_a*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**vrai** si le vecteur concomitant sur le côté gauche de l’opérateur est supérieur au vecteur concurrent sur le côté droit de l’opérateur; autrement **faux**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique `vector` à `std` l’opérateur équivalent pour la classe dans l’espace de nom.

Cette méthode n’est pas conforme à la sécurité en ce qui `_A` concerne `_B`d’autres méthodes qui pourraient modifier l’un ou l’autre des vecteurs concomitants ou .

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>opérateur&gt;et opérateur

Teste si l'objet `concurrent_vector` situé à gauche de l'opérateur est supérieur ou égal à l'objet `concurrent_vector` situé à droite.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données des éléments stockés dans les vecteurs concomitants.

*A1*<br/>
Le type d’alloueur du premier `concurrent_vector` objet.

*A2*<br/>
Le type d’alloueur du deuxième `concurrent_vector` objet.

*_a*<br/>
Objet de type `concurrent_vector`.

*_B*<br/>
Objet de type `concurrent_vector`.

### <a name="return-value"></a>Valeur de retour

**vrai** si le vecteur concomitant sur le côté gauche de l’opérateur est supérieur ou égal au vecteur con concurrent sur le côté droit de l’opérateur; autrement **faux**.

### <a name="remarks"></a>Notes

Le comportement de cet opérateur est identique `vector` à `std` l’opérateur équivalent pour la classe dans l’espace de nom.

Cette méthode n’est pas conforme à la sécurité en ce qui `_A` concerne `_B`d’autres méthodes qui pourraient modifier l’un ou l’autre des vecteurs concomitants ou .

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
