---
description: 'En savoir plus sur : erreur du compilateur C3894'
title: Erreur du compilateur C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: 6290cb247e45c4bd3fd3b140f467d608203b488b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115779"
---
# <a name="compiler-error-c3894"></a>Erreur du compilateur C3894

'var' : l’utilisation de l-value des données membres static initonly n’est autorisée que dans le constructeur de classe de la classe’class'

Les membres de données [initonly](../../dotnet/initonly-cpp-cli.md) statiques ne peuvent être utilisés que comme l-Values à leur point de déclaration, ou dans un constructeur statique.

Les données membres initonly de l’instance (non statiques) peuvent uniquement être utilisées comme l-Values à leur point de déclaration, ou dans des constructeurs d’instance (non statiques).

L’exemple suivant génère l’C3894 :

```cpp
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
