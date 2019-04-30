---
title: Erreur du compilateur C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 66b7c0d61cbc8141b9ed3e5f6eb329b68eb00477
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344700"
---
# <a name="compiler-error-c2975"></a>Erreur du compilateur C2975

> «*argument*' : argument template non valide pour '*type*', expression de constante de compilation attendue

L’argument de modèle ne correspond pas à la déclaration de modèle ; une expression constante doit apparaître entre crochets pointus. Les variables ne sont pas autorisés comme arguments réels du modèle. Vérifiez la définition du modèle pour trouver les types corrects.

## <a name="example"></a>Exemple

L’exemple suivant génère le C2975 et illustre également l’utilisation correcte :

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 se produit également lorsque vous utilisez &#95; &#95;ligne&#95; &#95; comme une constante de compilation avec [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Une solution consisterait à compiler avec [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) au lieu de **/Zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```