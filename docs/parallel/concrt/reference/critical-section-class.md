---
title: critical_section, classe
ms.date: 11/04/2016
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
ms.openlocfilehash: aef3ae6100133374cb89098f118c447effafd840
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417151"
---
# <a name="critical_section-class"></a>critical_section, classe

Mutex non réentrant qui a explicitement connaissance du runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class critical_section;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`native_handle_type`|Référence à un objet `critical_section`.|

### <a name="public-classes"></a>Classes publiques

|Name|Description|
|----------|-----------------|
|[critical_section :: scoped_lock, classe](#critical_section__scoped_lock_class)|Wrapper RAII de sécurité d’exception pour un objet `critical_section`.|

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[critical_section](#ctor)|Construit une nouvelle section critique.|
|[Destructeur ~ critical_section](#dtor)|Détruit une section critique.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[lock](#lock)|Acquiert cette section critique.|
|[native_handle](#native_handle)|Retourne un handle natif spécifique à la plateforme, s’il en existe un.|
|[try_lock](#try_lock)|Tente d’acquérir le verrou sans blocage.|
|[try_lock_for](#try_lock_for)|Tente d’acquérir le verrou sans se bloquer pendant un nombre spécifique de millisecondes.|
|[unlock](#unlock)|Déverrouille la section critique.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`critical_section`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrency

## <a name="ctor"></a>critical_section

Construit une nouvelle section critique.

```cpp
critical_section();
```

## <a name="dtor"></a>~ critical_section

Détruit une section critique.

```cpp
~critical_section();
```

### <a name="remarks"></a>Notes

Il est supposé que le verrou n’est plus maintenu lors de l’exécution du destructeur. Le fait d’autoriser la destruction de la section critique avec le verrou toujours maintenu entraîne un comportement indéfini.

## <a name="lock"></a>Lock

Acquiert cette section critique.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Il est souvent plus sûr d’utiliser la construction [scoped_lock](#critical_section__scoped_lock_class) pour acquérir et libérer un objet `critical_section` en toute sécurité.

Si le verrou est déjà détenu par le contexte d’appel, une exception [improper_lock](improper-lock-class.md) sera levée.

## <a name="native_handle"></a>native_handle

Retourne un handle natif spécifique à la plateforme, s’il en existe un.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur de retour

Référence à la section critique.

### <a name="remarks"></a>Notes

Un objet `critical_section` n’est pas associé à un handle natif spécifique à une plateforme pour le système d’exploitation Windows. La méthode retourne simplement une référence à l’objet lui-même.

## <a name="critical_section__scoped_lock_class"></a>critical_section :: scoped_lock, classe

Wrapper RAII de sécurité d’exception pour un objet `critical_section`.

```cpp
class scoped_lock;
```

## <a name="critical_section__scoped_lock_ctor"></a>scoped_lock :: scoped_lock

Construit un objet `scoped_lock` et acquiert l’objet `critical_section` passé dans le paramètre `_Critical_section`. Si la section critique est détenue par un autre thread, cet appel sera bloqué.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Paramètres

*_Critical_section*<br/>
Section critique à verrouiller.

## <a name="critical_section__scoped_lock_dtor"></a>scoped_lock :: ~ scoped_lock

Détruit un objet `scoped_lock` et libère la section critique fournie dans son constructeur.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a>try_lock

Tente d’acquérir le verrou sans blocage.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **true**; Sinon, la valeur **false**.

## <a name="try_lock_for"></a>try_lock_for

Tente d’acquérir le verrou sans se bloquer pendant un nombre spécifique de millisecondes.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Paramètres

*_Timeout*<br/>
Nombre de millisecondes à attendre avant l’expiration du délai d’attente.

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **true**; Sinon, la valeur **false**.

## <a name="unlock"></a>bloquer

Déverrouille la section critique.

```cpp
void unlock();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[reader_writer_lock, classe](reader-writer-lock-class.md)
