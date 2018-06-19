---
title: Compilateur avertissement (niveau 4) C4214 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4214
dev_langs:
- C++
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0efe0666ded5428dcc40a1900f263cfc522a1502
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292920"
---
# <a name="compiler-warning-level-4-c4214"></a>Avertissement du compilateur (niveau 4) C4214
extension non standard utilisée : les types autres qu’int de champ de bits  
  
 Avec les extensions Microsoft (/Ze), les membres de structure de champ de bits peuvent être de n’importe quel type entier.  
  
## <a name="example"></a>Exemple  
  
```  
// C4214.c  
// compile with: /W4  
struct bitfields  
{  
   unsigned short j:4;  // C4214  
};  
  
int main()  
{  
}  
```  
  
 Ces champs de bits sont non valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).