---
title: collection_adapter (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter
dev_langs:
- C++
helpviewer_keywords:
- collection_adapter class [STL/CLR]
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 62fb5dc48175d755771960e9121c3371a0292595
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33114443"
---
# <a name="collectionadapter-stlclr"></a>collection_adapter (STL/CLR)
Encapsule une collection de .NET à utiliser comme un conteneur STL/CLR. A `collection_adapter` est une classe de modèle qui décrit un objet de conteneur STL/CLR simple. Il inclut une interface de bibliothèque de classes de Base (BCL) et retourne une paire itérateur qui vous permet de manipuler la séquence contrôlée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 Coll  
 Le type de la collection encapsulée.  
  
## <a name="specializations"></a>Spécialisations  
  
|Spécialisation|Description|  
|--------------------|-----------------|  
|IEnumerable|Séquences dans les éléments.|  
|ICollection|Gère un groupe d’éléments.|  
|IList|Gère un groupe ordonné d’éléments.|  
|IDictionary|Conserver un jeu de {clé, valeur} paires.|  
|IEnumerable\<valeur >|Séquences via les éléments typés.|  
|ICollection\<valeur >|Gère un groupe d’éléments typés.|  
|IList\<valeur >|Gère un groupe ordonné d’éléments typés.|  
|IDictionary\<valeur >|Gère un ensemble de typé {clé, valeur} paires.|  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](../dotnet/collection-adapter-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[collection_adapter::iterator (STL/CLR)](../dotnet/collection-adapter-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[collection_adapter::key_type (STL/CLR)](../dotnet/collection-adapter-key-type-stl-clr.md)|Le type d’une clé de dictionnaire.|  
|[collection_adapter::mapped_type (STL/CLR)](../dotnet/collection-adapter-mapped-type-stl-clr.md)|Le type d’une valeur de dictionnaire.|  
|[collection_adapter::reference (STL/CLR)](../dotnet/collection-adapter-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[collection_adapter::size_type (STL/CLR)](../dotnet/collection-adapter-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[collection_adapter::value_type (STL/CLR)](../dotnet/collection-adapter-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)|Désigne l’interface BCL encapsulée.|  
|[collection_adapter::begin (STL/CLR)](../dotnet/collection-adapter-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[collection_adapter::collection_adapter (STL/CLR)](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|Construit un objet d’adaptateur.|  
|[collection_adapter::end (STL/CLR)](../dotnet/collection-adapter-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[collection_adapter::size (STL/CLR)](../dotnet/collection-adapter-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[collection_adapter::swap (STL/CLR)](../dotnet/collection-adapter-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)|Remplace le handle BCL stocké.|  
  
## <a name="remarks"></a>Notes  
 Cette classe de modèle vous permet de manipuler un conteneur BCL comme un conteneur STL/CLR. La `collection_adapter` stocke un handle vers une interface BCL, qui à son tour contrôle une séquence d’éléments. A `collection_adapter` objet `X` retourne une paire d’itérateurs d’entrée `X.begin()` et `X.end()` que vous utilisez pour consulter des éléments dans l’ordre. Parmi les spécialisations vous permettent également d’écrire `X.size()` pour déterminer la longueur de la séquence contrôlée.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/carte >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)