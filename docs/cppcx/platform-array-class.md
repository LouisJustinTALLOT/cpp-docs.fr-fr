---
title: Platform::Array (classe) | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65c45265714f869de10bdfd450c2b1349d6b526b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704670"
---
# <a name="platformarray-class"></a>Platform::Array (classe)
Représente un tableau unidimensionnel et modifiable qui peut être reçu et passé via l'interface binaire d'application (ABI).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp    
template <typename T>  
private ref class Array<TArg, 1> :   
    public WriteOnlyArray<TArg, 1>,  
    public IBoxArray<TArg>   
```  
  
### <a name="members"></a>Membres  
 Platform::Array hérite de toutes ses méthodes de [Platform::WriteOnlyArray (classe)](../cppcx/platform-writeonlyarray-class.md) et implémente la `Value` propriété de la [Platform::iboxarray, Interface](../cppcx/platform-iboxarray-interface.md).  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Constructeurs de tableaux](#ctor)|Initialise un tableau unidimensionnel et modifiable de types spécifiés par le paramètre de modèle de classe *T*.|  
  
### <a name="methods"></a>Méthodes  
 Consultez [Platform::WriteOnlyArray (classe)](../cppcx/platform-writeonlyarray-class.md).  
  
### <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|[Array::value](#value)|Récupère un handle vers le tableau actuel.|  
  
### <a name="remarks"></a>Notes  
 La classe Array est sealed et ne peut pas être héritée.  
  
 Le système de type Windows Runtime ne prend pas en charge le concept des tableaux en escalier et par conséquent, vous ne pouvez pas utiliser un IVector < Platform::Array\<T >> comme paramètre de méthode ou de la valeur de retour. Pour passer un tableau en escalier ou une séquence de séquences à travers l'ABI, utilisez `IVector<IVector<T>^>`.  
  
 Pour plus d’informations sur quand et comment utiliser Platform::Array, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
 Le système de type Windows Runtime ne prend pas en charge le concept des tableaux en escalier et par conséquent, vous ne pouvez pas utiliser un IVector < Platform::Array\<T >> comme paramètre de méthode ou de la valeur de retour. Pour passer un tableau en escalier ou une séquence de séquences à travers l'ABI, utilisez `IVector<IVector<T>^>`.  
  
 Cette classe est définie dans l'en-tête vccorlib.h, qui est inclus automatiquement par le compilateur. Il est visible dans IntelliSense mais pas dans l’Explorateur d’objets, car il n’est pas un type public défini dans platform.winmd.  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : **/ZW**  

 
## <a name="ctor"></a>  Constructeurs de tableaux
Initialise un tableau unidimensionnel et modifiable de types spécifiés par le paramètre de modèle de classe *T*.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Array(unsigned int size);  
Array(T* data, unsigned int size);    
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Paramètre de modèle de classe.  
  
 `size`  
 Nombre d’éléments dans le tableau.  
  
 `data`  
 Pointeur vers un tableau de données de type `T` utilisé pour initialiser l'objet Array.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la façon de créer des instances de Platform::Array, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>  Array::Get (méthode)
Extrait une référence à l'élément de tableau à la position d'index spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp    
T& get(unsigned int index)  const;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 Index de base zéro qui identifie un élément du tableau. L’index minimale est 0 et l’index maximal est la valeur spécifiée par la `size` paramètre dans le [constructeur de tableau](#ctor).  
  
### <a name="return-value"></a>Valeur de retour  
 Élément de tableau spécifié par le paramètre `index`.  
  
## <a name="value"></a>  Array::value (propriété)
Récupère un handle vers le tableau actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp 
property Array^ Value;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers le tableau actuel.  

## <a name="see-also"></a>Voir aussi  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)   
 [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)