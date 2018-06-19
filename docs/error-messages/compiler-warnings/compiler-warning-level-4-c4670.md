---
title: Compilateur avertissement (niveau 4) C4670 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4670
dev_langs:
- C++
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bec30fff715984073aa3061979fff11923f0bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315358"
---
# <a name="compiler-warning-level-4-c4670"></a>Avertissement du compilateur (niveau 4) C4670
'identificateur' : cette classe de base n’est pas accessible  
  
 La classe de base spécifiée d’un objet devant être levé dans un bloc **try** n’est pas accessible. L’objet ne peut pas être instancié s’il est levé. Vérifiez que la classe de base est héritée avec le bon spécificateur d’accès.  
  
 L’exemple suivant génère l’avertissement C4670 :  
  
```  
// C4670.cpp  
// compile with: /EHsc /W4  
class A  
{  
};  
  
class B : /* public */ A  
{  
} b;   // inherits A with private access by default  
  
int main()  
{  
    try  
    {  
       throw b;   // C4670  
    }  
    catch( B )  
    {  
    }  
}  
```