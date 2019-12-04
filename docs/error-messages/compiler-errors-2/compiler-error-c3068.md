---
title: Erreur du compilateur C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: 9e20333a4fc18219f7f2514f3aefe73b81f284a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759488"
---
# <a name="compiler-error-c3068"></a>Erreur du compilateur C3068

'fonction' : une fonction’Naked’ne peut pas contenir d’objets qui requièrent un déroulement C++ si une exception s’est produite

Le compilateur n’a pas pu effectuer le déroulement de la pile sur une fonction [Naked](../../cpp/naked-cpp.md) qui a levé une exception parce qu’un objet temporaire a été C++ créé dans la fonction et que la gestion des exceptions ([/EHsc](../../build/reference/eh-exception-handling-model.md)) a été spécifiée.

Pour résoudre cette erreur, effectuez au moins l’une des opérations suivantes :

- Ne pas compiler avec/EHsc.

- Ne Marquez pas la fonction comme `naked`.

- Ne créez pas d’objet temporaire dans la fonction.

Si une fonction crée un objet temporaire sur la pile, si la fonction lève une exception et si C++ la gestion des exceptions est activée, le compilateur nettoie la pile si une exception est levée.

Quand une exception est levée, le code généré par le compilateur, appelé prologue et épilogue et qui ne sont pas présents dans une fonction Naked, est exécuté pour une fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3068 :

```cpp
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
