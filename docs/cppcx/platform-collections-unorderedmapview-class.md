---
title: 'Classe Platform::Collections :: unorderedmapview | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2251703307c5f6ed5787227a4def42dfbcd3fc18
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684007"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView, classe
Représente une vue en lecture seule dans une *carte*, qui est une collection de paires clé/valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = ::std::equal_to<K>>  
ref class UnorderedMapView sealed;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `K`  
 Type de la clé dans la paire clé-valeur.  
  
 `V`  
 Type de la valeur dans la paire clé-valeur.  
  
 `C`  
 Type qui fournit un objet de fonction qui peut comparer l'égalité de deux valeurs de clés. Par défaut, [std::equal_to\<K >](../standard-library/equal-to-struct.md)  
  
### <a name="remarks"></a>Notes  
 UnorderedMapView est une implémentation C++ concrète de la [Windows::Foundation::Collections::IMapView\<K, V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interface est passée à travers l’interface binaire d’application (ABI). Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[UnorderedMapView::UnorderedMapView](#ctor)|Initialise une nouvelle instance de la classe UnorderedMapView.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[UnorderedMapView::First](#first)|Retourne un itérateur qui est initialisé au premier élément de la vue cartographique.|  
|[UnorderedMapView::HasKey](#haskey)|Détermine si le UnorderedMapView actuel contient la clé spécifiée.|  
|[UnorderedMapView::Lookup](#lookup)|Récupère l'élément à la clé spécifiée dans l'objet UnorderedMapView actuel.|  
|[UnorderedMapView::Size](#size)|Retourne le nombre d'éléments de l'objet UnorderedMapView actuel.|  
|[UnorderedMapView::Split](#split)|Fractionne un objet UnorderedMapView d'origine en deux objets UnorderedMapView.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `UnorderedMapView`  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** collection.h  
  
 **Espace de noms :** Platform::Collections  

## <a name="first"></a>  UnorderedMapView::First, méthode
Retourne un itérateur qui spécifie le premier [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) élément dans la carte non triée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp   
virtual Windows::Foundation::Collections::IIterator<  
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^   
    First();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur qui spécifie le premier élément de la vue cartographique.  
  
### <a name="remarks"></a>Notes  
 Un moyen pratique de contenir l’itérateur retourné par First() consiste à attribuer la valeur de retour à une variable est déclarée avec le **automatique** mot clé de déduction de type. Par exemple, `auto x = myMapView->First();`.  
  


## <a name="haskey"></a>  UnorderedMapView::HasKey, méthode
Détermine si le UnorderedMap actif contient la clé spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Clé utilisée pour rechercher l'élément. Le type de `key` est typename *K*.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si la clé est trouvée ; sinon, `false`.  
  


## <a name="lookup"></a>  UnorderedMapView::Lookup, méthode
Récupère la valeur du type V associé à la clé spécifiée de type K.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Clé utilisée pour rechercher un élément dans le UnorderedMapView. Le type de `key` est typename *K*.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur associée à `key`. Le type de la valeur de retour est typename *V*.  
  


## <a name="size"></a>  UnorderedMapView::Size, méthode
Retourne le nombre de [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) éléments de l’objet UnorderedMapView.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d'éléments contenus dans l'objet UnorderedMapView actif.  
  


## <a name="split"></a>  UnorderedMapView::Split, méthode
Divise l'objet UnorderedMapView actif en deux objets UnorderedMapView. Cette méthode n'est pas opérationnelle.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K,V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K,V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>Paramètres  
 `firstPartition`  
 Première partie de l'objet UnorderedMapView d'origine.  
  
 `secondPartition`  
 Deuxième partie de l'objet UnorderedMapView d'origine.  
  
### <a name="remarks"></a>Notes  
 Cette méthode n'est pas opérationnelle. Elle ne fait rien.  
  


## <a name="ctor"></a>  UnorderedMapView::UnorderedMapView, constructeur
Initialise une nouvelle instance de la classe UnorderedMapView.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
UnorderedMapView();    
explicit UnorderedMapView(size_t n);   
UnorderedMapView(size_t n, const H& h);   
UnorderedMapView(size_t n, const H& h, const P& p);  
  
explicit UnorderedMapView(  
    const std::unordered_map<K, V, H, P>& m);  
explicit UnorderedMapView(  
    std::unordered_map<K, V, H, P>&& m);  
  
template <typename InIt> UnorderedMapView(InIt first, InIt last );  
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h,  
    const P& p );  
  
UnorderedMapView(std::initializer_list<std::pair<const K, V>);  
  
UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n   
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h);  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h,  
    const P& p );  
```  
  
### <a name="parameters"></a>Paramètres  
 n  
 Nombre d'éléments pour lesquels préallouer de l'espace.  
  
 `InIt`  
 Nom de type du UnorderedMapView.  
  
 `H`  
 Objet de fonction qui peut avoir une valeur de hachage pour une clé. Valeur par défaut est [std::hash\<K >](../standard-library/hash-class.md) pour les types qui `std::hash` prend en charge.  
  
 `P`  
 Type qui fournit un objet de fonction qui peut comparer deux clés pour déterminer leur égalité. Valeur par défaut est [std::equal_to\<K >](../standard-library/equal-to-struct.md).  
  
 `m`  
 Une référence ou [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) à un [std::unordered_map](../standard-library/unordered-map-class.md) qui est utilisé pour initialiser le UnorderedMapView.  
  
 `first`  
 Itérateur d'entrée du premier élément d'une plage d'éléments utilisée pour initialiser le UnorderedMapView.  
  
 `last`  
 Itérateur d'entrée du premier élément qui suit une plage d'éléments utilisée pour initialiser le UnorderedMapView.  
   
## <a name="see-also"></a>Voir aussi  
 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)