---
title: Compilateur avertissement (niveau 1) C4090 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a28924b2cf176524a2ecd3156394dd7530cfb9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276488"
---
# <a name="compiler-warning-level-1-c4090"></a>Compilateur avertissement (niveau 1) C4090
'opération' : les qualificateurs 'modificateur' différents  
  
 Une variable utilisée dans une opération est définie avec un modificateur spécifié qui l’empêche d’être modifiée sans détection par le compilateur. L’expression est compilée sans modification.  
  
 Cet avertissement peut être provoqué lorsqu’un pointeur vers un **const** ou `volatile` élément est assigné à un pointeur non déclaré comme pointant vers **const** ou `volatile`.  
  
 Cet avertissement est émis pour les programmes C. Dans un programme C++, le compilateur génère une erreur : [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).  
  
 L’exemple suivant génère l’erreur C4090 :  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```