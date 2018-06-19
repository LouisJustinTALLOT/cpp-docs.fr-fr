---
title: Compilateur avertissement (niveau 1) C4407 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbc02c32463703f658cef1d5756926311d89b193
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282949"
---
# <a name="compiler-warning-level-1-c4407"></a>Avertissement du compilateur (niveau 1) C4407
cast entre différentes représentations du pointeur en membre, le compilateur peut générer du code incorrect  
  
 Un cast incorrect a été détecté.  
  
 L’erreur C4407 peut être généré en conformité du compilateur pour Visual C++ 2005. Pointeur vers membre requiert désormais un nom qualifié et l’opérateur d’adresse (&).  
  
 L’erreur C4407 peut se produire si vous effectuez un cast entre un héritage plusieurs pointeur vers membre à un héritage simple pointeur vers membre. Parfois, cette solution puisse fonctionner, mais parfois, il ne peut pas, car la représentation sous forme de pointeur vers membre de l’héritage unique ne contient pas suffisamment d’informations. La compilation avec le **/VMM** peut vous aider (pour plus d’informations, consultez [/VMM, / VMS, /vmv (représentation à but général)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Vous pouvez également essayer de réorganiser vos classes de base ; le compilateur détecte une perte d’informations dans la conversion, car une classe de base est à un offset différent de zéro à partir de la liste dérivée.  
  
 L’exemple suivant génère l’erreur C4407 :  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```