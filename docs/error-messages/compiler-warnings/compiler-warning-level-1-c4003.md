---
title: Compilateur avertissement (niveau 1) C4003 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4003
dev_langs:
- C++
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a90202bfc06d50089e2ac283a5060bc431b9549c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274256"
---
# <a name="compiler-warning-level-1-c4003"></a>Compilateur avertissement (niveau 1) C4003
nombre de paramètres réels insuffisants pour la macro 'identificateur'  
  
 Le nombre de paramètres formels dans la définition de macro dépasse le nombre de paramètres réels dans la macro. L’expansion macro substitue un texte vide pour les paramètres manquants.  
  
 L’exemple suivant génère C4003 :  
  
```  
// C4003.cpp  
// compile with: /WX  
#define test(a,b) (a+b)  
  
int main()  
{  
   int a = 1;  
   int b = 2;  
   a = test(b);   // C4003  
   // try..  
   a = test(a,b);  
}  
```