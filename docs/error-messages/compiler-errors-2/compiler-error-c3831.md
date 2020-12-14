---
description: 'En savoir plus sur : erreur du compilateur C3831'
title: Erreur du compilateur C3831
ms.date: 11/04/2016
f1_keywords:
- C3831
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
ms.openlocfilehash: ba3d1e7f6dfc2670307e510ee6eb13fa6277bc1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311810"
---
# <a name="compiler-error-c3831"></a>Erreur du compilateur C3831

'membre' : 'classe’ne peut pas avoir de membre de données épinglé ou une fonction membre qui retourne un pointeur épingle

[pin_ptr (C++/CLI)](../../extensions/pin-ptr-cpp-cli.md) a été utilisé de façon incorrecte.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3831 :

```cpp
// C3831a.cpp
// compile with: /clr
ref class Y
{
public:
   int i;
};

ref class X
{
   pin_ptr<int> mbr_Y;   // C3831
   int^ mbr_Y2;   // OK
};

int main() {
   Y y;
   pin_ptr<int> p = &y.i;
}
```
