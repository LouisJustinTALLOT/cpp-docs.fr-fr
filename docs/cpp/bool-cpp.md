---
title: bool (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3bd43c9ceb4f0a0f73b86e3a4ecf4d851d504b3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939310"
---
# <a name="bool-c"></a>bool (C++)

Ce mot clé est un type intégré. Une variable de ce type peut avoir des valeurs [true](../cpp/true-cpp.md) et [false](../cpp/false-cpp.md). Expressions conditionnelles ont le type **bool** et ont ainsi des valeurs de type **bool**. Par exemple, `i!=0` a maintenant TRUE ou FALSE selon la valeur de `i`.  

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : l’opérande d’un préfixe ou suffixe incrémentation ou de décrémentation opérateur ne peut pas être de type **bool**. En d’autres termes, avec une variable `b` de type **bool**, ces expressions ne sont plus autorisées :

```cpp
    b++;
    ++b;
    b--;
    --b;
```
  
Les valeurs TRUE et FALSE ont la relation suivante :  
  
```cpp  
!false == true  
!true == false  
```  
  
Dans l'instruction suivante :  
  
```cpp  
if (condexpr1) statement1;   
```  
  
Si `condexpr1` a la valeur TRUE, `statement1` est toujours exécuté ; si `condexpr1` est FALSE, `statement1` n’est jamais exécutée.  
  
Lorsqu’un préfixe ou suffixe **++** opérateur est appliqué à une variable de type **bool**, la variable est définie sur TRUE. 
**Visual Studio 2017 15.3 et versions ultérieures**: opérateur ++ pour **bool** a été supprimé du langage et n’est plus pris en charge.

Le préfixe ou suffixe **--** opérateur ne peut pas être appliqué à une variable de ce type.  
  
 Le **bool** type participe aux promotions intégrales. R-value de type **bool** peut être converti en une r-value de type **int**, avec FALSE devenant zéro et TRUE devenant un. Comme un type distinct, **bool** participe à la résolution de surcharge.  
  
## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types fondamentaux](../cpp/fundamental-types-cpp.md)<br/>
