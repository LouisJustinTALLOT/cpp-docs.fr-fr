---
title: accelerator_view, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa0e365ac531a5e1bb7b87a38fc86fb20032d20
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692715"
---
# <a name="acceleratorview-class"></a>accelerator_view, classe
Représente une abstraction d’appareil virtuel sur un accélérateur de données en parallèle de C++ AMP.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
class accelerator_view;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[accelerator_view, constructeur](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view`.|  
|[~ accelerator_view, destructeur](#dtor)|Détruit le `accelerator_view` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[create_marker](#create_marker)|Retourne une future pour effectuer le suivi de l’achèvement de toutes les commandes envoyées jusqu'à présent à ce `accelerator_view` objet.|  
|[flush](#flush)|Envoie toutes les commandes en attente en attente pour le `accelerator_view` objet pour l’accélérateur pour l’exécution.|  
|[get_accelerator](#get_accelerator)|Retourne l'objet `accelerator` de l'objet `accelerator_view`.|  
|[get_is_auto_selection](#get_is_auto_selection)|Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque le `accelerator_view` objet est passé à une [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[get_is_debug](#get_is_debug)|Retourne une valeur booléenne qui indique si le `accelerator_view` objet dispose de la couche de débogage activée pour le rapport d’erreurs étendues.|  
|[get_queuing_mode](#get_queuing_mode)|Retourne le mode de files d’attente pour le `accelerator_view` objet.|  
|[get_version](#get_version)|Retourne la version de la `accelerator_view`.|  
|[attente](#wait)|Attend que toutes les commandes envoyées à la `accelerator_view` objet se termine.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Compare cette `accelerator_view` objet avec un autre et retourne `false` s’ils sont identiques ; sinon, retourne `true`.|  
|[operator=](#operator_eq)|Copie le contenu de l’objet `accelerator_view` objet dans celui-ci.|  
|[operator==](#operator_eq_eq)|Compare cette `accelerator_view` objet avec un autre et retourne `true` s’ils sont identiques ; sinon, retourne `false`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[accélérateur](#accelerator)|Obtient l'objet `accelerator` pour l'objet `accelerator_view`.|  
|[is_auto_selection](#is_auto_selection)|Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque le `accelerator_view` objet est passé à une [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[is_debug](#is_debug)|Obtient une valeur booléenne qui indique si le `accelerator_view` objet dispose de la couche de débogage activée pour le rapport d’erreurs étendues.|  
|[queuing_mode](#queuing_mode)|Obtient le mode de files d’attente pour le `accelerator_view` objet.|  
|[version](#version)|Obtient la version de l’accélérateur.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `accelerator_view`  
  
### <a name="remarks"></a>Notes  
 Un `accelerator_view` objet représente une vue logique et isolée d’un accélérateur. Une unité de calcul physique unique peut avoir de nombreux logique et isolé `accelerator_view` objets. Chaque accélérateur a une valeur par défaut `accelerator_view` objet. Supplémentaires `accelerator_view` objets peuvent être créés.  
  
 Périphériques physiques peuvent être partagées entre plusieurs threads de client. Threads clients peuvent utiliser conjointement les mêmes `accelerator_view` objet d’un accélérateur, ou chaque client peut communiquer avec un périphérique de calcul via une indépendante `accelerator_view` objet pour l’isolation des autres threads de client.  
  
 Un `accelerator_view` objet peut avoir une des deux [énumération queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) États. Si le mode de file d’attente est `immediate`, comme les commandes `copy` et `parallel_for_each` sont envoyés à l’appareil d’accélérateur correspondant dès qu’elles sont retournées à l’appelant. Si le mode de file d’attente est `deferred`, ces commandes sont la file d’attente sur une file d’attente de la commande qui correspond à la `accelerator_view` objet. Commandes ne sont pas réellement envoyées à l’appareil jusqu'à ce que `flush()` est appelée.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amprt.h  
  
 **Espace de noms :** Concurrency  

## <a name="accelerator"></a> accélérateur 

Obtient l’objet de l’accélérateur pour l’objet accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="ctor"></a> accelerator_view 

Initialise une nouvelle instance de la classe accelerator_view en copiant une existante `accelerator_view` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à copier.  
  
## <a name="accelerator_view__create_marker"></a> create_marker 

Retourne une future pour effectuer le suivi de l’achèvement de toutes les commandes envoyées jusqu'à présent à ce `accelerator_view` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Ultérieures pour effectuer le suivi de l’achèvement de toutes les commandes envoyées jusqu'à présent à ce `accelerator_view` objet.  
  
## <a name="flush"></a> Vidage 

Envoie que toutes les commandes en attente en attente pour l’objet accelerator_view pour l’accélérateur pour l’exécution.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `void`.  

## <a name="accelerator_view__get_accelerator"></a> get_accelerator 

Retourne l’objet d’accélérateur pour l’objet accelerator_view.
### <a name="syntax"></a>Syntaxe
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>Valeur de retour
L’objet d’accélérateur pour l’objet accelerator_view.

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection 

Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à une [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le runtime sélectionne automatiquement un accélérateur approprié ; dans le cas contraire, `false`.  
  
## <a name="accelerator_view__get_is_debug"></a> get_is_debug 

Retourne une valeur booléenne qui indique si l’objet accelerator_view a la couche de débogage activée pour le rapport d’erreurs étendues.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui indique si le `accelerator_view` objet dispose de la couche de débogage activée pour le rapport d’erreurs étendues.  

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode 

Renvoie le mode de files d’attente pour l’objet accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le mode de files d’attente pour le `accelerator_view` objet.  
  
## <a name="accelerator_view__get_version"></a> get_version 

Retourne la version de l’accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La version de la `accelerator_view`.  
  
## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection 

Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à une [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="accelerator_view__is_debug"></a> is_debug 

Obtient une valeur booléenne qui indique si l’objet accelerator_view a la couche de débogage activée pour le rapport d’erreurs étendues.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="accelerator_view__operator_neq"></a> opérateur ! = 

Compare cet objet accelerator_view avec un autre et retourne `false` s’ils sont identiques ; sinon, retourne `true`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!= (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à comparer avec celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 `false` si les deux objets sont identiques ; sinon, `true`.  
  
## <a name="accelerator_view__operator_eq"></a> opérateur = 

Copie le contenu de l’objet accelerator_view spécifié dans celle-ci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
accelerator_view & operator= (    const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à copier à partir de.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la modification `accelerator_view` objet.  
  
## <a name="accelerator_view__operator_eq_eq"></a> opérateur == 

Compare cet objet accelerator_view avec un autre et retourne `true` s’ils sont identiques ; sinon, retourne `false`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator= = (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à comparer avec celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les deux objets sont identiques ; sinon, `false`.  
  
## <a name="accelerator_view__queuing_mode"></a> queuing_mode 

Obtient le mode de files d’attente pour l’objet accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="accelerator_view__version"></a> Version 

Obtient la version de l’accelerator_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="accelerator_view__wait"></a> attente 

Attend que toutes les commandes envoyées à l’objet accelerator_view se termine.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>Valeur de retour  
 Retourne `void`.  
  
#### <a name="remarks"></a>Notes  
 Si le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) est `immediate`, cette méthode est retournée immédiatement sans blocage.  
  
##  <a name="dtor"></a> ~ accelerator_view 

 Détruit l’objet accelerator_view.  
  
#### <a name="syntax"></a>Syntaxe  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
 
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
