---
title: lock_guard, classe
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351718"
---
# <a name="lock_guard-class"></a>lock_guard, classe

Représente un modèle qui peut être instancié pour créer un objet dont le destructeur déverrouille un `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Notes

L’argument de modèle `Mutex` doit nommer un *type mutex*.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`lock_guard::mutex_type`|Synonyme de l’argument de modèle `Mutex`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[lock_guard](#lock_guard)|Construit un objet `lock_guard`.|
|[lock_guard: Lock_guard Destructor](#dtorlock_guard_destructor)|Déverrouille le `mutex` passé au constructeur.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<mutex>

**Espace de noms :** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>lock_guard::lock_guard Constructeur

Construit un objet `lock_guard`.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Paramètres

*Mtx*\
Objet de *type mutex*.

### <a name="remarks"></a>Notes

Le premier constructeur construit un `lock_guard` objet de type et verrouille *Mtx*. Si *Mtx* n’est pas un mutex récursif, il doit être déverrouillé lorsque ce constructeur est appelé.

Le deuxième constructeur ne verrouille pas *Mtx*. *Mtx* doit être verrouillé lorsque ce constructeur est appelé. Le constructeur ne lève aucune exception.

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard: Lock_guard Destructor

Déverrouille le `mutex` passé au constructeur.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Notes

Si le `mutex` n’existe pas quand le destructeur s’exécute, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
