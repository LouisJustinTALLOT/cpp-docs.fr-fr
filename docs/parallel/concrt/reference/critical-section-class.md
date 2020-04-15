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
ms.openlocfilehash: 24f96282a7728c6db6e0b05d36406f15383913f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372678"
---
# <a name="critical_section-class"></a>critical_section, classe

Mutex non réentrant qui a explicitement connaissance du runtime d'accès concurrentiel.

## <a name="syntax"></a>Syntaxe

```cpp
class critical_section;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`native_handle_type`|Référence à un objet `critical_section`.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[critical_section::scoped_lock, classe](#critical_section__scoped_lock_class)|Un emballage RAII sûr `critical_section` d’exception pour un objet.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[critical_section](#ctor)|Construit une nouvelle section critique.|
|[Destructeur critical_section](#dtor)|Détruit une section critique.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Verrouillage](#lock)|Acquiert cette section critique.|
|[native_handle](#native_handle)|Retourne une poignée native spécifique à la plate-forme, si l’on existe.|
|[try_lock](#try_lock)|Essaye d’acquérir la serrure sans bloquer.|
|[try_lock_for](#try_lock_for)|Essaye d’acquérir la serrure sans bloquer pour un nombre spécifique de millisecondes.|
|[Déverrouiller](#unlock)|Déverrouiller la section critique.|

## <a name="remarks"></a>Notes

Pour plus d’informations, voir [Structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`critical_section`

## <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

**Namespace:** concurrence

## <a name="critical_section"></a><a name="ctor"></a>critical_section

Construit une nouvelle section critique.

```cpp
critical_section();
```

## <a name="critical_section"></a><a name="dtor"></a>critical_section

Détruit une section critique.

```cpp
~critical_section();
```

### <a name="remarks"></a>Notes

On s’attend à ce que la serrure ne soit plus tenue lorsque le destructeur s’exécute. Permettre à la section critique de détruire avec la serrure a toujours tenu des résultats dans un comportement indéfini.

## <a name="lock"></a><a name="lock"></a>Verrouillage

Acquiert cette section critique.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Il est souvent plus [scoped_lock](#critical_section__scoped_lock_class) sûr d’utiliser le scoped_lock `critical_section` construire pour acquérir et libérer un objet d’une manière sûre d’exception.

Si le verrou est déjà tenu par le contexte d’appel, [une](improper-lock-class.md) improper_lock exception sera jetée.

## <a name="native_handle"></a><a name="native_handle"></a>native_handle

Retourne une poignée native spécifique à la plate-forme, si l’on existe.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valeur de retour

Une référence à la section critique.

### <a name="remarks"></a>Notes

Un `critical_section` objet n’est pas associé à une poignée native spécifique à la plate-forme pour le système d’exploitation Windows. La méthode renvoie simplement une référence à l’objet lui-même.

## <a name="critical_sectionscoped_lock-class"></a><a name="critical_section__scoped_lock_class"></a>critical_section::scoped_lock Classe

Un emballage RAII sûr `critical_section` d’exception pour un objet.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_ctor"></a>scoped_lock::scoped_lock

Construit un `scoped_lock` objet et `critical_section` acquiert `_Critical_section` l’objet passé dans le paramètre. Si la section critique est tenue par un autre thread, cet appel bloquera.

```cpp
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```

### <a name="parameters"></a>Paramètres

*_Critical_section*<br/>
La section critique à verrouiller.

## <a name="scoped_lockscoped_lock"></a><a name="critical_section__scoped_lock_dtor"></a>scoped_lock: : scoped_lock

Détruit un `scoped_lock` objet et libère la section critique fournie dans son constructeur.

```cpp
~scoped_lock();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Essaye d’acquérir la serrure sans bloquer.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **est vraie;** autrement, la valeur **fausse**.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Essaye d’acquérir la serrure sans bloquer pour un nombre spécifique de millisecondes.

```cpp
bool try_lock_for(unsigned int _Timeout);
```

### <a name="parameters"></a>Paramètres

*_Timeout*<br/>
Le nombre de millisecondes à attendre avant de chronométrer.

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **est vraie;** autrement, la valeur **fausse**.

## <a name="unlock"></a><a name="unlock"></a>Déverrouiller

Déverrouiller la section critique.

```cpp
void unlock();
```

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Classe reader_writer_lock](reader-writer-lock-class.md)
