---
title: Erreur du compilateur C3851 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82104776b2d1153310d0552bd873238333e746f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268830"
---
# <a name="compiler-error-c3851"></a>Erreur du compilateur C3851
« char » : un nom de caractère universel ne peut pas désigner un caractère du jeu de caractères de base  
  
 Dans le code compilé en C++, vous ne pouvez pas utiliser un nom de caractère universel représentant un caractère dans le jeu de caractères source de base en dehors d’une chaîne ou d’un littéral de caractère. Pour plus d’informations, consultez [jeux de caractères](../../cpp/character-sets.md). Dans le code compilé en tant que C, vous ne pouvez pas utiliser un nom de caractère universel pour les caractères dans la plage 0x20-0x7f, inclusivement, excepté pour 0x24 (« $ »), 0x40 (« @ ») ou 0x60 (« ` »).  
  
 Les exemples suivants génèrent C3851 et montrent comment résoudre le problème :  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```