---
description: 'En savoir plus sur : erreur du compilateur C3699'
title: Erreur du compilateur C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: 670b5c41aad9afcece8d8cd292727ad64925a4ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228714"
---
# <a name="compiler-error-c3699"></a>Erreur du compilateur C3699

'operator' : impossible d’utiliser cette indirection sur le type’type'

Une tentative d’utilisation de l’indirection n’est pas autorisée sur `type` .

## <a name="examples"></a>Exemples

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

Une propriété triviale ne peut pas avoir de type référence. Pour plus d’informations, consultez [property](../../extensions/property-cpp-component-extensions.md) . L’exemple suivant génère l’C3699.

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

L’équivalent d’une syntaxe « pointeur vers pointeur » est un handle vers une référence de suivi. L’exemple suivant génère l’C3699.

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
