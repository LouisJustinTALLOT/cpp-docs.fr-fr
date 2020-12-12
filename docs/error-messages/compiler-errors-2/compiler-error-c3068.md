---
description: 'En savoir plus sur : erreur du compilateur C3068'
title: Erreur du compilateur C3068
ms.date: 11/04/2016
f1_keywords:
- C3068
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
ms.openlocfilehash: a73c525f017a3d571600e31d4c9ea875d0b25662
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281670"
---
# <a name="compiler-error-c3068"></a>Erreur du compilateur C3068

'fonction' : une fonction’Naked’ne peut pas contenir d’objets qui requièrent un déroulement si une exception C++ s’est produite

Le compilateur n’a pas pu effectuer le déroulement de la pile sur une fonction [Naked](../../cpp/naked-cpp.md) qui a levé une exception parce qu’un objet temporaire a été créé dans la fonction et que la gestion des exceptions C++ ([/EHsc](../../build/reference/eh-exception-handling-model.md)) a été spécifiée.

Pour résoudre cette erreur, effectuez au moins l’une des opérations suivantes :

- Ne pas compiler avec/EHsc.

- Ne Marquez pas la fonction comme `naked` .

- Ne créez pas d’objet temporaire dans la fonction.

Si une fonction crée un objet temporaire sur la pile, si la fonction lève une exception et que la gestion des exceptions C++ est activée, le compilateur nettoie la pile si une exception est levée.

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
