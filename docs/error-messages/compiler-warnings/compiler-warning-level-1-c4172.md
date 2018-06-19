---
title: Du compilateur (niveau 1) d’avertissement C4172 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746442638820d0c81144611a678996dc4c8483b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276657"
---
# <a name="compiler-warning-level-1-c4172"></a>Du compilateur (niveau 1) d’avertissement C4172
Retourne l’adresse d’une variable locale ou temporaire  
  
 Une fonction retourne l’adresse d’un objet temporaire ou de variable local. Variables locales et les objets temporaires sont détruits lorsqu’une fonction retourne, l’adresse retournée n’est pas valide.  
  
 Reconcevez la fonction afin qu’il ne retourne pas de l’adresse d’un objet local.  
  
 L’exemple suivant génère l’erreur C4172 :  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```