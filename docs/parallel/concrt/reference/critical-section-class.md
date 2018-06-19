---
title: critical_section, classe | Documents Microsoft
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
ms.openlocfilehash: d0287c74155e7b4fe827bb015b43cfca3384f3b1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693560"
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
|[try_lock_for](#try_lock_for)|Tente d’acquérir le verrou sans se bloquer pour un certain nombre de millisecondes.|  
|[unlock](#unlock)|Déverrouille la section critique.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [des Structures de données de synchronisation](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `critical_section`  
  
## <a name="requirements"></a>Spécifications  
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
 Il est probable que le verrou n’est plus maintenu lorsque le destructeur s’exécute. Autoriser la section critique détruire avec le verrou maintenu toujours résultats un comportement non défini.  
  
##  <a name="lock"></a> verrou 

 Acquiert cette section critique.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Notes  
 Il est souvent plus sécurisé d’utiliser la [scoped_lock](#critical_section__scoped_lock_class) construction pour acquérir et libérer un `critical_section` objet dans une exception sûre.  
  
 Si le verrou est déjà contenu par le contexte d’appel, un [improper_lock](improper-lock-class.md) exception sera levée.  
  
##  <a name="native_handle"></a> native_handle 

 Retourne un handle natif de plateforme spécifique, s’il en existe.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la section critique.  
  
### <a name="remarks"></a>Notes  
 A `critical_section` objet n’est pas associé à un handle natif de plateforme spécifique pour le système d’exploitation Windows. La méthode retourne simplement une référence à l’objet lui-même.  
  
##  <a name="critical_section__scoped_lock_class"></a>  critical_section::scoped_lock, classe  
 Un wrapper RAII sécurisé pour un `critical_section` objet.  
  
```
class scoped_lock;
```  
  
##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock 

 Construit un `scoped_lock` de l’objet et acquiert le `critical_section` objet passé dans le `_Critical_section` paramètre. Si la section critique est détenue par un autre thread, cet appel se bloquera.  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Critical_section`  
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

 Tente d’acquérir le verrou sans se bloquer pour un certain nombre de millisecondes.  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Timeout`  
 Le nombre de millisecondes à attendre avant l’expiration.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le verrou a été acquis, la valeur `true`; sinon, la valeur `false`.  
  
##  <a name="unlock"></a> déverrouiller 

 Déverrouille la section critique.  
  
```
void unlock();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [reader_writer_lock, classe](reader-writer-lock-class.md)
