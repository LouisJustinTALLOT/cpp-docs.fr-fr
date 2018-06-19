---
title: Erreur du compilateur C2084 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce1510dd6e78b8774d3cc433f583c16cdbb8d06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33173875"
---
# <a name="compiler-error-c2084"></a>Erreur du compilateur C2084
fonction '*fonction*' a déjà un corps  
  
 La fonction a déjà été définie.  
  
 Dans les versions de Visual C++ antérieures à Visual Studio 2002,  
  
-   Le compilateur accepte plusieurs spécialisations de modèle résolu sur le même type, bien que les définitions supplémentaires ne sont jamais accessibles. Le compilateur détecte maintenant ces définitions multiples.  
  
-   `__int32` et `int` étaient considérées comme des types distincts. Le compilateur traite maintenant `__int32` comme synonyme de `int`. Cela signifie que le compilateur détecte plusieurs définitions si une fonction est surchargée sur les deux `__int32` et `int` et génère une erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2084 :  
  
```cpp  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
Pour corriger cette erreur, supprimez la définition en double :  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```