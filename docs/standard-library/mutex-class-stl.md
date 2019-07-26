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
ms.openlocfilehash: 099cf17db7b99f9cd1d953a603db70f75c33358e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457059"
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
|[mutex](#mutex)|Construit un objet `mutex`.|
|[mutex::~mutex, destructeur](#dtormutex_destructor)|Libère toutes les ressources qui étaient utilisées par l’objet `mutex`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[lock](#lock)|Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.|
|[native_handle](#native_handle)|Retourne le type propre à l’implémentation qui représente le descripteur de mutex.|
|[try_lock](#try_lock)|Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.|
|[unlock](#unlock)|Libère la propriété du `mutex`.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> mutex

**Espace de noms :** std

## <a name="lock"></a>  mutex::lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="mutex"></a>  mutex::mutex, constructeur

Construit un objet `mutex` qui n’est pas verrouillé.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>  mutex::~mutex, destructeur

Libère les ressources utilisées par l’objet `mutex`.

```cpp
~mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="native_handle"></a>  mutex::native_handle

Retourne le type propre à l’implémentation qui représente le descripteur de mutex. Vous pouvez utiliser le descripteur de plusieurs manières propres à l’implémentation.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur de retour

`native_handle_type` est défini comme un `Concurrency::critical_section *` converti en `void *`.

## <a name="try_lock"></a>  mutex::try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

**true** si la méthode obtient avec succès la propriété de `mutex`; sinon, **false**.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="unlock"></a>  mutex::unlock

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
