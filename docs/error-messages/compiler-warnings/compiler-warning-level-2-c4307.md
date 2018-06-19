---
title: Compilateur avertissement (niveau 2) C4307 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52914fc5825bda5647308c006b853538f3d6225e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292030"
---
# <a name="compiler-warning-level-2-c4307"></a>Avertissement du compilateur (niveau 2) C4307
'opérateur' : dépassement de constante intégrale  
  
 L’opérateur est utilisé dans une expression qui aboutit à une constante entière un dépassement de l’espace alloué pour celle-ci. Vous devrez peut-être utiliser un type plus grand pour la constante. A **type signed int** contient une valeur inférieure à celle un `unsigned int` , car le **type signed int** utilise un bit pour représenter le signe.  
  
 L’exemple suivant génère l’erreur C4307 :  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```