---
title: Erreur du compilateur C2461 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47aee3122dad3e875cf58d5a41bcadda297e1463
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197635"
---
# <a name="compiler-error-c2461"></a>Erreur du compilateur C2461
  
> '*classe*' : syntaxe de constructeur absence de paramètres formels  
  
 Le constructeur de la classe ne spécifie pas de tous les paramètres formels. La déclaration d’un constructeur doit spécifier une liste de paramètres formels. La liste peut être vide.  
  
Pour résoudre ce problème, ajoutez une paire de parenthèses après la déclaration de *classe*:: **classe*.  
  
## <a name="example"></a>Exemple  
  
L’exemple suivant montre comment la corriger C2461 :  
  
```cpp  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;     // C2461  
   C::C();   // OK  
};  
```