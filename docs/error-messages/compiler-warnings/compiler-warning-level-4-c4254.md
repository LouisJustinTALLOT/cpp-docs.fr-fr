---
title: Compilateur avertissement (niveau 4) C4254 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c4254
dev_langs:
- C++
helpviewer_keywords:
- C4254
ms.assetid: c7dcef24-d535-4c98-bb41-fc3d2b88fd11
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b58184eef2913fcbcdd0e8c6284d26a2207e6681
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297714"
---
# <a name="compiler-warning-level-4-c4254"></a>Avertissement du compilateur (niveau 4) C4254
'opérateur' : conversion de 'type1' en 'type2', perte possible de données  
  
 Un plus grand champ de bits a été assigné à un champ de bits plus petit. Il peut exister une perte de données.  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 L’exemple suivant génère C4254 :  
  
```  
// C4254.cpp  
// compile with: /W4  
#pragma warning(default: 4254)  
  
struct X {  
   int a : 20;  
   int b : 12;  
};  
  
int main() {  
   X *x = new X();  
   x->b = 10;  
   x->a = 4;  
   x->a = x->b;    // OK  
   x->b = x->a;    // C4254  
};  
```