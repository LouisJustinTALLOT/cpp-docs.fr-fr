---
title: lock_guard, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 047c7ab9db009bceafe47bb0ae53b876adad81b5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="lockguard-class"></a>lock_guard, classe
Représente un modèle qui peut être instancié pour créer un objet dont le destructeur déverrouille un `mutex`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Mutex>
class lock_guard;
```  
  
## <a name="remarks"></a>Notes  
 L’argument de modèle `Mutex` doit nommer un *type mutex*.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`lock_guard::mutex_type`|Synonyme de l’argument de modèle `Mutex`.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[lock_guard](#lock_guard)|Construit un objet `lock_guard`.|  
|[lock_guard::~lock_guard, destructeur](#dtorlock_guard_destructor)|Déverrouille le `mutex` passé au constructeur.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<mutex >  
  
 **Espace de noms :** std  
  
##  <a name="lock_guard"></a> lock_guard::lock_guard, constructeur  
 Construit un objet `lock_guard`.  
  
```cpp  
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```  
  
### <a name="parameters"></a>Paramètres  
 `Mtx`  
 Objet de *type mutex*.  
  
### <a name="remarks"></a>Remarques  
 Le premier constructeur construit un objet de type `lock_guard` et verrouille `Mtx`. Si `Mtx` n’est pas un mutex récursif, il doit être déverrouillé quand ce constructeur est appelé.  
  
 Le deuxième constructeur ne verrouille pas `Mtx`. `Mtx` doit être verrouillé quand ce constructeur est appelé. Le constructeur ne lève aucune exception.  
  
##  <a name="dtorlock_guard_destructor"></a> lock_guard::~lock_guard, destructeur  
 Déverrouille le `mutex` passé au constructeur.  
  
```
~lock_guard() noexcept;
```  
  
### <a name="remarks"></a>Remarques  
 Si le `mutex` n’existe pas quand le destructeur s’exécute, le comportement est indéfini.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




