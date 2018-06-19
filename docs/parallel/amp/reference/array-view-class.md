---
title: array_view, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
dev_langs:
- C++
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e53b4927b102fc64a32f73ca5be78e71954b45f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694418"
---
# <a name="arrayview-class"></a>array_view, classe
Représente une vue à N dimensions sur les données contenues dans un autre conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <
    typename value_type,  
    int _Rank = 1  
>  
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
 
template <
    typename value_type,  
    int _Rank  
>  
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `value_type`  
 Le type de données des éléments dans le `array_view` objet.  
  
 `_Rank`  
 Le classement de la `array_view` objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[array_view, constructeur](#ctor)|Initialise une nouvelle instance de la classe `array_view`. Il n’existe aucun constructeur par défaut pour `array<T,N>`. Tous les constructeurs sont restreints à s’exécuter sur le processeur uniquement et ne peut pas être exécutées sur une cible de Direct3D.|  
|[~ array_view, destructeur](#ctor)|Détruit le `array_view` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[copy_to](#copy_to)|Copie le contenu de la `array_view` objet vers la destination spécifiée en appelant `copy(*this, dest)`.|  
|[data](#data)|Retourne un pointeur vers les données brutes de la `array_view`.|  
|[discard_data](#discard_data)|Ignore les données actuelles sous-jacente de cette vue.|  
|[get_extent](#get_extent)|Retourne l’objet de mesure de l’objet array_view.|  
|[get_ref](#get_ref)|Retourne une référence à l’élément indexé.|  
|[get_source_accelerator_view](#get_source_accelerator_view)|Retourne le [accelerator_view](accelerator-view-class.md) où la source de données de la `array_view` se trouve.|  
|[refresh](#refresh)|Notifie le `array_view` objet sa mémoire lié a été modifié en dehors de la `array_view` interface. Un appel à cette méthode restitue toutes les informations mises en cache obsolète.|  
|[reinterpret_as](#reinterpret_as)|Retourne un tableau unidimensionnel qui contienne tous les éléments dans le `array_view` objet.|  
|[section](#section)|Retourne une sous-section de le `array_view` objet qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.|  
|[synchronize](#synchronize)|Synchronise les modifications apportées à la `array_view` objet à sa source de données.|  
|[synchronize_async](#synchronize_async)|En mode asynchrone synchronise les modifications apportées à la `array_view` objet à sa source de données.|  
|[synchronize_to](#synchronize_to)|Synchronise les modifications apportées à la `array_view` objet spécifié [accelerator_view](accelerator-view-class.md).|  
|[synchronize_to_async](#synchronize_to_async)|En mode asynchrone synchronise les modifications apportées à la `array_view` objet spécifié [accelerator_view](accelerator-view-class.md).|  
|[view_as](#view_as)|Génère un `array_view` objet d’un rang différent à l’aide de ce `array_view` données de l’objet.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator()](#operator_call)|Retourne la valeur de l’élément spécifié par l’ou les paramètres.|  
|[operator[]](#operator_at)|Retourne l’élément qui est spécifié par les paramètres.|  
|[operator=](#operator_eq)|Copie le contenu de l’objet `array_view` objet dans celui-ci.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[RANK (constante)](#rank)|Stocke le rang de le `array_view` objet.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[extent](#extent)|Obtient l'objet `extent` qui définit la forme de l'objet `array_view`.|  
|[source_accelerator_view](#source_accelerator_view)|Obtient le [accelerator_view](accelerator-view-class.md) où la source de données de la `array_view` se trouve|  
|[value_type](#value_type)|Le type de valeur de la `array_view` et le tableau lié.|  
  
## <a name="remarks"></a>Notes  
 Le `array_view` classe représente une vue dans les données contenues dans un [tableau](array-class.md) objet ou une sous-section d’une `array` objet.  
  
 Vous pouvez accéder à le `array_view` où la source de données se trouve (localement) ou sur un accélérateur différent ou un domaine de la cohérence de l’objet (à distance). Lorsque vous accédez à l’objet à distance, les vues sont copiés et mis en cache si nécessaire. Sauf pour les effets de la mise en cache automatique `array_view` objets dispose d’un profil de performances similaire à celle de `array` objets. Il existe une baisse des performances lorsque vous accédez aux données via des vues.  
  
 Il existe trois scénarios d’utilisation à distance :  
  
-   Une vue vers un pointeur de mémoire système est passée au moyen d’un [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each) appel à un accélérateur et accessibles sur l’accélérateur.  
  
-   Une vue dans un tableau situé sur un accélérateur est passée au moyen d’un `parallel_for_each` de l’appel à un autre accélérateur et est accessible en il.  
  
-   Une vue dans un tableau situé sur un accélérateur est accessible sur l’UC.  
  
 Dans l’un de ces scénarios, les vues référencées sont copiées par le runtime à l’emplacement distant et, si modifié par les appels à la `array_view` de l’objet, sont copiés vers l’emplacement local. Le runtime peut optimiser le processus de copie des modifications, peut copier uniquement les éléments modifiés ou peut également copier des parties sans modification. Chevauchement `array_view` objets sur une source de données ne sont pas garanti que pour maintenir l’intégrité référentielle dans un emplacement distant.  
  
 Vous devez synchroniser l’accès multithread à la même source de données.  
  
 Le runtime apporte les garanties suivantes concernant la mise en cache des données dans `array_view` objets :  
  
-   Tous les accès correctement synchronisés à une `array` objet et un `array_view` un objet dans l’ordre de programme obéissent aux règles de série se produit-avant de relation.  
  
-   Tous les accès correctement synchronisés chevauchant `array_view` des objets sur le même accélérateur sur un seul `array` objet sont des alias via le `array` objet. Ils induire un total se produit-avant une relation qui obéit à la commande de programme. Il n’existe aucune mise en cache. Si le `array_view` objets sont exécutent sur différents accélérateurs, l’ordre d’accès n’est pas défini, la création d’une condition de concurrence.  
  
 Lorsque vous créez un `array_view` de l’objet à l’aide d’un pointeur dans la mémoire système, vous devez modifier la vue `array_view` uniquement par l’intermédiaire de l’objet le `array_view` pointeur. Ou bien, vous devez appeler `refresh()` sur l’un de la `array_view` les objets qui sont attachés au pointeur système, si la mémoire native sous-jacente est modifiée directement, plutôt que via le `array_view` objet.  
  
 Des actions notifie le `array_view` de l’objet que la mémoire native sous-jacente est modifiée et que toutes les copies qui sont trouvent sur un accélérateur sont obsolètes. Si vous suivez ces instructions, les vues de pointeur sont identiques à ceux fournis pour les affichages de tableaux de données en parallèle.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp.h  
  
 **Espace de noms :** Concurrency  
  
##  <a name="dtor"></a> ~ array_view 

 Détruit le `array_view` objet.  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="ctor"></a> array_view 

 Initialise une nouvelle instance de la classe `array_view`.  
  
```  
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view& _Other)restrict(amp,cpu);

 
explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    _Container& _Src) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _Container& _Src);

 
explicit array_view(
    int _E0,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const _Container& _Src) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    const _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const _Container& _Src);

 
array_view(
    int _E0,  
    const value_type* _Src)restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    const value_type* _Src) restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const value_type* _Src) restrict(amp,cpu);

 
```  
  
### <a name="parameters"></a>Paramètres  
 `_Arr_type`  
 Le type d’élément d’un tableau de style C à partir de laquelle les données sont fournies.  
  
 `_Container`  
 Un argument de modèle qui doit spécifier un conteneur linéaire qui prend en charge `data()` et `size()` membres.  
  
 `_E0`  
 Le composant plus significatif de l’étendue de cette section.  
  
 `_E1`  
 Le composant suivant-à-plus significatif de l’étendue de cette section.  
  
 `_E2`  
 Le composant de poids faible de l’étendue de cette section.  
  
 `_Extent`  
 L’étendue de chaque dimension de ce `array_view`.  
  
 `_Other`  
 Un objet de type `array_view<T,N>` à partir de laquelle initialiser la nouvelle `array_view`.  
  
 `_Size`  
 La taille d’un tableau de style C à partir de laquelle les données sont fournies.  
  
 `_Src`  
 Pointeur vers les données source qui seront copiés dans le nouveau tableau.  
  
##  <a name="copy_to"></a> copy_to 

 Copie le contenu de la `array_view` objet à l’objet de destination spécifié en appelant `copy(*this, dest)`.  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>Paramètres  
 `_Dest`  
 L’objet de destination.  
  
##  <a name="data"></a> Données 

 Retourne un pointeur vers les données brutes de la `array_view`.  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers les données brutes de la `array_view`.  
  
##  <a name="discard_data"></a> discard_data 

 Ignore les données actuelles sous-jacente de cette vue. Il s’agit d’un indicateur d’optimisation de runtime utilisée pour éviter de copier le contenu actuel de la vue à une cible `accelerator_view` qu’il est accessible sur, et son utilisation est recommandée si le contenu existant n’est pas nécessaire. Cette méthode est une opération inefficace lorsqu’il est utilisé dans un contexte Restrict (amp)  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="extent"></a> étendue 

 Obtient l'objet `extent` qui définit la forme de l'objet `array_view`.  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_extent"></a> get_extent 

 Retourne le [étendue](extent-class.md) objet de la `array_view` objet.  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le `extent` objet de la `array_view` objet  
  
##  <a name="get_ref"></a> get_ref 

 Obtenir une référence à l’élément indexé par _Index. Contrairement à d’autres opérateurs d’indexation pour accéder à l’array_view sur l’UC, cette méthode ne synchronise pas implicitement le contenu de cette array_view pour l’UC. Après l’accès à l’array_view sur un emplacement distant ou en effectuant une opération de copie impliquant ce array_view les utilisateurs sont responsables de la synchronisation explicite de l’array_view à l’UC avant d’appeler cette méthode. Cela entraîne un comportement non défini.  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 Index.  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à l’élément indexé par _Index  
  
##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view 

 Retourne l’accelerator_view où se trouve la source de données de l’array_view. Si l’array_view n’a pas d’une source de données, cette API lève une runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_call"></a> operator() 

 Retourne la valeur de l’élément spécifié par l’ou les paramètres.  
  
```  
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 L’emplacement de l’élément.  
  
 `_I0`  
 L’index de la première dimension.  
  
 `_I1`  
 Index dans la deuxième dimension.  
  
 `_I2`  
 Index dans la troisième dimension.  
  
 `_I`  
 L’emplacement de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de l’élément spécifié par l’ou les paramètres.  
  
##  <a name="operator_at"></a> operator] 

 Retourne l’élément qui est spécifié par les paramètres.  
  
```  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

 
value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Index`  
 Index.  
  
 `_I`  
 Index.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de l’élément à l’index, ou un `array_view` projetée sur la dimension plus significatif.  
  
##  <a name="operator_eq"></a> opérateur = 

 Copie le contenu de l’objet `array_view` objet à celui-ci.  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Other`  
 Le `array_view` objet à copier à partir de.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à ce `array_view` objet.  
  
##  <a name="rank"></a> Rang 

 Stocke le rang de le `array_view` objet.  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="refresh"></a> Actualisation 

 Notifie le `array_view` objet sa mémoire lié a été modifié en dehors de la `array_view` interface. Un appel à cette méthode restitue toutes les informations mises en cache obsolète.  
  
```  
void refresh() const restrict(cpu);
```  
## <a name="reinterpret_as"></a> reinterpret_as 

Réinterprète les array_view via un array_view unidimensionnel, qui, en tant qu’option peut avoir un type valeur autre que la source array_view.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
template <  
    typename _Value_type2  
>  
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
  
template <  
    typename _Value_type2  
>  
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Value_type2`  
 Le type de données de la nouvelle `array_view` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `array_view` objet ou une variable const `array_view` objet qui est basé sur ce `array_view`, avec le type d’élément converti à partir de `T` à `_Value_type2`, et le rang est réduite de *N* à 1.  
  
### <a name="remarks"></a>Notes  
 Il est parfois commode afficher un tableau multidimensionnel sous la forme d’un tableau unidimensionnel linéaire, qui peut avoir un type de valeur différente que le tableau source. Vous pouvez y parvenir sur un `array_view` à l’aide de cette méthode.  
  
**Avertissement** Reinterpeting un objet array_view à l’aide d’un type valeur différent est une opération potentiellement dangereuse. Cette fonctionnalité doit être utilisée avec précaution.  
  
 Voici un exemple :  
  
```cpp  
struct RGB { float r; float g; float b; };  
  
array<RGB,3>  a = ...;   
array_view<float,1> v = a.reinterpret_as<float>();   
  
assert(v.extent == 3*a.extent);  
```  
    
##  <a name="section"></a> Section 

 Retourne une sous-section de le `array_view` objet qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée.  
  
```  
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _E0) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_E0`  
 Le composant plus significatif de l’étendue de cette section.  
  
 `_E1`  
 Le composant suivant-à-plus significatif de l’étendue de cette section.  
  
 `_E2`  
 Le composant de poids faible de l’étendue de cette section.  
  
 `_Ext`  
 Le [étendue](extent-class.md) objet qui spécifie l’étendue de la section. L’origine est 0.  
  
 `_Idx`  
 Le [index](index-class.md) objet qui spécifie l’emplacement d’origine. La sous-section est le reste de l’étendue.  
  
 `_I0`  
 Le composant plus significatif de l’origine de cette section.  
  
 `_I1`  
 Le composant suivant-à-plus significatif de l’origine de cette section.  
  
 `_I2`  
 Le composant moins significatif de l’origine de cette section.  
  
 `_Rank`  
 Le rang de la section.  
  
 `_Section_extent`  
 Le [étendue](extent-class.md) objet qui spécifie l’étendue de la section.  
  
 `_Section_origin`  
 Le [index](index-class.md) objet qui spécifie l’emplacement d’origine.  
  
### <a name="return-value"></a>Valeur de retour  
 Une sous-section de le `array_view` objet qui est à l’origine spécifiée et, éventuellement, qui a l’étendue spécifiée. Lorsque seul le `index` objet est spécifié, la sous-section contienne tous les éléments dans l’étendue associée qui ont des index supérieurs à l’index des éléments dans le `index` objet.  
  
##  <a name="source_accelerator_view"></a> source_accelerator_view 

 Obtient l’accelerator_view source qui est associé à cette array_view.  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="synchronize"></a> Synchroniser 

 Synchronise les modifications apportées à la `array_view` objet à sa source de données.  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Access_type`  
 La destination [access_type](concurrency-namespace-enums-amp.md#access_type) sur la cible [accelerator_view](accelerator-view-class.md). Ce paramètre a la valeur par défaut `access_type_read`.  
  
##  <a name="synchronize_async"></a> synchronize_async 

 En mode asynchrone synchronise les modifications apportées à la `array_view` objet à sa source de données.  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Access_type`  
 La destination [access_type](concurrency-namespace-enums-amp.md#access_type) sur la cible [accelerator_view](accelerator-view-class.md). Ce paramètre a la valeur par défaut `access_type_read`.  
  
### <a name="return-value"></a>Valeur de retour  
 Ultérieures sur lequel vous souhaitez attendre que l’opération se termine.  
  
##  <a name="synchronize_to"></a> synchronize_to 

 Synchronise les modifications apportées à cette array_view pour l’accelerator_view spécifié.  
  
```  
void synchronize_to(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Accl_view`  
 Accelerator_view de cible à synchroniser avec.  
  
 `_Access_type`  
 Access_type de votre choix sur la cible accelerator_view. Ce paramètre a la valeur par défaut access_type_read.  
  
##  <a name="synchronize_to_async"></a> synchronize_to_async 

 En mode asynchrone synchronise les modifications apportées à cette array_view pour l’accelerator_view spécifié.  
  
```  
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Accl_view`  
 Accelerator_view de cible à synchroniser avec.  
  
 `_Access_type`  
 Access_type de votre choix sur la cible accelerator_view. Ce paramètre a la valeur par défaut access_type_read.  
  
### <a name="return-value"></a>Valeur de retour  
 Ultérieures sur lequel vous souhaitez attendre que l’opération se termine.  
  
##  <a name="value_type"></a> Value_type 

 Le type de valeur de l’array_view et le tableau lié.  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="view_as"></a> view_as 

 Cela réinterprète `array_view` comme un `array_view` d’un classement différent.  
  
```  
template <
    int _New_rank  
>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

 
template <
    int _New_rank  
>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_New_rank`  
 Le rang du nouveau `array_view` objet.  
  
 `_View_extent`  
 La modification `extent`.  
  
 `value_type`  
 Le type de données des éléments dans les deux d’origine [tableau](array-class.md) objet et retourné `array_view` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Le `array_view` objet construit.  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
