---
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
ms.openlocfilehash: 8be17c8ab361272678c25326464261e153da6a49
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369642"
---
# <a name="recursivemutex-class"></a>recursive_mutex, classe

Représente un *type mutex*. Contrairement à [mutex](../standard-library/mutex-class-stl.md), le comportement est bien défini pour les appels aux méthodes de verrouillage sur des objets qui sont déjà verrouillés.

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
|[lock](#lock)|Bloque le thread appelant jusqu’à ce que le thread obtienne la propriété du mutex.|
|[try_lock](#try_lock)|Tente d’obtenir la propriété du mutex sans bloquer le thread.|
|[unlock](#unlock)|Libère la propriété du mutex.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<mutex >

**Espace de noms :** std

## <a name="lock"></a>  lock

Bloque le thread appelant jusqu'à ce que le thread obtienne la propriété du `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la méthode est retournée immédiatement, et le verrou précédent reste en vigueur.

## <a name="recursive_mutex"></a>  recursive_mutex

Construit un objet `recursive_mutex` qui n’est pas verrouillé.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

Libère les ressources utilisées par l’objet.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Notes

Si l'objet est verrouillé lorsque le destructeur s'exécute, le comportement est indéfini.

## <a name="try_lock"></a>  try_lock

Tente d'obtenir la propriété de la référence `mutex` sans se bloquer.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valeur de retour

**true** si la méthode obtient correctement la propriété de la `mutex` ou si le thread appelant possède déjà le `mutex**; otherwise, **false`.

### <a name="remarks"></a>Notes

Si le thread appelant possède déjà le `mutex`, la fonction retourne immédiatement **true**, et le verrou précédent reste en vigueur.

## <a name="unlock"></a>  unlock

Libère la propriété du mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Cette méthode libère la propriété du `mutex` uniquement si elle a été appelée autant de fois que [lock](#lock) et [try_lock](#try_lock) ont été appelés avec succès sur l’objet `recursive_mutex`.

Si le thread appelant ne possède pas `mutex`, le comportement est indéfini.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
