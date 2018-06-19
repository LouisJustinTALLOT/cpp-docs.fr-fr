---
title: Erreur du compilateur C2975 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2975
dev_langs:
- C++
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53cb020dc0d456f10b7cfbae82a16b2ebe5fda6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246981"
---
# <a name="compiler-error-c2975"></a>Erreur du compilateur C2975

> '*argument*' : argument template non valide pour '*type*', expression constante de compilation attendue

L’argument de modèle ne correspond pas à la déclaration de modèle ; une expression constante doit apparaître entre crochets pointus. Les variables ne sont pas autorisées en tant qu’arguments réels du modèle. Vérifiez la définition du modèle pour trouver les types corrects.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2975 s’et montre également l’utilisation correcte :

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