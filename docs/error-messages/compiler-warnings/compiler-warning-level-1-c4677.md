---
title: Compilateur avertissement (niveau 1) C4677 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3511ad3100bf695cec5df97703b39e5926c71c11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281692"
---
# <a name="compiler-warning-level-1-c4677"></a>Avertissement du compilateur (niveau 1) C4677
'fonction' : signature de membre non privée contient un type privé d’assembly 'type_privé'  
  
 Un type qui a une accessibilité publique en dehors de l’assembly utilise un type qui possède un accès privé en dehors de l’assembly. Un composant qui fait référence au type d’assembly public ne sera pas en mesure d’utiliser le type ou les membres qui font référence au type privé d’assembly.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4677 :.  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```