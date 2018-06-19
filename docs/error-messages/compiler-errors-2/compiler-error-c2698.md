---
title: Erreur du compilateur C2698 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c466e39702f1e408ad96d79c16c4a5953fa373f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233815"
---
# <a name="compiler-error-c2698"></a>Erreur du compilateur C2698
la déclaration using pour ' déclaration 1' ne peuvent pas coexister avec la déclaration using existante pour ' déclaration 2'  
  
 Une fois que vous avez un [à l’aide de la déclaration](../../cpp/using-declaration.md) pour un membre de données, à l’aide de toute déclaration dans la même portée qui utilise le même nom n’est pas autorisée, car seules les fonctions peuvent être surchargées.  
  
 L’exemple suivant génère C2698 :  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```