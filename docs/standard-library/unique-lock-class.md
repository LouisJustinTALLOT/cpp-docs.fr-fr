---
title: unique_lock, classe
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 189fd70ce10b6067646553f2b92a8fc09239d054
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212033"
---
# <a name="unique_lock-class"></a>unique_lock, classe

Représente un modèle qui peut être instancié pour créer des objets qui gèrent le verrouillage et le déverrouillage d'un `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Notes

L’argument de modèle `Mutex` doit nommer un *type mutex*.

En interne, un `unique_lock` stocke un pointeur vers un `mutex` objet associé et une valeur **`bool`** qui indique si le thread actuel possède le `mutex` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`mutex_type`|Synonyme de l’argument de modèle `Mutex`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[unique_lock](#unique_lock)|Construit un objet `unique_lock`.|
|[Destructeur ~ unique_lock](#dtorunique_lock_destructor)|Libère toutes les ressources associées à l’objet `unique_lock`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Lock](#lock)|Bloque le thread appelant jusqu’à ce que le thread obtienne la propriété du `mutex` associé.|
|[relatif](#mutex)|Récupère le pointeur stocké vers le `mutex` associé.|
|[owns_lock](#owns_lock)|Spécifie si le thread appelant possède le `mutex` associé.|
|[3/05](#release)|Dissocie l’objet `unique_lock` de l’objet `mutex` associé.|
|[swap](#swap)|Échange le `mutex` associé et l’état de propriété avec ceux d’un objet spécifié.|
|[try_lock](#try_lock)|Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.|
|[try_lock_for](#try_lock_for)|Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.|
|[try_lock_until](#try_lock_until)|Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.|
|[bloquer](#unlock)|Libère la propriété du `mutex` associé.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[bool, opérateur](#op_bool)|Spécifie si le thread appelant possède le `mutex` associé.|
|[opérateur =](#op_eq)|Copie le pointeur `mutex` stocké et l’état de propriété associé à partir d’un objet spécifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

*unique_lock*

## <a name="requirements"></a>Spécifications

**En-tête :**\<mutex>

**Espace de noms :** std

## <a name="lock"></a><a name="lock"></a>Lock

Bloque le thread appelant jusqu’à ce que le thread obtienne la propriété du `mutex` associé.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Si le pointeur stocké `mutex` est null, cette méthode lève une [system_error](../standard-library/system-error-class.md) qui a un code d’erreur `operation_not_permitted` .

Si le thread appelant possède déjà le `mutex` associé, cette méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.

Sinon, cette méthode appelle `lock` sur le associé `mutex` et affecte à l’indicateur de propriété de thread interne la valeur **`true`** .

## <a name="mutex"></a><a name="mutex"></a>relatif

Récupère le pointeur stocké vers le `mutex` associé.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="operator-bool"></a><a name="op_bool"></a>bool, opérateur

Spécifie si le thread appelant possède le mutex associé.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si le thread possède le mutex ; Sinon, **`false`** .

## <a name="operator"></a><a name="op_eq"></a>opérateur =

Copie le pointeur `mutex` stocké et l’état de propriété associé à partir d’un objet spécifié.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Objet `unique_lock`.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Si le thread appelant possède le `mutex` précédemment associé, avant que cette méthode appelle `unlock` sur le `mutex`, il assigne les nouvelles valeurs.

Après la copie, cette méthode définit un *autre* État sur un état construit par défaut.

## <a name="owns_lock"></a><a name="owns_lock"></a>owns_lock

Spécifie si le thread appelant possède le `mutex` associé.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si le thread possède le `mutex` ; sinon, **`false`** .

## <a name="release"></a><a name="release"></a>3/05

Dissocie l’objet `unique_lock` de l’objet `mutex` associé.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Valeur de retour

La valeur précédente du pointeur `mutex` stocké.

### <a name="remarks"></a>Notes

Cette méthode affecte la valeur 0 au pointeur stocké `mutex` et affecte à l’indicateur de propriété interne la valeur `mutex` **`false`** .

## <a name="swap"></a><a name="swap"></a>échange

Échange le `mutex` associé et l’état de propriété avec ceux d’un objet spécifié.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Objet `unique_lock`.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si la méthode obtient avec succès la propriété de `mutex` ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Si le pointeur stocké `mutex` est null, la méthode lève une [system_error](../standard-library/system-error-class.md) qui a un code d’erreur `operation_not_permitted` .

Si le thread appelant possède déjà le `mutex`, la méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Paramètres

*Rel_time*\
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété du `mutex`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la méthode obtient avec succès la propriété de `mutex` ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Si le pointeur stocké `mutex` est null, la méthode lève une [system_error](../standard-library/system-error-class.md) qui a un code d’erreur `operation_not_permitted` .

Si le thread appelant possède déjà le `mutex`, la méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Paramètres

*Abs_time*\
Point dans le temps qui spécifie le seuil au-delà duquel la méthode ne tente plus d'obtenir la propriété du `mutex`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si la méthode obtient avec succès la propriété de `mutex` ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Si le pointeur stocké `mutex` est null, la méthode lève une [system_error](../standard-library/system-error-class.md) qui a un code d’erreur `operation_not_permitted` .

Si le thread appelant possède déjà le `mutex`, la méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.

## <a name="unique_lock-constructor"></a><a name="unique_lock"></a>Constructeur unique_lock

Construit un objet `unique_lock`.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>Paramètres

*MTX*\
Objet de type mutex.

*Rel_time*\
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété du `mutex`.

*Abs_time*\
Point dans le temps qui spécifie le seuil au-delà duquel la méthode ne tente plus d'obtenir la propriété du `mutex`.

*Autres*\
Objet `unique_lock`.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet qui a une valeur de pointeur mutex associé de 0.

Le deuxième constructeur déplace l’État mutex associé d’un *autre*constructeur. Après le déplacement, *other* n’est plus associé à un mutex.

Les constructeurs restants stockent & *MTX* comme `mutex` pointeur stocké. L’appartenance du `mutex` est déterminée par le deuxième argument, s’il existe.

|||
|-|-|
|`No argument`|L’appartenance est obtenue en appelant la méthode `lock` sur l’objet `mutex` associé.|
|`Adopt`|L’appartenance est supposée. `Mtx` doit être verrouillé quand le constructeur est appelé.|
|`Defer`|Le thread appelant est supposé ne pas posséder l’objet `mutex`. `Mtx` ne doit pas être verrouillé quand le constructeur est appelé.|
|`Try`|L’appartenance est déterminée en appelant `try_lock` sur l’objet `mutex` associé. Le constructeur ne lève aucune exception.|
|`Rel_time`|L’appartenance est déterminée en appelant `try_lock_for(Rel_time)`.|
|`Abs_time`|L’appartenance est déterminée en appelant `try_lock_until(Abs_time)`.|

## <a name="unique_lock-destructor"></a><a name="dtorunique_lock_destructor"></a>  ~unique_lock, destructeur

Libère toutes les ressources associées à l’objet `unique_lock`.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Notes

Si le thread appelant possède le `mutex` associé, le destructeur libère la propriété en appelant unlock sur l’objet `mutex`.

## <a name="unlock"></a><a name="unlock"></a>bloquer

Libère la propriété du `mutex` associé.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si le thread appelant ne possède pas le `mutex` associé, cette méthode lève une [system_error](../standard-library/system-error-class.md) avec le code d’erreur `operation_not_permitted`.

Sinon, cette méthode appelle `unlock` sur le associé `mutex` et affecte à l’indicateur de propriété de thread interne la valeur **`false`** .

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
