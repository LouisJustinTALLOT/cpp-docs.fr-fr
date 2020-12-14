---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4382'
title: Avertissement du compilateur (niveau 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 038225aea9592070b44af138be9deb5076e2f5f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311303"
---
# <a name="compiler-warning-level-1-c4382"></a>Avertissement du compilateur (niveau 1) C4382

> levée de'*type*' : un type avec __clrcall destructeur ou un constructeur de copie ne peut être intercepté que dans le module/CLR : pure

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

En cas de compilation avec **/CLR** (not **/clr : pure**), la gestion des exceptions s’attend à ce que les fonctions membres d’un type natif soient [__cdecl](../../cpp/cdecl.md) et non [__clrcall](../../cpp/clrcall.md). Les types natifs avec des fonctions membres utilisant `__clrcall` la Convention d’appel ne peuvent pas être interceptés dans un module compilé avec **/CLR**.

Si l’exception est interceptée dans un module compilé avec **/clr : pure**, vous pouvez ignorer cet avertissement.

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```
