---
description: 'En savoir plus sur : erreur du compilateur C2975'
title: Erreur du compilateur C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 9f9108d1dc4e0fe61b6dd2135fb69bbaedfaedf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210346"
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

C2975 se produit également lorsque vous utilisez &#95;&#95;&#95;&#95; de ligne comme une constante au moment de la compilation avec [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Une solution consisterait à compiler avec [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) au lieu de **/Zi**.

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
