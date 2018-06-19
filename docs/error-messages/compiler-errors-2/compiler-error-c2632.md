---
title: Erreur du compilateur C2632 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3bc07c404a1f4d667045fdfea24009e7d20ad69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232631"
---
# <a name="compiler-error-c2632"></a>Erreur du compilateur C2632
'type1' suivi de 'type2' est non conforme  
  
 Cette erreur peut être provoquée si le code entre deux spécificateurs de type est manquant.  
  
 L’exemple suivant génère C2632 :  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 Cette erreur peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003. `bool` est maintenant un type approprié. Dans les versions précédentes, `bool` était un typedef et vous pouviez créer des identificateurs portant ce nom.  
  
 L’exemple suivant génère C2632 :  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 Pour résoudre cette erreur, afin que le code soit valide dans les versions de Visual Studio .NET 2003 et de Visual Studio .NET de Visual C++, renommez l’identificateur.