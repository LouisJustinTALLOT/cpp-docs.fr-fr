---
description: 'En savoir plus sur : classe recursive_mutex'
title: recursive_mutex, classe
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: f8a9c9322407871984c83135eecd2e26ac475d2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337894"
---
# <a name="recursive_mutex-class"></a>recursive_mutex, classe

Représente un *type Mutex*. Contrairement à [mutex](../standard-library/mutex-class-stl.md), le comportement est bien défini pour les appels aux méthodes de verrouillage sur des objets qui sont déjà verrouillés.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_mutex;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Construit un objet `recursive_mutex`.|
|[~recursive_mutex, destructeur](#dtorrecursive_mutex_destructor)|Libère les ressources utilisées par l’objet `recursive_mutex`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Lock](#lock)|Bloque le thread appelant jusqu’à ce que le thread obtienne la propriété du mutex.|
|[try_lock](#try_lock)|Tente d’obtenir la propriété du mutex sans bloquer le thread.|
|[bloquer](#unlock)|Libère la propriété du mutex.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<mutex>

**Espace de noms :** std

## <a name="lock"></a><a name="lock"></a> Lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la méthode est retournée immédiatement, et le verrou précédent reste en vigueur.

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a> recursive_mutex

Construit un objet `recursive_mutex` qui n’est pas verrouillé.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

Libère les ressources utilisées par l’objet.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la méthode réussit à obtenir la propriété du `mutex` ou si le thread appelant possède déjà le `mutex**; otherwise, **false` .

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex` , la fonction retourne immédiatement **`true`** , et le verrou précédent reste en vigueur.

## <a name="unlock"></a><a name="unlock"></a> bloquer

Libère la propriété du mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Cette méthode libère la propriété du `mutex` uniquement si elle a été appelée autant de fois que [lock](#lock) et [try_lock](#try_lock) ont été appelés avec succès sur l’objet `recursive_mutex`.

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
