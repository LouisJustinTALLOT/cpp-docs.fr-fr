---
description: 'En savoir plus sur : erreur du compilateur C3350'
title: Erreur du compilateur C3350
ms.date: 11/04/2016
f1_keywords:
- C3350
helpviewer_keywords:
- C3350
ms.assetid: cfbbc338-92b5-4f34-999e-aa2d2376bc70
ms.openlocfilehash: edda71fdf8f1160d17099a7cee228a053ddd881b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326012"
---
# <a name="compiler-error-c3350"></a>Erreur du compilateur C3350

'délégué' : un constructeur délégué attend 'nombre' argument(s)

Quand vous créez une instance d’un délégué, vous devez passer deux arguments, une instance du type contenant la fonction déléguée et la fonction.

L’exemple suivant génère l’erreur C3350 :

```cpp
// C3350.cpp
// compile with: /clr
delegate void SumDelegate();

public ref class X {
public:
   void F() {}
   static void F2() {}
};

int main() {
   X ^ MyX = gcnew X();
   SumDelegate ^ pSD = gcnew SumDelegate();   // C3350
   SumDelegate ^ pSD1 = gcnew SumDelegate(MyX, &X::F);
   SumDelegate ^ pSD2 = gcnew SumDelegate(&X::F2);
}
```
