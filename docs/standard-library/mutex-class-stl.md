---
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
ms.openlocfilehash: 84e6e3a46903a204444df9886556ae2c563304a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364846"
---
# <a name="mutex-class-c-standard-library"></a>mutex, classe (Bibliothèque standard C++)

Représente un *type mutex*. Vous pouvez utiliser des objets de ce type pour appliquer une exclusion mutuelle dans un programme.

## <a name="syntax"></a>Syntaxe

```cpp
class mutex;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Mutex](#mutex)|Construit un objet `mutex`.|
|[mutex::-mutex Destructor](#dtormutex_destructor)|Libère toutes les ressources qui étaient utilisées par l’objet `mutex`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Verrouillage](#lock)|Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.|
|[native_handle](#native_handle)|Retourne le type propre à l’implémentation qui représente le descripteur de mutex.|
|[try_lock](#try_lock)|Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.|
|[Déverrouiller](#unlock)|Libère la propriété du `mutex`.|

## <a name="requirements"></a>Spécifications

**En-tête:** \<mutex>

**Espace de noms :** std

## <a name="mutexlock"></a><a name="lock"></a>mutex::lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>mutex::mutex Constructor

Construit un objet `mutex` qui n’est pas verrouillé.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>mutex::-mutex Destructor

Libère les ressources utilisées par l’objet `mutex`.

```cpp
~mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="mutexnative_handle"></a><a name="native_handle"></a>mutex::native_handle

Retourne le type propre à l’implémentation qui représente le descripteur de mutex. Vous pouvez utiliser le descripteur de plusieurs manières propres à l’implémentation.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur de retour

`native_handle_type` est défini comme un `Concurrency::critical_section *` converti en `void *`.

## <a name="mutextry_lock"></a><a name="try_lock"></a>mutex::try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

**vrai** si la méthode obtient `mutex`avec succès la propriété de la ; autrement, **faux**.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="mutexunlock"></a><a name="unlock"></a>mutex::déverrouiller

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
