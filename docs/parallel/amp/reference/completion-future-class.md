---
title: completion_future, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b6aa7e9c160a7bedc6eed58a63c07ae7bb65913
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689036"
---
# <a name="completionfuture-class"></a>completion_future, classe
Représente une future qui correspond à une opération asynchrone de C++ AMP.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
class completion_future;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[completion_future, constructeur](#ctor)|Initialise une nouvelle instance de la classe `completion_future`.|  
|[~ completion_future, destructeur](#dtor)|Détruit le `completion_future` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[get](#get)|Attend que l’opération asynchrone terminée.|  
|[puis](#then)|Remonte d’un objet de fonction de rappel pour le `completion_future` objet à exécuter lorsque l’opération asynchrone associée termine son exécution.|  
|[to_task](#to_task)|Retourne un `task` objet correspondant à l’opération asynchrone associée.|  
|[valid](#valid)|Obtient une valeur booléenne qui indique si l’objet est associé à une opération asynchrone.|  
|[attente](#wait)|Bloque jusqu'à ce que l’opération asynchrone terminée.|  
|[wait_for](#wait_for)|Bloque jusqu'à ce que l’opération asynchrone terminée ou que la durée spécifiée par `_Rel_time` s’est écoulé.|  
|[wait_until](#wait_until)|Bloque jusqu'à ce que l’opération asynchrone terminée ou jusqu'à ce que l’heure actuelle dépasse la valeur spécifiée par `_Abs_time`.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[opérateur std::shared_future\<void >](#operator_shared_future)|Convertit implicitement la `completion_future` de l’objet à un `std::shared_future` objet.|  
|[operator=](#operator_eq)|Copie le contenu de l’objet `completion_future` objet dans celui-ci.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `completion_future`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amprt.h  
  
 **Espace de noms :** concurrency  


## <a name="ctor"></a> completion_future 

Initialise une nouvelle instance de la classe `completion_future`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
completion_future();  
  
completion_future(  
    const completion_future& _Other );  
  
completion_future(  
    completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `completion_future` objet à copier ou déplacer.  
  
### <a name="overloads-list"></a>Liste de surcharge  
  
|Name|Description|  
|----------|-----------------|  
|`completion_future();`|Initialise une nouvelle instance de la `completion_future` classe|  
|`completion_future(const completion_future& _Other);`|Initialise une nouvelle instance de la `completion_future` classe par un constructeur de copie.|  
|`completion_future(completion_future&& _Other);`|Initialise une nouvelle instance de la `completion_future` classe en déplaçant un constructeur.|  
  
## <a name="get"></a> Télécharger 

Attend que l’opération asynchrone terminée. Lève l’exception stockée si une s’est produite lors de l’opération asynchrone.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void get() const;  
```  
  
## <a name="operator_shared_future"></a> opérateur std::shared_future<void> 

Convertit implicitement la `completion_future` de l’objet à un `std::shared_future` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
operator std::shared_future<void>() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Objet `std::shared_future`.  
  
## <a name="operator_eq"></a> opérateur = 

Copie le contenu de l’objet `completion_future` objet dans celui-ci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
completion_future&  operator= (const completion_future& _Other );    
completion_future&  operator= (completion_future&& _Other );  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 L’objet d’origine.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `completion_future` objet.  
  
## <a name="overloads-list"></a>Liste de surcharge  
  
|Name|Description|  
|----------|-----------------|  
|`completion_future& operator=(const completion_future& _Other);`|Copie le contenu de l’objet `completion_future` objet dans celui-ci, à l’aide d’une copie complète.|  
|`completion_future& operator=(completion_future&& _Other);`|Copie le contenu de l’objet `completion_future` objet dans celui-ci, à l’aide d’une assignation de déplacement.|  
  
## <a name="then"></a> puis 

Remonte d’un objet de fonction de rappel pour le `completion_future` objet à exécuter lorsque l’opération asynchrone associée termine son exécution.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <typename _Functor>  
void then(const _Functor & _Func ) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Functor`  
 La fonction de rappel.  
  
 `_Func`  
 L’objet de fonction de rappel.  
  
## <a name="to_task"></a> to_task 

Retourne un `task` objet correspondant à l’opération asynchrone associée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
concurrency::task<void> to_task() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `task` objet correspondant à l’opération asynchrone associée.  
  
## <a name="valid"></a> valide 

Obtient une valeur booléenne qui indique si l’objet est associé à une opération asynchrone.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool valid() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’objet est associé à une opération asynchrone ; dans le cas contraire, `false`.  
  
## <a name="wait"></a> attente 

Bloque jusqu'à ce que l’opération asynchrone terminée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void wait() const;  
```  
  
## <a name="wait_for"></a> wait_for 

Bloque jusqu'à ce que l’opération asynchrone terminée ou que la durée spécifiée par `_Rel_time` s’est écoulé.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <  
    class _Rep,  
    class _Period  
>  
std::future_status::future_status wait_for(  
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rep`  
 Un type arithmétique qui représente le nombre de graduations.  
  
 `_Period`  
 Std::ratio qui représente le nombre de secondes qui s’écoulent par cycle.  
  
 `_Rel_time`  
 La quantité maximale de délai d’attente pour l’opération se termine.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne :  
  
-   `std::future_status::deferred` Si l’opération asynchrone associée n’est pas en cours d’exécution.  
  
-   `std::future_status::ready` Si l’opération asynchrone associée est terminée.  
  
-   `std::future_status::timeout` Si le laps de temps spécifié a expiré.  
  
## <a name="wait_until"></a> wait_until 

Bloque jusqu'à ce que l’opération asynchrone terminée ou jusqu'à ce que l’heure actuelle dépasse la valeur spécifiée par `_Abs_time`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <  
    class _Clock,  
    class _Duration  
>  
std::future_status::future_status wait_until(  
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Clock`  
 L’horloge sur lesquels ce point de temps est mesuré.  
  
 `_Duration`  
 Depuis le début de l’intervalle de temps `_Clock`d’époque, après lequel la fonction va expirer.  
  
 `_Abs_time`  
 Le point dans le temps après lequel la fonction expire.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne :  
  
1.  `std::future_status::deferred` Si l’opération asynchrone associée n’est pas en cours d’exécution.  
  
2.  `std::future_status::ready` Si l’opération asynchrone associée est terminée.  
  
3.  `std::future_status::timeout` Si la période de temps spécifié a expiré.  
  
## <a name="dtor"></a> ~completion_future 

Détruit le `completion_future` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
~completion_future();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
