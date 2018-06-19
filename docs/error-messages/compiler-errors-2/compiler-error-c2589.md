---
title: Erreur du compilateur C2589 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c15589358979f554a9c17114f7d78b05dd83c472
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230751"
---
# <a name="compiler-error-c2589"></a>Erreur du compilateur C2589
'identificateur' : jeton non conforme à droite de ' ::'  
  
 Si un nom de classe, structure ou union apparaît à gauche de l’opérateur de résolution de portée (doubles deux-points), le jeton à droite doit être une classe, une structure ou un membre d’union. Sinon, n’importe quel identificateur global peut apparaître à droite.  
  
 L’opérateur de résolution de portée ne peut pas être surchargé.  
  
 L’exemple suivant génère l’erreur C2589 :  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```