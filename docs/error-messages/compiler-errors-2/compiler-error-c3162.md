---
title: Erreur du compilateur C3162
ms.date: 11/04/2016
f1_keywords:
- C3162
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
ms.openlocfilehash: 95cd2c4af614906da7ba2d1c4c5dd488059f970a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761801"
---
# <a name="compiler-error-c3162"></a>Erreur du compilateur C3162

'type' : un type référence qui a un destructeur ne peut pas être utilisé comme type de données membres static’Member'

La common language runtime ne peut pas savoir quand exécuter un destructeur défini par l’utilisateur lorsque la classe contient également une fonction membre statique.

Un destructeur ne sera jamais exécuté, sauf si l’objet est supprimé explicitement.

Pour plus d'informations, consultez

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Problèmes courants de migration vers Visual C++ 64 bits](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3162.

```cpp
// C3162.cpp
// compile with: /clr /c
ref struct A {
   ~A() { System::Console::WriteLine("in destructor"); }
   static A i;   // C3162
   static A^ a = gcnew A;   // OK
};

int main() {
   A ^ a = gcnew A;
   delete a;
}
```
