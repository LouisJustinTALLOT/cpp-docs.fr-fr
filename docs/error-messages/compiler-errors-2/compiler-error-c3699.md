---
title: Erreur du compilateur C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: 93058d34ca9a17ab175a55a7bc7b953d369e65c5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776737"
---
# <a name="compiler-error-c3699"></a>Erreur du compilateur C3699

'opérateur' : Impossible d’utiliser cette indirection sur le type 'type'

Une tentative a été effectuée à l’utilisation de l’indirection qui n’est pas autorisée sur `type`.

## <a name="example"></a>Exemple

L’exemple suivant génère C3699.

```
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

Une propriété triviale ne peut pas avoir de type référence. Pour plus d'informations, voir [property](../../extensions/property-cpp-component-extensions.md) . L’exemple suivant génère C3699.

```
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>Exemple

L’équivalent d’une syntaxe « pointeur vers un autre pointeur » est un handle vers une référence de suivi. L’exemple suivant génère C3699.

```
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```