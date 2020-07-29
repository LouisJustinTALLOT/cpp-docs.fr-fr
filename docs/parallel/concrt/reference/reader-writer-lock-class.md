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
ms.openlocfilehash: e4c38a6e1f1a1c6f4beda43ff2c055b6070258b8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222665"
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
|[reader_writer_lock::scoped_lock, classe](#scoped_lock_class)|Wrapper RAII sécurisé pour l’exception qui peut être utilisé pour acquérir des `reader_writer_lock` objets de verrou en tant qu’enregistreur.|
|[reader_writer_lock::scoped_lock_read, classe](#scoped_lock_read_class)|Wrapper RAII sécurisé pour les exceptions qui peut être utilisé pour acquérir des `reader_writer_lock` objets de verrou en tant que lecteur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[reader_writer_lock](#ctor)|Construit un nouvel objet `reader_writer_lock`.|
|[Destructeur ~ reader_writer_lock](#dtor)|Détruit l' `reader_writer_lock` objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Lock](#lock)|Acquiert le verrou lecteur-writer en tant que writer.|
|[lock_read](#lock_read)|Acquiert le verrou lecteur-writer en tant que lecteur. En présence d’enregistreurs, les lecteurs actifs doivent attendre la fin de leur exécution. Le lecteur enregistre simplement un intérêt dans le verrou et attend que les Writers le libèrent.|
|[try_lock](#try_lock)|Tente d’acquérir le verrou lecteur-writer en tant qu’enregistreur sans blocage.|
|[try_lock_read](#try_lock_read)|Tente d’acquérir le verrou lecteur-writer en tant que lecteur sans blocage.|
|[bloquer](#unlock)|Déverrouille le verrou lecteur-writer en fonction de la personne qui l’a verrouillé, lecteur ou enregistreur.|

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`reader_writer_lock`

## <a name="requirements"></a>Spécifications

**En-tête :** concrt. h

**Espace de noms :** concurrence

## <a name="lock"></a><a name="lock"></a>Lock

Acquiert le verrou lecteur-writer en tant que writer.

```cpp
void lock();
```

### <a name="remarks"></a>Notes

Il est souvent plus sûr d’utiliser la construction [scoped_lock](#scoped_lock_class) pour acquérir et libérer un `reader_writer_lock` objet en tant qu’enregistreur d’une manière sécurisée d’exception.

Une fois qu’un enregistreur a tenté d’acquérir le verrou, tous les futurs lecteurs se bloquent jusqu’à ce que les enregistreurs aient réussi à acquérir et à libérer le verrou. Ce verrou est biaisé vers les writers et peut priver les lecteurs d’un chargement continu d’enregistreurs.

Les writers sont chaînés afin qu’un enregistreur quittant le verrou libère le writer suivant en ligne.

Si le verrou est déjà détenu par le contexte d’appel, une exception [improper_lock](improper-lock-class.md) sera levée.

## <a name="lock_read"></a><a name="lock_read"></a>lock_read

Acquiert le verrou lecteur-writer en tant que lecteur. En présence d’enregistreurs, les lecteurs actifs doivent attendre la fin de leur exécution. Le lecteur enregistre simplement un intérêt dans le verrou et attend que les Writers le libèrent.

```cpp
void lock_read();
```

### <a name="remarks"></a>Notes

Il est souvent plus sûr d’utiliser la construction [scoped_lock_read](#scoped_lock_read_class) pour acquérir et libérer un `reader_writer_lock` objet en tant que lecteur de façon sécurisée.

Si des Writers attendent sur le verrou, le lecteur attend que tous les enregistreurs de la ligne aient acquis et libéré le verrou. Ce verrou est biaisé vers les writers et peut priver les lecteurs d’un chargement continu d’enregistreurs.

## <a name="reader_writer_lock"></a><a name="ctor"></a>reader_writer_lock

Construit un nouvel objet `reader_writer_lock`.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a>~ reader_writer_lock

Détruit l' `reader_writer_lock` objet.

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>Notes

Il est supposé que le verrou n’est plus maintenu lors de l’exécution du destructeur. Autoriser le verrou de l’enregistreur de lecteur à se détruire avec le verrou conservé entraîne un comportement indéfini.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a>reader_writer_lock :: scoped_lock, classe

Wrapper RAII sécurisé pour l’exception qui peut être utilisé pour acquérir des `reader_writer_lock` objets de verrou en tant qu’enregistreur.

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a>scoped_lock :: scoped_lock

Construit un `scoped_lock` objet et acquiert l' `reader_writer_lock` objet passé dans le `_Reader_writer_lock` paramètre en tant que writer. Si le verrou est détenu par un autre thread, cet appel est bloqué.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Paramètres

*_Reader_writer_lock*<br/>
`reader_writer_lock`Objet à acquérir en tant qu’enregistreur.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a>scoped_lock :: ~ scoped_lock

Détruit un `reader_writer_lock` objet et libère le verrou fourni dans son constructeur.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a>reader_writer_lock :: scoped_lock_read, classe

Wrapper RAII sécurisé pour les exceptions qui peut être utilisé pour acquérir des `reader_writer_lock` objets de verrou en tant que lecteur.

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a>scoped_lock_read :: scoped_lock_read

Construit un `scoped_lock_read` objet et acquiert l' `reader_writer_lock` objet passé dans le `_Reader_writer_lock` paramètre en tant que lecteur. Si le verrou est détenu par un autre thread en tant qu’enregistreur ou si des enregistreurs sont en attente, cet appel sera bloqué.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>Paramètres

*_Reader_writer_lock*<br/>
`reader_writer_lock`Objet à acquérir en tant que lecteur.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">reader_writer_lock :: scoped_lock_read :: ~ scoped_lock_read destructeur

Détruit un `scoped_lock_read` objet et libère le verrou fourni dans son constructeur.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Tente d’acquérir le verrou lecteur-writer en tant qu’enregistreur sans blocage.

### <a name="syntax"></a>Syntaxe

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, valeur **`true`** ; sinon, la valeur **`false`** .

## <a name="try_lock_read"></a><a name="try_lock_read"></a>try_lock_read

Tente d’acquérir le verrou lecteur-writer en tant que lecteur sans blocage.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>Valeur de retour

Si le verrou a été acquis, valeur **`true`** ; sinon, la valeur **`false`** .

## <a name="unlock"></a><a name="unlock"></a>bloquer

Déverrouille le verrou lecteur-writer en fonction de la personne qui l’a verrouillé, lecteur ou enregistreur.

```cpp
void unlock();
```

### <a name="remarks"></a>Notes

Si des Writers attendent sur le verrou, la libération du verrou passera toujours au writer suivant dans l’ordre FIFO. Ce verrou est biaisé vers les writers et peut priver les lecteurs d’un chargement continu d’enregistreurs.

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)<br/>
[Classe critical_section](critical-section-class.md)
