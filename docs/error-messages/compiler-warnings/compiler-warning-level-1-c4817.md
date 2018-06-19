---
title: 'L’erreur c4817 : avertissement (niveau 1) du compilateur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4817
dev_langs:
- C++
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa1dfa3cf0e63e319198cd9394f194864f87eacf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286186"
---
# <a name="compiler-warning-level-1-c4817"></a>Avertissement du compilateur (niveau 1) C4817
'membre' : utilisation non conforme de '.' pour accéder à ce membre ; compilateur remplacé par '->'  
  
 Le mauvais opérateur d’accès aux membres a été utilisé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4817 :  
  
```  
// C4817.cpp  
// compile with: /clr /W1  
using namespace System;  
int main() {  
   array<Int32> ^ a = gcnew array<Int32>(100);  
   Console::WriteLine( a.Length );   // C4817  
   Console::WriteLine( a->Length );   // OK  
}  
```  
