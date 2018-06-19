---
title: Compilateur avertissement (niveau 3) C4159 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4159
dev_langs:
- C++
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 139a21f5fbb7ce279d96f9df8be6008c2f092287
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291669"
---
# <a name="compiler-warning-level-3-c4159"></a>Compilateur avertissement (niveau 3) C4159
\#pragma pragma(pop,...) : a exécuté un POP l’identificateur 'identificateur'  
  
 Votre code source contient un **push** instruction avec un identificateur pour un pragma suivi d’une **pop** instruction sans identificateur. Par conséquent, ***identificateur*** est dépilé et ultérieures utilise de ***identificateur*** peuvent provoquer un comportement inattendu.  
  
 Pour éviter cet avertissement, donnez un identificateur dans le **pop** instruction. Par exemple :  
  
```  
// C4159.cpp  
// compile with: /W3  
#pragma pack(push, f)  
#pragma pack(pop)   // C4159  
  
// using the identifier resolves the warning  
// #pragma pack(pop, f)  
  
int main()  
{  
}  
```