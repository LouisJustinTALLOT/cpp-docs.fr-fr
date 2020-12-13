---
description: 'En savoir plus sur : avertissement du compilateur C4959'
title: Avertissement du compilateur C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 3a4fae04ee654caf23776a7bf4d6b073853bd03a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336085"
---
# <a name="compiler-warning-c4959"></a>Avertissement du compilateur C4959

> Impossible de définir le struct'*type*'non managé dans/CLR : safe, car l’accès à ses membres génère du code non vérifiable

## <a name="remarks"></a>Notes

L’accès à un membre d’un type non managé entraîne la création d’une image non vérifiable (peverify.exe).

Pour plus d’informations, consultez [Code pur et vérifiable (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

L’option de compilateur **/clr : safe** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Cet avertissement s’affiche comme une erreur et peut être désactivé avec le pragma [warning](../../preprocessor/warning.md) ou l’option du compilateur [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4959.

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```
