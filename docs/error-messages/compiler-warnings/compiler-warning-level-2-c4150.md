---
title: Avertissement (niveau 2) du compilateur C4150 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4150
dev_langs:
- C++
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3108da1b203160456e0823b4d9a3fd594b705a8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290476"
---
# <a name="compiler-warning-level-2-c4150"></a>Avertissement (niveau 2) du compilateur C4150
suppression de pointeur vers type incomplet 'type' ; aucun destructeur appelé  
  
 Le **supprimer** opérateur est appelé pour supprimer un type qui a été déclaré mais pas défini, donc le compilateur ne peut pas trouver de destructeur.  
  
 L’exemple suivant génère l’erreur C4150 :  
  
```  
// C4150.cpp  
// compile with: /W2  
class  IncClass;  
  
void NoDestruct( IncClass* pIncClass )  
{  
   delete pIncClass;  
} // C4150, define class to resolve  
  
int main()  
{  
}  
```