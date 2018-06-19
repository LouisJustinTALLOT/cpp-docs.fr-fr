---
title: Compilateur avertissement (niveau 4) C4238 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06dbec01da8d1b47cb7b93c90a22ae5266e9b4c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292435"
---
# <a name="compiler-warning-level-4-c4238"></a>Avertissement du compilateur (niveau 4) C4238
extension non standard utilisée : classe rvalue utilisée comme lvalue  
  
 Pour la compatibilité avec les versions précédentes de Visual C++, les extensions Microsoft (**/Ze**) vous permettent d’utiliser un type de classe comme rvalue dans un contexte qui implicitement ou explicitement prend son adresse. Dans certains cas, par exemple, l’exemple ci-dessous, il peut s’avérer dangereux.  
  
## <a name="example"></a>Exemple  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 Cette utilisation génère une erreur sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).