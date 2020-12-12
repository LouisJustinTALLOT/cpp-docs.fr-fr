---
description: 'En savoir plus sur &lt; : &gt; fonctions et variables mutex'
title: '&lt;mutex&gt;, fonctions et variables'
ms.date: 11/04/2016
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: e06fe09c78d8b79f5dd804e64ef11e84c558ba24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338262"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt;, fonctions et variables

## <a name="adopt_lock"></a><a name="adopt_lock"></a> adopt_lock

Représente un objet pouvant être passé aux constructeurs pour [lock_guard](../standard-library/lock-guard-class.md) et [unique_lock](../standard-library/unique-lock-class.md) afin d’indiquer que l’objet mutex qui est également passé au constructeur est verrouillé.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a><a name="call_once"></a> call_once

Fournit un mécanisme permettant d'appeler un objet spécifique pouvant être appelé une seule fois durant l'exécution.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Paramètres

*Activé*\
Objet [once_flag](../standard-library/once-flag-structure.md) qui permet de s’assurer que l’objet pouvant être appelé n’est appelé qu’une seule fois.

*FA*\
Objet pouvant être appelé.

*Un*\
Liste d’arguments.

### <a name="remarks"></a>Notes

Si l' *indicateur* n’est pas valide, la fonction lève une [system_error](../standard-library/system-error-class.md) avec un code d’erreur `invalid_argument` . Dans le cas contraire, la fonction de modèle utilise son argument *Flag* pour s’assurer qu’elle appelle `F(A...)` correctement une seule fois, quel que soit le nombre de fois que la fonction de modèle est appelée. Si `F(A...)` se termine en levant une exception, l’appel n’a pas réussi.

## <a name="defer_lock"></a><a name="defer_lock"></a> defer_lock

Représente un objet qui peut être passé au constructeur pour [unique_lock](../standard-library/unique-lock-class.md). Cela indique que le constructeur ne doit pas verrouiller l’objet mutex qui lui est également passé.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a><a name="lock"></a> Lock

Tente de verrouiller tous les arguments sans interblocage.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Notes

Les arguments de la fonction de modèle doivent être des *types mutex*, sauf que les appels à `try_lock` peuvent lever des exceptions.

La fonction verrouille tous ses arguments sans blocage par des appels à `lock`, `try_lock` et `unlock`. Si un appel à `lock` ou `try_lock` lève une exception, la fonction appelle `unlock` sur l’un des objets mutex qui ont été correctement verrouillés avant de relever l’exception.

## <a name="swap"></a><a name="swap"></a> échange

```cpp
template <class Mutex>
void swap(unique_lock<Mutex>& x, unique_lock<Mutex>& y) noexcept;
```

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

```cpp
template <class L1, class L2, class... L3> int try_lock(L1&, L2&, L3&...);
```

## <a name="try_to_lock"></a><a name="try_to_lock"></a> try_to_lock

Représente un objet pouvant être passé au constructeur pour [unique_lock](../standard-library/unique-lock-class.md), afin d’indiquer que le constructeur doit essayer de déverrouiller le `mutex` qui lui est également passé sans blocage.

```cpp
const try_to_lock_t try_to_lock;
```
