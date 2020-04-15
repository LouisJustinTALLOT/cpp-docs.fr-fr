---
title: reader_writer_lock, classe
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 13b44387f3e9489090ec31345fe4347ff5f205ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376239"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock, classe

Verrou de lecteur-writer basé sur une file d'attente à préférence de writer avec rotation uniquement locale. Le verrou accorde un accès Premier entré, premier sorti aux writers et prive les lecteurs sous une charge continue de writers.

## <a name="syntax"></a>Syntaxe

```cpp
class reader_writer_lock;
```

## <a name="members"></a>Membres

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[reader_writer_lock::scoped_lock, classe](#scoped_lock_class)|Un emballage RAII sûr d’exception `reader_writer_lock` qui peut être employé pour acquérir des objets de serrure en tant qu’auteur.|
|[reader_writer_lock::scoped_lock_read, classe](#scoped_lock_read_class)|Un emballage RAII sûr d’exception `reader_writer_lock` qui peut être employé pour acquérir des objets de verrouillage en tant que lecteur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Construit un nouvel objet `reader_writer_lock`.|
|[Destructeur reader_writer_lock](#dtor)|Détruit l’objet. `reader_writer_lock`|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Verrouillage](#lock)|Acquiert le verrou lecteur-écrivain en tant qu’écrivain.|
|[lock_read](#lock_read)|Acquiert le verrou lecteur-écrivain en tant que lecteur. S’il y a des écrivains, les lecteurs actifs doivent attendre jusqu’à ce qu’ils soient faits. Le lecteur enregistre simplement un intérêt pour la serrure et attend que les écrivains le libèrent.|
|[try_lock](#try_lock)|Tentatives d’acquérir le verrou lecteur-écrivain comme un écrivain sans blocage.|
|[try_lock_read](#try_lock_read)|Tentatives d’acquérir le verrou lecteur-écrivain comme un lecteur sans bloquer.|
|[Déverrouiller](#unlock)|Débloque le verrou lecteur-écrivain en fonction de qui l’a verrouillé, lecteur ou écrivain.|

## <a name="remarks"></a>Notes

Pour plus d’informations, voir [Structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`reader_writer_lock`

## <a name="requirements"></a>Spécifications

**En-tête:** concrt.h

**Namespace:** concurrence

## <a name="lock"></a><a name="lock"></a>Verrouillage

Acquiert le verrou lecteur-écrivain en tant qu’écrivain.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Il est souvent plus [scoped_lock](#scoped_lock_class) sûr d’utiliser le scoped_lock `reader_writer_lock` construire pour acquérir et libérer un objet en tant qu’écrivain d’une manière sûre exception.

Après un écrivain tente d’acquérir la serrure, tous les futurs lecteurs bloqueront jusqu’à ce que les écrivains ont acquis et libéré avec succès la serrure. Ce verrou est biaisé vers les écrivains et peut affamer les lecteurs sous une charge continue d’écrivains.

Les écrivains sont enchaînés de sorte qu’un écrivain sortant de la serrure libère le prochain écrivain en ligne.

Si le verrou est déjà tenu par le contexte d’appel, [une](improper-lock-class.md) improper_lock exception sera jetée.

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Acquiert le verrou lecteur-écrivain en tant que lecteur. S’il y a des écrivains, les lecteurs actifs doivent attendre jusqu’à ce qu’ils soient faits. Le lecteur enregistre simplement un intérêt pour la serrure et attend que les écrivains le libèrent.

```cpp
void lock_read();
```

### <a name="remarks"></a>Notes

Il est souvent plus [scoped_lock_read](#scoped_lock_read_class) sûr d’utiliser la `reader_writer_lock` scoped_lock_read construire pour acquérir et libérer un objet en tant que lecteur d’une manière sûre d’exception.

S’il ya des écrivains en attente sur la serrure, le lecteur attendra jusqu’à ce que tous les écrivains en ligne ont acquis et libéré la serrure. Ce verrou est biaisé vers les écrivains et peut affamer les lecteurs sous une charge continue d’écrivains.

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

Construit un nouvel objet `reader_writer_lock`.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>reader_writer_lock

Détruit l’objet. `reader_writer_lock`

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Notes

On s’attend à ce que la serrure ne soit plus tenue lorsque le destructeur s’exécute. Permettre à l’auteur lecteur de verrouiller de détruire avec la serrure encore tenu résultats dans un comportement indéfini.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock::scoped_lock Classe

Un emballage RAII sûr d’exception `reader_writer_lock` qui peut être employé pour acquérir des objets de serrure en tant qu’auteur.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock::scoped_lock

Construit un `scoped_lock` objet et `reader_writer_lock` acquiert `_Reader_writer_lock` l’objet passé dans le paramètre en tant qu’écrivain. Si le verrou est tenu par un autre thread, cet appel bloquera.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Paramètres

*_Reader_writer_lock*<br/>
L’objet `reader_writer_lock` à acquérir en tant qu’écrivain.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock: : scoped_lock

Détruit un `reader_writer_lock` objet et libère la serrure fournie dans son constructeur.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock::scoped_lock_read Classe

Un emballage RAII sûr d’exception `reader_writer_lock` qui peut être employé pour acquérir des objets de verrouillage en tant que lecteur.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read::scoped_lock_read

Construit un `scoped_lock_read` objet et `reader_writer_lock` acquiert `_Reader_writer_lock` l’objet passé dans le paramètre en tant que lecteur. Si la serrure est tenue par un autre fil en tant qu’écrivain ou il ya des écrivains en attente, cet appel va bloquer.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Paramètres

*_Reader_writer_lock*<br/>
L’objet `reader_writer_lock` à acquérir en tant que lecteur.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock::scoped_lock_read::-scoped_lock_read Destructor

Détruit un `scoped_lock_read` objet et libère la serrure fournie dans son constructeur.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Tentatives d’acquérir le verrou lecteur-écrivain comme un écrivain sans blocage.

### <a name="syntax"></a>Syntaxe

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **est vraie;** autrement, la valeur **fausse**.

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Tentatives d’acquérir le verrou lecteur-écrivain comme un lecteur sans bloquer.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **est vraie;** autrement, la valeur **fausse**.

## <a name="unlock"></a><a name="unlock"></a>Déverrouiller

Débloque le verrou lecteur-écrivain en fonction de qui l’a verrouillé, lecteur ou écrivain.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

S’il ya des écrivains en attente sur la serrure, la libération de la serrure sera toujours aller à l’auteur suivant dans l’ordre FIFO. Ce verrou est biaisé vers les écrivains et peut affamer les lecteurs sous une charge continue d’écrivains.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[Classe critical_section](critical-section-class.md)
