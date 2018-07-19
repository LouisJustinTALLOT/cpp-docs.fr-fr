---
title: mutex, classe (Bibliothèque standard C++)| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
dev_langs:
- C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 84a6b685501927d9fbd79fa7c82a90c5671f70b2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958943"
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

**En-tête :** \<mutex >

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

**true** si la méthode obtient correctement la propriété de la `mutex`; sinon, **false**.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà `mutex`, le comportement est indéfini.

## <a name="unlock"></a>  mutex::Unlock

Libère la propriété du `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
