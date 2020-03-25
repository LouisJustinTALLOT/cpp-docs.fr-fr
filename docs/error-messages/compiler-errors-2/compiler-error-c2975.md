---
title: Erreur du compilateur C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 70fc648de8bcf4f1e85edf3a12cc0b7d3d70625f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201563"
---
# <a name="compiler-error-c2975"></a>Erreur du compilateur C2975

> '*argument*' : argument template non valide pour'*type*', expression constante au moment de la compilation attendue

L’argument de modèle ne correspond pas à la déclaration de modèle ; une expression constante doit apparaître entre crochets. Les variables ne sont pas autorisées comme arguments réels template. Vérifiez la définition du modèle pour trouver les types corrects.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2975 et affiche également l’utilisation correcte :

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

C2975 se produit également lorsque vous &#95; &#95;utilisez&#95; &#95; Line comme constante au moment de la compilation avec [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Une solution consisterait à compiler avec [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) au lieu de **/Zi**.

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
