---
title: Compilateur avertissement (niveau 1) C4925 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4925
dev_langs:
- C++
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62c661b4fffee6c6da17d72724d61b7df39a3268
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109442"
---
# <a name="compiler-warning-level-1-c4925"></a>Avertissement du compilateur (niveau 1) C4925

'méthode' : la méthode dispinterface ne peut pas être appelée à partir d’un script

Les langages de script ne peuvent pas créer de paramètres VT_BYREF « in », mais uniquement des paramètres VT_BYREF « out ».

Pour résoudre cet avertissement, vous pouvez également ne pas faire du paramètre un type pointeur (dans la définition et l’implémentation).

L’exemple suivant génère l’avertissement C4925 :

```
// C4925.cpp
// compile with: /LD /W1
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[ module(name="Test")];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IDisp {
   [id(9)] void f([in] int*);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002")  ]
struct CDisp : IDisp {   // C4925
   void f(int*) {}
};
```