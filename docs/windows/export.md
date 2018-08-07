---
title: Exporter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48c4a645456e3b3c0556dfed268ce911e5799fc3
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569415"
---
# <a name="export"></a>exporter
Provoque une structure de données à placer dans le fichier .idl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[export]  
```  
  
## <a name="remarks"></a>Notes  
 Le **exporter** attribut C++ provoque une structure de données à placer dans le fichier .idl et soit disponible dans la bibliothèque de types dans un format compatible binaire qui le rend disponible pour une utilisation avec n’importe quel langage.  
  
 Vous ne pouvez pas appliquer le **exporter** attribut à une classe, même si la classe a uniquement des membres publics (l’équivalent d’un **struct**).  
  
 Si vous exportez sans nom **enum**s ou **struct**s, elles seront nommées qui commencent par **__unnamed *** x*, où *x* est un séquentiel nombre.  
  
 Les typedefs valides pour l’exportation sont des types de base, les structures, unions, énumérations, ou tapez les identificateurs.  Consultez [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le **exporter** attribut :  
  
```cpp  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**Union**, **typedef**, **enum**, **struct**, ou **interface**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs de compilateur](../windows/compiler-attributes.md)   
 [Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)   