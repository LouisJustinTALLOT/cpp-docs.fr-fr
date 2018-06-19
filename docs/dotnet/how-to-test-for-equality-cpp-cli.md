---
title: 'Comment : tester l’égalité (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- equality, testing for
ms.assetid: 9115e298-9f75-452d-bdfb-6eeb0fa0b3c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c32bd9c73b7251f311593b547d4f3abdd33d7c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127979"
---
# <a name="how-to-test-for-equality-ccli"></a>Comment : tester l'égalité (C++/CLI)
Dans l’exemple suivant, un test d’égalité qui utilise les Extensions managées pour C++ est basé sur ce que les handles font référence.  
  
## <a name="example"></a>Exemple  
  
```  
// mcppv2_equality_test.cpp  
// compile with: /clr /LD  
using namespace System;  
  
bool Test1() {  
   String ^ str1 = "test";  
   String ^ str2 = "test";  
   return (str1 == str2);  
}  
```  
  
 Le langage intermédiaire de ce programme montre que la valeur de retour est implémentée à l’aide d’un appel à op_Equality.  
  
```  
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,  
                                                               string)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types managés (C++-CLI)](../dotnet/managed-types-cpp-cli.md)