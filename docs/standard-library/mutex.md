---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 377ec995f4e61c957e8e620749f96523b60fed3e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240597"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Incluez l’en-tête standard \<mutex> pour définir les classes `mutex`, `recursive_mutex`, `timed_mutex` et `recursive_timed_mutex`, les modèles `lock_guard` et `unique_lock`, ainsi que les types et fonctions qui définissent les régions de code de mutex.

> [!WARNING]
> À compter de Visual Studio 2015, les types de synchronisation de bibliothèque C++ Standard sont basés sur les primitives de synchronisation Windows et n’utilisent plus ConcRT (sauf si la plateforme cible est Windows XP). Les types définis dans \<mutex> ne doivent pas être utilisés avec des fonctions ou types ConcRT.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<mutex >

**Espace de noms :** std

## <a name="remarks"></a>Notes

> [!NOTE]
> Dans le code est compilé à l’aide de **/CLR**, cet en-tête est bloqué.

Les classes `mutex` et `recursive_mutex` sont des *types mutex*. Un type mutex a un constructeur par défaut et un destructeur qui ne lève pas d'exceptions. Ces objets ont des méthodes qui fournissent un mutex quand plusieurs threads essaient de verrouiller le même objet. Plus précisément, un type mutex contient les méthodes `lock`, `try_lock` et `unlock` :

- La méthode `lock` bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du mutex. Sa valeur de retour est ignorée.

- La méthode `try_lock` tente d'obtenir la propriété du mutex sans se bloquer. Son type de retour est convertible en **bool** et est **true** si la méthode obtient la propriété, mais est sinon **false**.

- La méthode `unlock` libère la propriété du mutex du thread appelant.

Vous pouvez utiliser les types mutex comme arguments de type pour instancier les modèles `lock_guard` et `unique_lock`. Vous pouvez utiliser des objets de ces types en tant qu’arguments `Lock` des fonctions membres d’attente (wait) dans le modèle [condition_variable_any](../standard-library/condition-variable-any-class.md).

Un *type mutex limité dans le temps* répond aux exigences d’un type mutex. En outre, il a le `try_lock_for` et `try_lock_until` méthodes qui doivent pouvoir être appelée à l’aide d’un seul argument et doivent retourner un type convertible en **bool**. Un type mutex limité dans le temps peut définir ces fonctions à l’aide d’arguments supplémentaires, à condition que ces arguments supplémentaires aient tous des valeurs par défaut.

- La méthode `try_lock_for` doit pouvoir être appelée à l’aide d’un seul argument, `Rel_time`, dont le type est une instanciation de [chrono::duration](../standard-library/duration-class.md). La méthode essaie d'obtenir la propriété du mutex. Toutefois, elle retourne une valeur dans le temps imparti désigné par `Rel_time`, indépendamment de la réussite de l'opération. Convertit la valeur de retour **true** si la méthode obtienne la propriété ; sinon, la valeur de retour convertit **false**.

- La méthode `try_lock_until` doit pouvoir être appelée à l’aide d’un seul argument, `Abs_time`, dont le type est une instanciation de [chrono::time_point](../standard-library/time-point-class.md). La méthode essaie d'obtenir la propriété du mutex. Toutefois, elle retourne une valeur dans le temps imparti désigné par `Abs_time`, indépendamment de la réussite de l'opération. Convertit la valeur de retour **true** si la méthode obtienne la propriété ; sinon, la valeur de retour convertit **false**.

Un type mutex est également appelé *type verrouillable*. S’il ne fournit pas la fonction membre `try_lock`, il s’agit d’un *type verrouillable de base*. Un type mutex limité dans le temps est également appelé *type verrouillable limité dans le temps*.

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|-|
|[lock_guard, classe](../standard-library/lock-guard-class.md)|Représente un modèle qui peut être instancié pour créer un objet dont le destructeur déverrouille un `mutex`.|
|[mutex, classe (Bibliothèque standard C++ )](../standard-library/mutex-class-stl.md)|Représente un type mutex. Utilisez les objets de ce type pour appliquer une exclusion mutuelle (mutex) dans un programme.|
|[recursive_mutex, classe](../standard-library/recursive-mutex-class.md)|Représente un type mutex. Contrairement à la classe `mutex`, le comportement d'appel des méthodes de verrouillage pour les objets qui sont déjà verrouillés est bien défini.|
|[recursive_timed_mutex, classe](../standard-library/recursive-timed-mutex-class.md)|Représente un type mutex limité dans le temps. Utilisez les objets de ce type pour appliquer une exclusion mutuelle (mutex) dont le blocage est limité dans le temps au sein d'un programme. Contrairement aux objets de type `timed_mutex`, l'effet de l'appel des méthodes de verrouillage pour les objets `recursive_timed_mutex` est bien défini.|
|[scoped_lock, classe](../standard-library/scoped-lock-class.md)||
|[timed_mutex, classe](../standard-library/timed-mutex-class.md)|Représente un type mutex limité dans le temps. Utilisez les objets de ce type pour appliquer une exclusion mutuelle (mutex) dont le blocage est limité dans le temps au sein d'un programme.|
|[unique_lock, classe](../standard-library/unique-lock-class.md)|Représente un modèle qui peut être instancié pour créer des objets qui gèrent le verrouillage et le déverrouillage d'un `mutex`.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|Fournit un mécanisme permettant d'appeler un objet spécifique pouvant être appelé une seule fois durant l'exécution.|
|[lock](../standard-library/mutex-functions.md#lock)|Tente de verrouiller tous les arguments sans interblocage.|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>Structs

|||
|-|-|
|[adopt_lock_t, structure](../standard-library/adopt-lock-t-structure.md)|Représente un type utilisé pour définir `adopt_lock`.|
|[defer_lock_t, structure](../standard-library/defer-lock-t-structure.md)|Représente un type qui définit un objet `defer_lock` permettant de sélectionner l'un des constructeurs surchargés de `unique_lock`.|
|[once_flag, structure](../standard-library/once-flag-structure.md)|Représente un **struct** qui est utilisé avec la fonction de modèle `call_once` pour vous assurer que l’initialisation le code est appelé une seule fois, même en présence de plusieurs threads d’exécution.|
|[try_to_lock_t, structure](../standard-library/try-to-lock-t-structure.md)|Représente un **struct** qui définit un `try_to_lock` de l’objet et permet de sélectionner un des constructeurs surchargés de `unique_lock`.|

### <a name="variables"></a>Variables

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Représente un objet pouvant être passé aux constructeurs pour `lock_guard` et `unique_lock` afin d'indiquer que l'objet mutex qui est également passé au constructeur est verrouillé.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Représente un objet pouvant être passé au constructeur pour `unique_lock`, afin d'indiquer que le constructeur ne doit pas verrouiller l'objet mutex qui lui est également passé.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Représente un objet pouvant être passé au constructeur pour `unique_lock`, afin d'indiquer que le constructeur doit essayer de déverrouiller le `mutex` qui lui est également passé sans blocage.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
