---
title: Erreur du compilateur C2648 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2648
dev_langs:
- C++
helpviewer_keywords:
- C2648
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 059c8934f8f797af0dd937827e6c52cf06d0cf15
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102539"
---
# <a name="compiler-error-c2648"></a>Erreur du compilateur C2648

'identificateur' : utilisation d’un membre comme paramètre par défaut nécessite un membre static

Un membre non statique est utilisé comme un paramètre par défaut.

L’exemple suivant génère l’erreur C2648 :

```
// C2648.cpp
// compile with: /c
class C {
public:
   int i;
   static int j;
   void func1( int i = i );  // C2648  i is not static
   void func2( int i = j );  // OK
};
```