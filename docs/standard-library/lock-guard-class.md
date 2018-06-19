---
title: lock_guard, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcbd0f17392c69b09d6f9f3c8123dfcf8b543fa4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852349"
---
# <a name="lockguard-class"></a>lock_guard, classe

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
|[lock_guard::~lock_guard, destructeur](#dtorlock_guard_destructor)|Déverrouille le `mutex` passé au constructeur.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<mutex >

**Espace de noms :** std

## <a name="lock_guard"></a> lock_guard::lock_guard, constructeur

Construit un objet `lock_guard`.

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>Paramètres

`Mtx` A *type mutex* objet.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet de type `lock_guard` et verrouille `Mtx`. Si `Mtx` n’est pas un mutex récursif, il doit être déverrouillé quand ce constructeur est appelé.

Le deuxième constructeur ne verrouille pas `Mtx`. `Mtx` doit être verrouillé quand ce constructeur est appelé. Le constructeur ne lève aucune exception.

## <a name="dtorlock_guard_destructor"></a> lock_guard::~lock_guard, destructeur

Déverrouille le `mutex` passé au constructeur.

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Notes

Si le `mutex` n’existe pas quand le destructeur s’exécute, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
