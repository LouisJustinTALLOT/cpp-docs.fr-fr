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
ms.openlocfilehash: 111d48b9c4a575078f2342bfaa944871bbd628f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394336"
---
# <a name="readerwriterlock-class"></a>reader_writer_lock, classe

Verrou de lecteur-writer basé sur une file d'attente à préférence de writer avec rotation uniquement locale. Le verrou accorde un accès Premier entré, premier sorti aux writers et prive les lecteurs sous une charge continue de writers.

## <a name="syntax"></a>Syntaxe

```
class reader_writer_lock;
```

## <a name="members"></a>Membres

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[reader_writer_lock::scoped_lock, classe](#scoped_lock_class)|Un wrapper RAII sécurisé qui peut être utilisé pour acquérir `reader_writer_lock` verrouiller les objets en tant que rédacteur.|
|[reader_writer_lock::scoped_lock_read, classe](#scoped_lock_read_class)|Un wrapper RAII sécurisé qui peut être utilisé pour acquérir `reader_writer_lock` verrouiller les objets en tant que lecteur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Construit un nouvel `reader_writer_lock` objet.|
|[~ reader_writer_lock, destructeur](#dtor)|Détruit le `reader_writer_lock` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[lock](#lock)|Acquiert le verrou de lecteur-writer en tant que rédacteur.|
|[lock_read](#lock_read)|Acquiert le verrou de lecteur-writer en tant que lecteur. Si des writers, lecteurs actifs doivent attendre jusqu'à ce qu’elles sont effectuées. Le lecteur simplement inscrit un intérêt dans le verrou et attend que writers à le libérer.|
|[try_lock](#try_lock)|Tente d’acquérir le verrou de lecteur-writer en tant que rédacteur sans blocage.|
|[try_lock_read](#try_lock_read)|Tente d’acquérir le verrou de lecteur-writer en tant que lecteur sans blocage.|
|[unlock](#unlock)|Déverrouille le verrou de lecteur-writer basé sur qui a verrouillé, le lecteur ou writer.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [les Structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`reader_writer_lock`

## <a name="requirements"></a>Configuration requise

**En-tête :** concrt.h

**Espace de noms :** concurrency

##  <a name="lock"></a> Verrou

Acquiert le verrou de lecteur-writer en tant que rédacteur.

```
void lock();
```

### <a name="remarks"></a>Notes

Il est souvent préférable d’utiliser le [scoped_lock](#scoped_lock_class) construction pour acquérir et libérer un `reader_writer_lock` objet en tant que rédacteur dans une exception sûre.

Une fois un writer essaie d’acquérir le verrou, tous les futurs lecteurs se bloquera jusqu'à ce que les enregistreurs ont acquis et libéré le verrou. Ce verrou est orienté vers les writers et peut priver les lecteurs sous une charge continue de writers.

Les writers sont chaînés afin qu’un writer de fermeture du verrou libère le writer suivant.

Si le verrou est déjà détenu par le contexte d’appel, un [improper_lock](improper-lock-class.md) exception sera levée.

##  <a name="lock_read"></a> lock_read

Acquiert le verrou de lecteur-writer en tant que lecteur. Si des writers, lecteurs actifs doivent attendre jusqu'à ce qu’elles sont effectuées. Le lecteur simplement inscrit un intérêt dans le verrou et attend que writers à le libérer.

```
void lock_read();
```

### <a name="remarks"></a>Notes

Il est souvent préférable d’utiliser le [scoped_lock_read](#scoped_lock_read_class) construction pour acquérir et libérer un `reader_writer_lock` objet sous la forme d’un lecteur dans une exception sûre.

Si des writers en attente sur le verrou, le lecteur attendra jusqu'à ce que tous les enregistreurs de ligne ont acquis et libéré le verrou. Ce verrou est orienté vers les writers et peut priver les lecteurs sous une charge continue de writers.

##  <a name="ctor"></a> reader_writer_lock

Construit un nouvel `reader_writer_lock` objet.

```
reader_writer_lock();
```

##  <a name="dtor"></a> ~reader_writer_lock

Détruit le `reader_writer_lock` objet.

```
~reader_writer_lock();
```

### <a name="remarks"></a>Notes

Il est probable que le verrou n’est plus conservé lorsque le destructeur s’exécute. Autoriser le verrou de writer de lecteur détruire avec le verrou maintenu toujours résultats dans un comportement non défini.

##  <a name="scoped_lock_class"></a>  reader_writer_lock::scoped_lock Class

Un wrapper RAII sécurisé qui peut être utilisé pour acquérir `reader_writer_lock` verrouiller les objets en tant que rédacteur.

```
class scoped_lock;
```

## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock

Construit un `scoped_lock` de l’objet et acquiert le `reader_writer_lock` objet passé dans le `_Reader_writer_lock` paramètre en tant que rédacteur. Si le verrou est maintenu par un autre thread, cet appel bloquera.

```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

#### <a name="parameters"></a>Paramètres

*_Reader_writer_lock*<br/>
Le `reader_writer_lock` objet acquérir en tant que rédacteur.

## <a name="scoped_lock_dtor"></a> scoped_lock :: ~ scoped_lock

Détruit un `reader_writer_lock` de l’objet et libère le verrou fourni dans son constructeur.

```
~scoped_lock();
```

##  <a name="scoped_lock_read_class"></a>  reader_writer_lock::scoped_lock_read, classe

Un wrapper RAII sécurisé qui peut être utilisé pour acquérir `reader_writer_lock` verrouiller les objets en tant que lecteur.

```
class scoped_lock_read;
```

##  <a name="try_lock"></a> try_lock

Tente d’acquérir le verrou de lecteur-writer en tant que rédacteur sans blocage.

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read

Construit un `scoped_lock_read` de l’objet et acquiert le `reader_writer_lock` objet passé dans le `_Reader_writer_lock` paramètre en tant que lecteur. Si le verrou est maintenu par un autre thread en tant que rédacteur ou sont en attente de writers, cet appel bloquera.

```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

#### <a name="parameters"></a>Paramètres

*_Reader_writer_lock*<br/>
Le `reader_writer_lock` objet acquérir en tant que lecteur.

## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock::scoped_lock_read :: ~ scoped_lock_read, destructeur

Détruit un `scoped_lock_read` de l’objet et libère le verrou fourni dans son constructeur.

```
~scoped_lock_read();
```

## <a name="try_lock"></a> try_lock

```
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **true**; sinon, la valeur **false**.

##  <a name="try_lock_read"></a> try_lock_read

Tente d’acquérir le verrou de lecteur-writer en tant que lecteur sans blocage.

```
bool try_lock_read();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, la valeur **true**; sinon, la valeur **false**.

##  <a name="unlock"></a> Déverrouiller

Déverrouille le verrou de lecteur-writer basé sur qui a verrouillé, le lecteur ou writer.

```
void unlock();
```

### <a name="remarks"></a>Notes

Si des writers en attente sur le verrou, la libération du verrou passera toujours au writer suivant dans l’ordre FIFO. Ce verrou est orienté vers les writers et peut priver les lecteurs sous une charge continue de writers.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[critical_section, classe](critical-section-class.md)
