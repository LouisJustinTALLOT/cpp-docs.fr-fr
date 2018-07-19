---
title: '&lt;mutex&gt;, fonctions et variables | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: df52b5bdf9b7054fd838b1892c4e641cdf9d4dcc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962186"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt;, fonctions et variables

||||
|-|-|-|
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|
|[lock](#lock)|[try_to_lock](#try_to_lock)|

## <a name="adopt_lock"></a> adopt_lock, variable

Représente un objet pouvant être passé aux constructeurs pour [lock_guard](../standard-library/lock-guard-class.md) et [unique_lock](../standard-library/unique-lock-class.md) afin d’indiquer que l’objet mutex qui est également passé au constructeur est verrouillé.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>  call_once

Fournit un mécanisme permettant d'appeler un objet spécifique pouvant être appelé une seule fois durant l'exécution.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Paramètres

*Indicateur* A [once_flag](../standard-library/once-flag-structure.md) objet qui permet de s’assurer que l’objet pouvant être est appelée uniquement une fois.

*F* un objet pouvant être appelé.

*Un* une liste d’arguments.

### <a name="remarks"></a>Notes

Si *indicateur* n’est pas valide, la fonction lève un [system_error](../standard-library/system-error-class.md) avec le code d’erreur `invalid_argument`. Sinon, la fonction de modèle utilise son *indicateur* argument pour vous assurer qu’elle appelle `F(A...)` correctement exactement une fois, quel que soit le nombre de fois où la fonction de modèle est appelée. Si `F(A...)` se termine en levant une exception, l’appel n’a pas réussi.

## <a name="defer_lock"></a>  defer_lock, variable

Représente un objet qui peut être passé au constructeur pour [unique_lock](../standard-library/unique-lock-class.md). Cela indique que le constructeur ne doit pas verrouiller l’objet mutex qui lui est également passé.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>  lock

Tente de verrouiller tous les arguments sans interblocage.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Notes

Les arguments de la fonction de modèle doivent être des *types mutex*, sauf que les appels à `try_lock` peuvent lever des exceptions.

La fonction verrouille tous ses arguments sans blocage par des appels à `lock`, `try_lock` et `unlock`. Si un appel à `lock` ou `try_lock` lève une exception, la fonction appelle `unlock` sur l’un des objets mutex qui ont été correctement verrouillés avant de relever l’exception.

## <a name="try_to_lock"></a>  try_to_lock, variable

Représente un objet pouvant être passé au constructeur pour [unique_lock](../standard-library/unique-lock-class.md), afin d’indiquer que le constructeur doit essayer de déverrouiller le `mutex` qui lui est également passé sans blocage.

```cpp
const try_to_lock_t try_to_lock;
```

## <a name="see-also"></a>Voir aussi

[\<mutex>](../standard-library/mutex.md)<br/>
