---
title: Erreur du compilateur C2180 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2180
dev_langs:
- C++
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a43c179b837e840f800a6c468efdd9cdd6a6604b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171534"
---
# <a name="compiler-error-c2180"></a>Erreur du compilateur C2180
l'expression de contrôle a le type 'type'  
  
 L'expression de contrôle dans une instruction `if`, `while`, `for` ou `do` est une expression convertie vers `void`. Pour résoudre ce problème, remplacez l'expression de contrôle par une expression qui génère un `bool` ou un type pouvant être converti en `bool`.  
  
 L'exemple suivant génère l'erreur C2180 :  
  
```  
// C2180.c  
  
int main() {  
   while ((void)1)   // C2180  
      return 1;  
   while (1)         // OK  
      return 0;  
}  
```