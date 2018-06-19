---
title: Erreur du compilateur C2274 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2274
dev_langs:
- C++
helpviewer_keywords:
- C2274
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd9bda3f3b0ab267ec008443dd865334e1b765e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33173023"
---
# <a name="compiler-error-c2274"></a>Erreur du compilateur C2274
'type' : non conforme à droite de '.' (opérateur)  
  
 Un type apparaît comme l’opérande de droite d’un opérateur d’accès aux membres (.).  
  
 Cette erreur peut être provoquée en essayant d’accéder à une conversion de type défini par l’utilisateur. Utilisez le mot clé `operator` entre la période et `type`.  
  
 L’exemple suivant génère l’erreur C2286 :  
  
```  
// C2274.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
  
int main() {  
   MyClass ClassName;  
   int i = ClassName.int();   // C2274  
   int j = ClassName.operator int();   // OK  
}  
```