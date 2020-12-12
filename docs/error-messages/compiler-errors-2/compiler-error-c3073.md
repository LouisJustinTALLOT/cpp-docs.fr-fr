---
description: 'En savoir plus sur : erreur du compilateur C3073'
title: Erreur du compilateur C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: e26938d6c708c364bb2447b793abf7d51adb5779
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320245"
---
# <a name="compiler-error-c3073"></a>Erreur du compilateur C3073

'type' : la classe ref n’a pas de constructeur de copie défini par l’utilisateur

Dans une compilation [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , le compilateur ne génère pas de constructeur de copie pour un type référence. Dans toute compilation **/CLR** , vous devez définir votre propre constructeur de copie pour un type référence si vous pensez qu’une instance du type doit être copiée.

Pour plus d’informations, consultez [sémantique de pile C++ pour les types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3073.

```cpp
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```
