---
title: Avertissement du compilateur C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 9afdd213baadd907afacde0ff7f14f3c78bc60a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528256"
---
# <a name="compiler-warning-c4957"></a>Avertissement du compilateur C4957

> «*cast*' : cast explicite de '*cast_from*'en'*cast_to*' n’est pas vérifiable

## <a name="remarks"></a>Notes

Un cast aura pour résultat une image non vérifiable.

Certains casts sont « safe » (par exemple, un `static_cast` qui déclenche des conversions définies par l’utilisateur et un `const_cast`). Un [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) garantit la génération d’un code vérifiable.

Pour plus d’informations, consultez [Code pur et vérifiable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Le **/CLR : safe** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Cet avertissement, qui s’affiche comme une erreur, peut être désactivé avec le pragma [warning](../../preprocessor/warning.md) ou l’option du compilateur [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4957 :

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```