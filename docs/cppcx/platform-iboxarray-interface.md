---
title: Platform::iboxarray, Interface | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78815ed42833c48074abbb4b0c0fa0203f8c35a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597318"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray, interface
`IBoxArray` est le wrapper pour les tableaux de types valeur passés via l'interface binaire d'application (ABI) ou stockés dans les collections d'éléments `Platform::Object^` tels que ceux dans les contrôles XAML.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Type de la valeur boxed dans chaque élément du tableau.  
  
### <a name="remarks"></a>Notes  
 `IBoxArray` est le C + c++ / nom CX pour `Windows::Foundation::IReferenceArray`.  
  
### <a name="members"></a>Membres  
 L'interface `IBoxArray` hérite de l'interface `IValueType` . `IBoxArray` a également ces membres :  
  
|Méthode|Description|  
|------------|-----------------|  
|[Valeur](#value)|Retourne le tableau non converti par boxing qui a été précédemment enregistré dans cette instance `IBoxArray` .|  

## <a name="value"></a> Iboxarray::value, propriété
Retourne la valeur qui a été enregistrée à l'origine dans cet objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>Paramètres  
 `T`  
 Type de la valeur boxed.  
  
### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Retourne la valeur qui a été enregistrée à l'origine dans cet objet.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir un exemple, consultez [Boxing](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)