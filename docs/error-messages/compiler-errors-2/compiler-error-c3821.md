---
title: Erreur du compilateur C3821 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3821
dev_langs:
- C++
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e1f9a0bbb8eaae6b316b3d00e4201b2b64222ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023031"
---
# <a name="compiler-error-c3821"></a>Erreur du compilateur C3821

'fonction' : fonction ou type managé ne peut pas être utilisée dans une fonction non managée

Fonctions avec un assembly inline ou [setjmp](../../c-runtime-library/reference/setjmp.md) ne peut pas contenir des types valeur ou des classes managées. Pour corriger cette erreur, supprimez l’assembly inline et `setjmp` ou supprimez les objets gérés.

C3821 peut également se produire si vous essayez d’utiliser le stockage automatique dans une fonction vararg.  Pour plus d’informations, consultez [listes d’arguments variables (...) (C + C++ / CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md) et [sémantique de pile C++ pour les Types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3821.

```
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>Exemple

L’exemple suivant génère C3821.

```
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
