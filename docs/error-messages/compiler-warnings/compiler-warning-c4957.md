---
description: 'En savoir plus sur : avertissement du compilateur C4957'
title: Avertissement du compilateur C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: ac9d41b6161f658eb7debf438c495fbc57c6bb2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314826"
---
# <a name="compiler-warning-c4957"></a>Avertissement du compilateur C4957

> '*Cast*' : le cast explicite de'*cast_from*'en'*cast_to*'n’est pas vérifiable

## <a name="remarks"></a>Notes

Un cast aura pour résultat une image non vérifiable.

Certains casts sont sécurisés (par exemple, un **`static_cast`** qui déclenche des conversions définies par l’utilisateur et un **`const_cast`** ). Un [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) garantit la génération d’un code vérifiable.

Pour plus d’informations, consultez [Code pur et vérifiable (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

L’option de compilateur **/clr : safe** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Cet avertissement s’affiche comme une erreur et peut être désactivé avec le pragma [warning](../../preprocessor/warning.md) ou l’option du compilateur [/wd](../../build/reference/compiler-option-warning-level.md) .

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
