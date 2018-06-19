---
title: Exporter | Documents Microsoft
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
ms.openlocfilehash: 67b71639fc0b7d0039f5665d2cc187191ac14baf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874601"
---
# <a name="export"></a>exporter
Provoque une structure de données doit être placé dans le fichier .idl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[export]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **exporter** attribut C++ provoque une structure de données doit être placé dans le fichier .idl et soit disponible dans la bibliothèque de types dans un format compatible binaire qui la rend disponible pour une utilisation avec n’importe quel langage.  
  
 Vous ne pouvez pas appliquer le **exporter** attribut à une classe, même si la classe possède uniquement des membres publics (l’équivalent d’un `struct`).  
  
 Si vous exportez sans nom `enum`s ou `struct`s, elles seront donné des noms qui commencent par **__unnamed *** x*, où *x* est un numéro séquentiel.  
  
 Les typedefs valides pour l’exportation sont des types de base, les structures, unions, énumérations, ou tapez les identificateurs.  Consultez [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le **exporter** attribut :  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**Union**, `typedef`, `enum`, `struct`, ou `interface`|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du compilateur](../windows/compiler-attributes.md)   
 [Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)   
