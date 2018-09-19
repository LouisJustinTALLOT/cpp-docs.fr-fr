---
title: Erreur du compilateur C3068 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdea26e204032c27f00639ee46a928c7bf084a4e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035617"
---
# <a name="compiler-error-c3068"></a>Erreur du compilateur C3068

'fonction' : une fonction 'naked' ne peut pas contenir des objets qui requièrent un déroulement si une exception C++ s’est produite

Le compilateur n’a pas pu effectuer le déroulement de pile sur un [naked](../../cpp/naked-cpp.md) fonction qui a levé une exception, car un objet temporaire a été créé dans la fonction et la gestion des exceptions C++ ([/EHsc](../../build/reference/eh-exception-handling-model.md)) a été spécifié.

Pour résoudre cette erreur, effectuez au moins une des opérations suivantes :

- Ne compilez pas avec /EHsc.

- Ne marquez pas la fonction en tant que `naked`.

- Ne créez pas un objet temporaire dans la fonction.

Si une fonction crée un objet temporaire sur la pile, si la fonction lève une exception, et si la gestion des exceptions C++ sont activée, le compilateur nettoie la pile si une exception est levée.

Lorsqu’une exception est levée, généré par le compilateur de code, appelée le prologue et épilogue, qui ne figurent pas dans une fonction naked, est exécutée pour une fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3068 :

```
// C3068.cpp
// compile with: /EHsc
// processor: x86
class A {
public:
   A(){}
   ~A(){}
};

void b(A){}

__declspec(naked) void c() {
   b(A());   // C3068
};
```