---
title: critical_section, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbffd14bdde45c3d6124eb5f982b90c92f64f47c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136216"
---
# <a name="criticalsection-class"></a>critical_section, classe
Mutex non réentrant qui a explicitement connaissance du runtime d'accès concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```
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
|[critical_section::scoped_lock, classe](#critical_section__scoped_lock_class)|Un wrapper RAII sécurisé pour un `critical_section` objet.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[critical_section](#ctor)|Construit une nouvelle section critique.|  
|[~ critical_section, destructeur](#dtor)|Détruit une section critique.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[lock](#lock)|Acquiert cette section critique.|  
|[native_handle](#native_handle)|Retourne un handle natif de plateforme spécifique, s’il en existe.|  
|[try_lock](#try_lock)|Tente d’acquérir le verrou sans se bloquer.|  
|[try_lock_for](#try_lock_for)|Tente d’acquérir le verrou sans se bloquer pendant un nombre spécifique de millisecondes.|  
|[unlock](#unlock)|Déverrouille la section critique.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [les Structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `critical_section`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="ctor"></a> critical_section 

 Construit une nouvelle section critique.  
  
```
critical_section();
```  
  
##  <a name="dtor"></a> ~ critical_section 

 Détruit une section critique.  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>Notes  
 Il est probable que le verrou n’est plus conservé lorsque le destructeur s’exécute. Ce qui permet de la section critique détruire avec le verrou conservé résultats en un comportement non défini.  
  
##  <a name="lock"></a> Verrou 

 Acquiert cette section critique.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Notes  
 Il est souvent préférable d’utiliser le [scoped_lock](#critical_section__scoped_lock_class) construction pour acquérir et libérer un `critical_section` objet dans une exception sûre.  
  
 Si le verrou est déjà détenu par le contexte d’appel, un [improper_lock](improper-lock-class.md) exception sera levée.  
  
##  <a name="native_handle"></a> native_handle 

 Retourne un handle natif de plateforme spécifique, s’il en existe.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la section critique.  
  
### <a name="remarks"></a>Notes  
 Un `critical_section` objet n’est pas associé à un handle natif de plateforme spécifique pour le système d’exploitation Windows. La méthode retourne simplement une référence à l’objet lui-même.  
  
##  <a name="critical_section__scoped_lock_class"></a>  critical_section::scoped_lock, classe  
 Un wrapper RAII sécurisé pour un `critical_section` objet.  
  
```
class scoped_lock;
```  
  
##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock 

 Construit un `scoped_lock` de l’objet et acquiert le `critical_section` objet passé dans le `_Critical_section` paramètre. Si la section critique est maintenue par un autre thread, cet appel bloquera.  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>Paramètres  
*_Critical_section*<br/>
La section critique à verrouiller.  
  
##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock :: ~ scoped_lock 

 Détruit un `scoped_lock` de l’objet et libère la section critique fournie dans son constructeur.  
  
```
~scoped_lock();
```  
  
##  <a name="try_lock"></a> try_lock 

 Tente d’acquérir le verrou sans se bloquer.  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si le verrou a été acquis, la valeur `true`; sinon, la valeur `false`.  
  
##  <a name="try_lock_for"></a> try_lock_for 

 Tente d’acquérir le verrou sans se bloquer pendant un nombre spécifique de millisecondes.  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>Paramètres  
*_Délai*<br/>
Le nombre de millisecondes à attendre avant l’expiration.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le verrou a été acquis, la valeur `true`; sinon, la valeur `false`.  
  
##  <a name="unlock"></a> Déverrouiller 

 Déverrouille la section critique.  
  
```
void unlock();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [reader_writer_lock, classe](reader-writer-lock-class.md)
