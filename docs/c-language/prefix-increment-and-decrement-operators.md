---
title: Opérateurs préfixés d’incrémentation et de décrémentation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116921ea46418db5c8eff3327de73a40aa42533c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384527"
---
# <a name="prefix-increment-and-decrement-operators"></a>Opérateurs préfixés d'incrémentation et de décrémentation
Les opérateurs unaires (`++` et **--**) sont appelés opérateurs d’incrémentation ou de décrémentation « préfixés » lorsqu’ils apparaissent avant l’opérande. L'incrémentation et la décrémentation suffixées ont une priorité plus élevée que l'incrémentation et la décrémentation préfixées. L’opérande doit être de type entier, flottant ou pointeur et doit être une expression lvalue modifiable (une expression sans l’attribut **const**). Le résultat est une l-value.  
  
 Lorsque l'opérateur apparaît avant son opérande, l'opérande est incrémenté ou décrémenté et sa nouvelle valeur est le résultat de l'expression.  
  
 Un opérande de type intégral ou virgule flottante est incrémenté ou décrémenté par la valeur 1 entière. Le type du résultat est identique au type d'opérande. Un opérande de type pointeur est incrémenté ou décrémenté par la taille de l'objet qu'il adresse. Un pointeur incrémenté pointe vers l'objet suivant. Un pointeur décrémenté pointe vers l'objet précédent.  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre l'opérateur de pré-décrémentation unaire :  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 Dans cet exemple, la variable `i` est décrémentée avant d'être utilisée comme indice sur `line`.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs unaires C](../c-language/c-unary-operators.md)