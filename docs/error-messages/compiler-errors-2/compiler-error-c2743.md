---
description: 'En savoir plus sur : erreur du compilateur C2743'
title: Erreur du compilateur C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: 2619d4a0dd2b89d36f11944b59c2ab4993d95fd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123056"
---
# <a name="compiler-error-c2743"></a>Erreur du compilateur C2743

'type' : impossible d’intercepter un type natif avec __clrcall destructeur ou un constructeur de copie

Un module compilé avec **/CLR** a tenté d’intercepter une exception de type natif et où le destructeur du type ou le constructeur de copie utilise la `__clrcall` Convention d’appel.

En cas de compilation avec **/CLR**, la gestion des exceptions s’attend à ce que les fonctions membres d’un type natif soient [__cdecl](../../cpp/cdecl.md) et non [__clrcall](../../cpp/clrcall.md). Les types natifs avec des fonctions membres utilisant `__clrcall` la Convention d’appel ne peuvent pas être interceptés dans un module compilé avec **/CLR**.

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2743.

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
