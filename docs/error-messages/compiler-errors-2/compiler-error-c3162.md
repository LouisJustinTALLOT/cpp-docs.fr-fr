---
description: 'En savoir plus sur : erreur du compilateur C3162'
title: Erreur du compilateur C3162
ms.date: 11/04/2016
f1_keywords:
- C3162
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
ms.openlocfilehash: ca44b27607a34a469a5fd6fc1371e1510452247a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242312"
---
# <a name="compiler-error-c3162"></a>Erreur du compilateur C3162

'type' : un type référence qui a un destructeur ne peut pas être utilisé comme type de données membres static’Member'

La common language runtime ne peut pas savoir quand exécuter un destructeur défini par l’utilisateur lorsque la classe contient également une fonction membre statique.

Un destructeur ne sera jamais exécuté, sauf si l’objet est supprimé explicitement.

Pour plus d'informations, consultez

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

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
