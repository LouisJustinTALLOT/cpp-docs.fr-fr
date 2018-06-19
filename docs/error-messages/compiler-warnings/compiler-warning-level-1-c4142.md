---
title: Compilateur avertissement (niveau 1) C4142 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c87b7689cf11ab28c1a6377ff85e1594fd1b5fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284431"
---
# <a name="compiler-warning-level-1-c4142"></a>Compilateur avertissement (niveau 1) C4142
redéfinition bénigne du type  
  
 Un type est redéfini d’une manière qui n’a aucun effet sur le code généré.  
  
 Les causes possibles sont les suivantes :  
  
-   Une fonction membre d’une classe dérivée a un autre type de retour à partir de la fonction membre correspondante de la classe de base.  
  
-   Un type défini avec la `typedef` commande est redéfinie avec une syntaxe différente.  
  
 L’exemple suivant génère l’erreur C4142 :  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```