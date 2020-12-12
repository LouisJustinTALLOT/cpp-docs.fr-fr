---
description: 'En savoir plus sur : mutex, classe (bibliothèque standard C++)'
title: mutex, classe (Bibliothèque standard C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 528fe0698fb7815be9b678d72055c54bad5ce2bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338275"
---
# <a name="mutex-class-c-standard-library"></a>mutex, classe (Bibliothèque standard C++)

Représente un *type Mutex*. Vous pouvez utiliser des objets de ce type pour appliquer une exclusion mutuelle dans un programme.

## <a name="syntax"></a>Syntaxe

```cpp
class mutex;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[relatif](#mutex)|Construit un objet `mutex`.|
|[mutex :: ~ mutex, destructeur](#dtormutex_destructor)|Libère toutes les ressources qui étaient utilisées par l’objet `mutex`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Lock](#lock)|Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.|
|[native_handle](#native_handle)|Retourne le type propre à l’implémentation qui représente le descripteur de mutex.|
|[try_lock](#try_lock)|Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.|
|[bloquer](#unlock)|Libère la propriété du `mutex`.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<mutex>

**Espace de noms :** std

## <a name="mutexlock"></a><a name="lock"></a> mutex :: Lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a> mutex :: mutex, constructeur

Construit un objet `mutex` qui n’est pas verrouillé.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a> mutex :: ~ mutex, destructeur

Libère les ressources utilisées par l’objet `mutex`.

```cpp
~mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="mutexnative_handle"></a><a name="native_handle"></a> mutex :: native_handle

Retourne le type propre à l’implémentation qui représente le descripteur de mutex. Vous pouvez utiliser le descripteur de plusieurs manières propres à l’implémentation.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur renvoyée

`native_handle_type` est défini comme un `Concurrency::critical_section *` converti en `void *`.

## <a name="mutextry_lock"></a><a name="try_lock"></a> mutex :: try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la méthode obtient avec succès la propriété de `mutex` ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="mutexunlock"></a><a name="unlock"></a> mutex :: Unlock

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
