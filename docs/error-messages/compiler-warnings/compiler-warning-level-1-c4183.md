---
title: Compilateur avertissement (niveau 1) C4183 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4183
dev_langs:
- C++
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a271c12facaacdd07b4a664396c36c7301ac2f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277470"
---
# <a name="compiler-warning-level-1-c4183"></a>Compilateur avertissement (niveau 1) C4183
'identificateur' : type de retour manquant censé pour être une fonction membre retournant 'int'  
  
 La définition d’une fonction membre dans une classe ou une structure en ligne n’a pas un type de retour. Cette fonction membre est censée pour avoir une valeur par défaut de type de retour `int`.  
  
 L’exemple suivant génère l’erreur C4183 :  
  
```  
// C4183.cpp  
// compile with: /W1 /c  
#pragma warning(disable : 4430)  
class MyClass1;  
class MyClass2 {  
   MyClass1() {};   // C4183  
};  
```