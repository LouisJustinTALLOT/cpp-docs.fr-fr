---
title: Erreur du compilateur C3409 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1964cffd0593e87a790befd8a76ae13847f2058d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257268"
---
# <a name="compiler-error-c3409"></a>Erreur du compilateur C3409
bloc d’attributs vide n’est pas autorisée.  
  
 Les crochets sont interprétés par le compilateur comme une [attribut](../../windows/cpp-attributes-reference.md) bloc, mais aucun attribut n’a été trouvé.  
  
 Le compilateur peut générer cette erreur lorsque vous utilisez des crochets dans le cadre de la définition d’une expression lambda. Cette erreur se produit lorsque le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs. Pour plus d’informations sur les expressions lambda, consultez [Expressions Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Si les crochets font partie d’un bloc d’attributs :  
  
    1.  Fournir un ou plusieurs attributs dans le bloc d’attributs.  
  
    2.  Supprimez le bloc d’attributs.  
  
2.  Si les crochets font partie d’une expression lambda :  
  
    1.  Assurez-vous que l’expression lambda suit les règles de syntaxe valide.  
  
         Pour plus d’informations sur la syntaxe d’expression lambda, consultez [syntaxe d’Expression Lambda](../../cpp/lambda-expression-syntax.md).  
  
    2.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3409.  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3409, car une expression lambda utilise le `mutable` spécification, mais ne fournit ne pas une liste de paramètres. Le compilateur ne peut pas déterminer si les crochets font partie de la définition d’une expression lambda ou d’un bloc d’attributs.  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Attribut](../../windows/cpp-attributes-reference.md)   
 [Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)   
 [Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)