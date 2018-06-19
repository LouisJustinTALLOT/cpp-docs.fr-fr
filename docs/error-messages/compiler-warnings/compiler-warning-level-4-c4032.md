---
title: Du compilateur (niveau 4) d’avertissement C4032 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4032
dev_langs:
- C++
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb61588c12378972194305d979ecdd89140ac6f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291685"
---
# <a name="compiler-warning-level-4-c4032"></a>Du compilateur (niveau 4) d’avertissement C4032
le paramètre formel 'nombre' a un type différent lors de sa promotion  
  
 Le type de paramètre n’est pas compatible, via les promotions par défaut, avec le type d’une déclaration précédente.  
  
 Il s’agit d’une erreur en C ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) et un avertissement avec les extensions Microsoft (/Ze).  
  
## <a name="example"></a>Exemple  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```