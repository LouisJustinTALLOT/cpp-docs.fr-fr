---
title: Erreur du compilateur C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: ec902266550e591623894823e6336bd2436bfbd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758032"
---
# <a name="compiler-error-c3699"></a>Erreur du compilateur C3699

'operator' : impossible d’utiliser cette indirection sur le type’type'

Une tentative d’utilisation d’une indirection n’est pas autorisée sur `type`.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3699.

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>Exemple

Une propriété triviale ne peut pas avoir de type référence. Pour plus d'informations, voir [property](../../extensions/property-cpp-component-extensions.md) . L’exemple suivant génère l’C3699.

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>Exemple

L’équivalent d’une syntaxe « pointeur vers pointeur » est un handle vers une référence de suivi. L’exemple suivant génère l’C3699.

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
