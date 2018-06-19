---
title: Platform::WriteOnlyArray (classe) | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
dev_langs:
- C++
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5c1f1f0260d4f1d1c4a6fb640b7cbf1e9d3f2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091485"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray (classe)
Représente un tableau unidimensionnel utilisé comme paramètre d'entrée lorsque l'appelant transmet un tableau à remplir pour la méthode.  
  
 Cette classe ref est déclarée comme privée dans vccorlib.h. Par conséquent, elle n'est pas émise dans les métadonnées et est uniquement consommable à partir de C++. Cette classe est prévue uniquement pour être utilisée comme paramètre d'entrée qui accepte un tableau que l'appelant a alloué. Elle n'est pas constructible à partir du code utilisateur. Il permet à la méthode C++ d'écrire directement dans ce tableau, un modèle appelé modèle *FillArray* . Pour plus d’informations, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
### <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
 Ces méthodes offrent une accessibilité interne, c'est-à-dire qu'elles ne sont accessibles que dans l'application ou le composant C++.  
  
|Name|Description|  
|----------|-----------------|  

|[WriteOnlyArray::begin](#begin)| Itérateur qui pointe vers le premier élément du tableau. |  
|[WriteOnlyArray::Data](#data)| Un pointeur vers le tampon de données. |  
|[WriteOnlyArray::end](#end)| Itérateur qui pointe vers un suit le dernier élément du tableau. |  
|[WriteOnlyArray::FastPass](#fastpass)| Indique si le tableau peut utiliser le mécanisme FastPass, qui est une optimisation exécutée en toute transparence par le système. N’utilisez pas cela dans votre code |  
|[WriteOnlyArray::Length](#length)| Retourne le nombre d’éléments dans le tableau. |  
|[WriteOnlyArray::set](#set)| Définit l’élément spécifié à la valeur spécifiée. |  

  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `WriteOnlyArray`  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
 **Métadonnées :** platform.winmd  
  
 **Espace de noms :** Platform  

## <a name="begin"></a>  WriteOnlyArray::begin (méthode)
Retourne un pointeur désignant le premier élément du tableau.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T* begin() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur désignant le premier élément du tableau.  
  
### <a name="remarks"></a>Notes  
 Cet itérateur peut être utilisé avec les algorithmes STL tels que `std::sort` pour exécuter des opérations sur les élément du tableau.  
  


## <a name="data"></a>  WriteOnlyArray::Data, propriété
Pointeur vers le tampon de données.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers les octets bruts de tableau.  
  


## <a name="end"></a>  WriteOnlyArray::end (méthode)
Retourne un pointeur sur un point suivant au-delà du dernier élément du tableau.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T* end() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur de pointeur sur un point suivant au-delà du dernier élément du tableau.  
  
### <a name="remarks"></a>Notes  
 Cet itérateur peut être utilisé avec les algorithmes STL pour exécuter des opérations telles que `std::sort` sur les éléments de tableau.  
  


## <a name="fastpass"></a>  WriteOnlyArray::FastPass, propriété
Indique si l'optimisation interne FastPass peut être exécutée. Non destiné à être utilisé par le code utilisateur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui indique si le tableau est FastPass.  
  


## <a name="get"></a>  WriteOnlyArray::get (méthode)
Retourne l'élément à l'index spécifié.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T& get(  
   unsigned int indexArg) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `indexArg`  
  
### <a name="return-value"></a>Valeur de retour  
  


## <a name="length"></a>  WriteOnlyArray::Length, propriété
Retourne le nombre d'éléments du tableau alloué par l'appelant.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property unsigned int Length{  
   unsigned int get() const;  
}  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d’éléments dans le tableau.  
  


## <a name="set"></a>  WriteOnlyArray::set (fonction)
Définit la valeur spécifiée à l'index spécifié dans le tableau.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
### <a name="parameters"></a>Paramètres  
 `indexArg`  
 Index de l'élément à définir.  
  
 `valueArg`  
 Valeur à définir à `indexArg`.  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à l'élément qui vient d'être défini.  
  

  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la manière d’interpréter la valeur HRESULT, consultez [Structure of COM Error Codes](http://go.microsoft.com/fwlink/p/?LinkId=262045).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)   
 [Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)