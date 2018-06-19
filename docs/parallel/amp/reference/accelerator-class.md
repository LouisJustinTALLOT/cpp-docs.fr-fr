---
title: Accelerator, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40177af3796a17d32e78e628c41ea694f69ed9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694752"
---
# <a name="accelerator-class"></a>accelerator, classe
Un raccourci est une fonctionnalité de matériel qui est optimisée pour le calcul des données en parallèle. Un accélérateur peut être un périphérique connecté à un bus PCIe (par exemple, une carte GPU), ou il peut être une instruction étendue définie sur l’unité centrale principale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[accélérateur, constructeur](#ctor)|Initialise une nouvelle instance de la classe `accelerator`.|  
|[~ accelerator, destructeur](#ctor)|Détruit le `accelerator` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[create_view](#create_view)|Crée et retourne un `accelerator_view` objet sur cet accélérateur.|  
|[get_all](#get_all)|Retourne un vecteur de `accelerator` objets qui représentent tous les accélérateurs disponibles.|  
|[get_auto_selection_view](#get_auto_selection_view)|Retourne la sélection automatique `accelerator_view`.|  
|[get_dedicated_memory](#get_dedicated_memory)|Retourne la mémoire dédiée pour le `accelerator`, en kilo-octets.|  
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Retourne la valeur par défaut [access_type](concurrency-namespace-enums-amp.md#access_type) pour les mémoires tampons créées sur cet accélérateur.|  
|[get_default_view](#get_default_view)|Retourne la valeur par défaut `accelerator_view` objet auquel est associé le `accelerator`.|  
|[get_description](#get_description)|Retourne une brève description de la `accelerator` appareil.|  
|[get_device_path](#get_device_path)|Retourne le chemin d’accès de l’appareil.|  
|[get_has_display](#get_has_display)|Détermine si la `accelerator` est attaché à un affichage.|  
|[get_is_debug](#get_is_debug)|Détermine si le `accelerator` la couche de débogage activées pour le rapport d’erreurs étendues.|  
|[get_is_emulated](#get_is_emulated)|Détermine si la `accelerator` est émulée.|  
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Détermine si le `accelerator` prend en charge de la mémoire partagée|  
|[get_supports_double_precision](#get_supports_double_precision)|Détermine si la `accelerator` est attaché à un affichage.|  
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Détermine si le `accelerator` prend en charge pour les fonctions mathématiques de double précision limitée.|  
|[get_version](#get_version)|Retourne la version de la `accelerator`.|  
|[set_default](#set_default)|Retourne le chemin d’accès de l’accélérateur par défaut.|  
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Définit l’unité centrale par défaut [access_type](concurrency-namespace-enums-amp.md#access_type)pour les tableaux et les allocations de mémoire implicites effectuées sur ce `accelerator`.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Compare cette `accelerator` objet avec un autre et retourne `false` s’ils sont identiques ; sinon, retourne `true`.|  
|[operator=](#operator_eq)|Copie le contenu de l’objet `accelerator` objet à celui-ci.|  
|[operator==](#operator_eq_eq)|Compare cette `accelerator` objet avec un autre et retourne `true` s’ils sont identiques ; sinon, retourne `false`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[cpu_accelerator](#cpu_accelerator)|Obtient une chaîne constante pour le processeur `accelerator`.|  
|[dedicated_memory](#dedicated_memory)|Obtient la mémoire dédiée pour le `accelerator`, en kilo-octets.|  
|[default_accelerator](#default_accelerator)|Obtient une chaîne constante pour la valeur par défaut `accelerator`.|  
|[default_cpu_access_type](#default_cpu_access_type)|Obtient ou définit l’unité centrale par défaut [access_type](concurrency-namespace-enums-amp.md#access_type)pour les tableaux et les allocations de mémoire implicites effectuées sur ce `accelerator`.|  
|[default_view](#default_view)|Obtient la valeur par défaut `accelerator_view` objet auquel est associé le `accelerator`.|  
|[description](#description)|Obtient une brève description de la `accelerator` appareil.|  
|[device_path](#device_path)|Obtient le chemin d’accès de l’appareil.|  
|[direct3d_ref](#direct3d_ref)|Obtient une chaîne constante pour une référence de Direct3D `accelerator`.|  
|[direct3d_warp](#direct3d_warp)|Obtient la chaîne constante pour un `accelerator` de l’objet que vous pouvez utiliser pour l’exécution de code C++ AMP sur des processeurs multicœurs qui utilisent les Extensions Streaming SIMD (SSE).|  
|[has_display](#has_display)|Obtient une valeur booléenne qui indique si la `accelerator` est attaché à un affichage.|  
|[is_debug](#is_debug)|Indique si le `accelerator` la couche de débogage activées pour le rapport d’erreurs étendues.|  
|[is_emulated](#is_emulated)|Indique si la `accelerator` est émulée.|  
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Indique si le `accelerator` prend en charge de la mémoire partagée.|  
|[supports_double_precision](#supports_double_precision)|Indique si l’accélérateur prend en charge la double précision mathématiques.|  
|[supports_limited_double_precision](#supports_limited_double_precision)|Indique si l’accélérateur est limitée à la prise en charge pour les fonctions mathématiques de double précision.|  
|[version](#version)|Obtient la version de la `accelerator`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `accelerator`  
  
## <a name="remarks"></a>Notes  
 Un raccourci est une fonctionnalité de matériel qui est optimisée pour le calcul des données en parallèle. Un accélérateur est souvent un GPU discret, mais il peut également être une entité côté hôte virtuelle comme un périphérique DirectX REF, une chaîne (un périphérique de l’UC côté est accéléré au moyen d’instructions SSE), ou que le processeur lui-même.  
  
 Vous pouvez construire une `accelerator` objet par l’énumération des périphériques disponibles, ou par mise en route de l’appareil par défaut, l’appareil de référence ou le périphérique WARP.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amprt.h  
  
 **Espace de noms :** Concurrency  
  
##  <a name="dtor"></a> </a> ~ accelerator 

 Détruit le `accelerator` objet.  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="ctor"></a> accélérateur 

 Initialise une nouvelle instance de la [Accelerator (classe)](accelerator-class.md).  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Device_path`  
 Le chemin d’accès de l’unité physique.  
  
 `_Other`  
 L’accélérateur à copier.  
  
##  <a name="cpu_accelerator"></a> cpu_accelerator 

 Obtient une chaîne constante pour l’accélérateur de l’UC.  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="create_view"></a> CREATE_VIEW 

 Crée et retourne un `accelerator_view` objet sur cet accélérateur, à l’aide du mode de file d’attente spécifié. Lorsque le mode de file d’attente n’est pas spécifié, la nouvelle `accelerator_view` utilise le [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) mode files d’attente.  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>Paramètres  
 `qmode`  
 Le mode de files d’attente.  
  
### <a name="return-value"></a>Valeur de retour  
 Un nouveau `accelerator_view` objet sur cet accélérateur, à l’aide du mode de file d’attente spécifié.  
  
##  <a name="dedicated_memory"></a> dedicated_memory 

 Obtient la mémoire dédiée pour le `accelerator`, en kilo-octets.  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="default_accelerator"></a> default_accelerator 

 Obtient une chaîne constante pour la valeur par défaut `accelerator`.  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="default_cpu_access_type"></a> default_cpu_access_type 

 La valeur par défaut processeur [access_type](concurrency-namespace-enums-amp.md#access_type)pour les tableaux et les allocations de mémoire implicites effectuées sur cette ce `accelerator`.  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="default_view"></a> default_view 

 Obtient la vue d’accélérateur par défaut qui est associée à le `accelerator`.  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="description"></a> Description 

 Obtient une brève description de la `accelerator` appareil.  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="device_path"></a> chemin_unité 

 Obtient le chemin d’accès de l’accélérateur. Le chemin d’accès est unique sur le système.  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="direct3d_ref"></a> direct3d_ref 

 Obtient une chaîne constante pour un accélérateur de référence de Direct3D.  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="direct3d_warp"></a> direct3d_warp 

 Obtient la chaîne constante pour un `accelerator` de l’objet que vous pouvez utiliser pour l’exécution de votre code C++ AMP sur des processeurs multicœurs à l’aide des Extensions Streaming SIMD (SSE).  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="get_all"></a> get_all 

 Retourne un vecteur de `accelerator` objets qui représentent tous les accélérateurs disponibles.  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le vecteur d’accélérateurs disponibles  
  
##  <a name="get_auto_selection_view"></a> get_auto_selection_view 

 Retourne l’accelerator_view de sélection automatique, où spécifié en tant que les résultats de la cible parallel_for_each dans l’accelerator_view cible pour l’exécution du noyau parallel_for_each soit sélectionné automatiquement par le runtime. À d’autres fins, l’accelerator_view retourné par cette méthode est identique à la valeur par défaut accelerator_view de l’accélérateur par défaut  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’accelerator_view de sélection automatique.  
  
##  <a name="get_dedicated_memory"></a> get_dedicated_memory 

 Retourne la mémoire dédiée pour le `accelerator`, en kilo-octets.  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 La mémoire dédiée pour le `accelerator`, en kilo-octets.  
  
##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type 

 Obtient l’access_type du processeur par défaut pour les mémoires tampons créées sur cet accélérateur  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Access_type de l’UC par défaut pour les mémoires tampons créées sur cet accélérateur.  
  
##  <a name="get_default_view"></a> get_default_view 

 Retourne la valeur par défaut `accelerator_view` objet auquel est associé le `accelerator`.  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur par défaut `accelerator_view` objet auquel est associé le `accelerator`.  
  
##  <a name="get_description"></a> get_description 

 Retourne une brève description de la `accelerator` appareil.  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une brève description de la `accelerator` appareil.  
  
##  <a name="get_device_path"></a> get_device_path 

 Retourne le chemin d’accès de l’accélérateur. Le chemin d’accès est unique sur le système.  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le chemin de l’instance à l’échelle du système des périphériques uniques.  
  
##  <a name="get_has_display"></a> get_has_display 

 Retourne une valeur booléenne qui indique si le `accelerator` pouvez sur un écran de sortie.  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le `accelerator` pouvez de sortie pour un affichage ; sinon, `false`.  
  
##  <a name="get_is_debug"></a> get_is_debug 

 Détermine si le `accelerator` la couche de débogage activées pour le rapport d’erreurs étendues.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le `accelerator` la couche de débogage activées pour le rapport d’erreurs étendues. Sinon, `false`.  
  
##  <a name="get_is_emulated"></a> get_is_emulated 

 Détermine si la `accelerator` est émulée.  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si la `accelerator` est émulée. Sinon, `false`.  
  
##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory 

 Retourne une valeur booléenne indiquant si l’accélérateur prend en charge la mémoire accessible à la fois par l’UC et de l’accélérateur.  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’accélérateur prend en charge la mémoire de processeur partagé ; dans le cas contraire, `false`.  
  
##  <a name="get_supports_double_precision"></a> get_supports_double_precision 

 Retourne une valeur booléenne qui indique si l’accélérateur prend en charge la double mathématique de précision, y compris fused multiply ajouter (FMA), division, réciproque et effectuer un cast entre `int` et `double`.  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’accélérateur prend en charge la double mathématique de précision ; dans le cas contraire, `false`.  
  
##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision 

 Retourne une valeur booléenne qui indique si l’accélérateur est limitée à la prise en charge pour le calcul de la précision double. Si l’accélérateur est uniquement prise en charge limitée, puis fused multiply ajouter (FMA), division, réciproque et effectuer un cast entre `int` et `double` ne sont pas pris en charge.  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’accélérateur est limitée à la prise en charge pour le calcul de précision double ; dans le cas contraire, `false`.  
  
##  <a name="get_version"></a> get_version 

 Retourne la version de la `accelerator`.  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 La version de la `accelerator`.  
  
##  <a name="has_display"></a> has_display 

 Obtient une valeur booléenne qui indique si le `accelerator` pouvez sur un écran de sortie.  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="is_debug"></a> is_debug 

 Obtient une valeur booléenne qui indique si le `accelerator` la couche de débogage activées pour le rapport d’erreurs étendues.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="is_emulated"></a> is_emulated 

 Obtient une valeur booléenne qui indique si la `accelerator` est émulée.  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="operator_neq"></a> opérateur ! = 

 Compare cette `accelerator` objet avec un autre et retourne `false` s’ils sont identiques ; sinon, retourne `true`.  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator` objet à comparer avec celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 `false` Si les deux `accelerator` objets sont identiques ; sinon, `true`.  
  
##  <a name="operator_eq"></a> opérateur = 

 Copie le contenu de l’objet `accelerator` objet à celui-ci.  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator` objet à copier à partir de.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `accelerator` objet.  
  
##  <a name="operator_eq_eq"></a> opérateur == 

 Compare cette `accelerator` objet avec un autre et retourne `true` s’ils sont identiques ; sinon, retourne `false`.  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator` objet à comparer avec celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’autre `accelerator` objet est identique à ce `accelerator` de l’objet ; sinon, `false`.  
  
##  <a name="set_default"></a> set_default 

 Définit l’accélérateur par défaut à utiliser pour toute opération qui utilise implicitement l’accélérateur par défaut. Cette méthode ne réussit que si l’accélérateur sélectionné par défaut de runtime n’a pas déjà été utilisé dans une opération qui utilise implicitement l’accélérateur par défaut  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Path`  
 Le chemin d’accès pour l’accélérateur.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si l’appel aboutit à la définition de l’accélérateur par défaut. Sinon, `false`.  
  
##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type 

 Définir l’access_type du processeur par défaut pour les tableaux créé sur cet accélérateur ou des allocations de mémoire implicites comme partie d’array_views accessible sur ce cet accélérateur. Cette méthode ne réussit que si le default_cpu_access_type pour l’accélérateur n’a pas encore été remplacée par un appel précédent à cette méthode et la default_cpu_access_type runtime sélectionné pour cet accélérateur n’a pas encore été utilisé pour l’allocation d’un tableau ou pour une allocation de mémoire implicite une array_view d’accéder sur cet accélérateur de la sauvegarde.  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Default_cpu_access_type`  
 Access_type de l’UC par défaut à utiliser pour les allocations de mémoire tableau/array_view sur cet accélérateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur booléenne indiquant si l’access_type du processeur par défaut pour l’accélérateur a été correctement définie.  
  
##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory 

 Obtient une valeur booléenne indiquant si le `accelerator` prend en charge de la mémoire partagée.  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="supports_double_precision"></a> supports_double_precision 

 Obtient une valeur booléenne qui indique si l’accélérateur prend en charge les mathématiques double précision.  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision 

 Obtient une valeur booléenne qui indique si l’accélérateur est limitée à la prise en charge pour le calcul de la précision double. Si l’accélérateur est uniquement prise en charge limitée, puis fused multiply ajouter (FMA), division, réciproque et effectuer un cast entre `int` et `double` ne sont pas pris en charge.  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="version"></a> Version 

 Obtient la version de la `accelerator`.  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="dtor"></a> </a> ~ accelerator_view 

 Détruit le [accelerator_view](accelerator-view-class.md) objet.  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="accelerator"></a> accélérateur 

 Obtient le `accelerator` de l’objet pour le [accelerator_view](accelerator-view-class.md) objet.  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="ctor"></a> accelerator_view 

 Initialise une nouvelle instance de la [accelerator_view](accelerator-view-class.md) classe en copiant une existante `accelerator_view` objet.  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à copier.  
  
##  <a name="create_marker"></a> create_marker 

 Retourne une future pour effectuer le suivi de l’achèvement de toutes les commandes envoyées jusqu'à présent à ce `accelerator_view` objet.  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Ultérieures pour effectuer le suivi de l’achèvement de toutes les commandes envoyées jusqu'à présent à ce `accelerator_view` objet.  
  
##  <a name="flush"></a> Vidage 

 Envoie toutes les commandes en attente en attente pour le [accelerator_view](accelerator-view-class.md) objet pour l’accélérateur pour l’exécution.  
  
```  
void flush();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `void`.  
  
##  <a name="get_accelerator"></a> get_accelerator 

 Retourne le `accelerator` de l’objet pour le [accelerator_view](accelerator-view-class.md) objet.  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le `accelerator` de l’objet pour le `accelerator_view` objet.  
  
##  <a name="get_is_auto_selection"></a> get_is_auto_selection 

 Retourne une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à une [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le runtime sélectionne automatiquement un accélérateur approprié ; dans le cas contraire, `false`.  
  
##  <a name="get_is_debug"></a> get_is_debug 

 Retourne une valeur booléenne qui indique si le [accelerator_view](accelerator-view-class.md) objet dispose de la couche de débogage activée pour le rapport d’erreurs étendues.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui indique si le `accelerator_view` objet dispose de la couche de débogage activée pour le rapport d’erreurs étendues.  
  
##  <a name="get_queuing_mode"></a> get_queuing_mode 

 Retourne le mode de files d’attente pour le [accelerator_view](accelerator-view-class.md) objet.  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le mode de files d’attente pour le `accelerator_view` objet.  
  
##  <a name="get_version"></a> get_version 

 Retourne la version de la [accelerator_view](accelerator-view-class.md).  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
 La version de la `accelerator_view`.  
  
##  <a name="is_auto_selection"></a> is_auto_selection 

 Obtient une valeur booléenne qui indique si le runtime sélectionne automatiquement un accélérateur approprié lorsque l’accelerator_view est passé à une [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="is_debug"></a> is_debug 

 Obtient une valeur booléenne qui indique si le [accelerator_view](accelerator-view-class.md) objet dispose de la couche de débogage activée pour le rapport d’erreurs étendues.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="operator_neq"></a> opérateur ! = 

 Compare cette [accelerator_view](accelerator-view-class.md) objet avec un autre et retourne `false` s’ils sont identiques ; sinon, retourne `true`.  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à comparer avec celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 `false` si les deux objets sont identiques ; sinon, `true`.  
  
##  <a name="operator_eq"></a> opérateur = 

 Copie le contenu de l’objet [accelerator_view](accelerator-view-class.md) objet dans celui-ci.  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à copier à partir de.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la modification `accelerator_view` objet.  
  
##  <a name="operator_eq_eq"></a> opérateur == 

 Compare cette [accelerator_view](accelerator-view-class.md) objet avec un autre et retourne `true` s’ils sont identiques ; sinon, retourne `false`.  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `accelerator_view` objet à comparer avec celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les deux objets sont identiques ; sinon, `false`.  
  
##  <a name="queuing_mode"></a> queuing_mode 

 Obtient le mode de files d’attente pour le [accelerator_view](accelerator-view-class.md) objet.  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="version"></a> Version 

 Obtient la version de la [accelerator_view](accelerator-view-class.md).  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="wait"></a> attente 

 Attend que toutes les commandes envoyées à la [accelerator_view](accelerator-view-class.md) objet se termine.  
  
```  
void wait();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `void`.  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
