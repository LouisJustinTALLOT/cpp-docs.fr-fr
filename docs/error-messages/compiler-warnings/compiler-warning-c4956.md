---
title: Avertissement du compilateur C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: c15de8b22f56a2555cc763a45153139b1df01a31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280839"
---
# <a name="compiler-warning-c4956"></a>Avertissement du compilateur C4956

> «*type*' : ce type n’est pas vérifiable

## <a name="remarks"></a>Notes

Cet avertissement est généré quand [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) est spécifié et que votre code contient un type qui n’est pas vérifiable. Le **/CLR : safe** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Pour plus d’informations, consultez [Code pur et vérifiable (C++ / c++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Cet avertissement, qui s’affiche comme une erreur, peut être désactivé avec le pragma [warning](../../preprocessor/warning.md) ou l’option du compilateur [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4956.

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```