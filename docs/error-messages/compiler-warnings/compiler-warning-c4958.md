---
description: 'En savoir plus sur : avertissement du compilateur C4958'
title: Avertissement du compilateur C4958
ms.date: 11/04/2016
f1_keywords:
- C4958
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
ms.openlocfilehash: 1a6260a441b619923e8c2ddf8c7a5d891a3c3844
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314800"
---
# <a name="compiler-warning-c4958"></a>Avertissement du compilateur C4958

> '*opération*' : l’opération arithmétique de pointeur n’est pas vérifiable

## <a name="remarks"></a>Notes

L’utilisation d’une opération arithmétique de pointeur produira une image non vérifiable.

Pour plus d’informations, consultez [Code pur et vérifiable (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

L’option de compilateur **/clr : safe** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Cet avertissement s’affiche comme une erreur et peut être désactivé avec le pragma [warning](../../preprocessor/warning.md) ou l’option du compilateur [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4958 :

```cpp
// C4958.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )
using namespace System;

int main( ) {
   Int32 arr[] = new Int32[10];
   Int32* p = &arr[0];
   p++;   // C4958
}
```

Le compilateur implémente des opérations de tableau avec l’opération arithmétique de pointeur. Par conséquent, les tableaux natifs ne sont pas vérifiables ; utilisez plutôt un tableau CLR. Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

L’exemple suivant génère l’avertissement C4958 :

```cpp
// C4958b.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )

int main() {
   int array[5];
   array[4] = 0;   // C4958
}
```
