---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4481'
title: Avertissement du compilateur (niveau 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: 463df18090a4f6f632a80543576db4cb9048e754
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251295"
---
# <a name="compiler-warning-level-4-c4481"></a>Avertissement du compilateur (niveau 4) C4481

extension non standard utilisée : spécificateur de substitution’keyword'

Un mot clé qui n’est pas dans la norme C++, par exemple, un des spécificateurs de substitution qui fonctionne également sous/CLR.  Pour plus d'informations, consultez

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Spécificateurs de substitution](../../extensions/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4481.

```cpp
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```
