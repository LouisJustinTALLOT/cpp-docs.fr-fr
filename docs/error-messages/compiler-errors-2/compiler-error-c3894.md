---
title: Erreur du compilateur C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: 4d935e140d89cb5c3714450597677a7a02a245e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496042"
---
# <a name="compiler-error-c3894"></a>Erreur du compilateur C3894

'var' : utilisation comme l-value des données membres static initonly est autorisée uniquement dans le constructeur de classe de la classe 'class'

Statique [initonly](../../dotnet/initonly-cpp-cli.md) données membres peuvent uniquement être utilisés comme l-values à leur point de déclaration ou dans un constructeur statique.

Instance (non statique) les données membres initonly peuvent uniquement être utilisés comme l-values à leur point de déclaration ou dans des constructeurs d’instance (non statique).

L’exemple suivant génère l’erreur C3894 :

```
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```