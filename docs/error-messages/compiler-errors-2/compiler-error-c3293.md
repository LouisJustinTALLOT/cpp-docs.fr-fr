---
description: 'En savoir plus sur : erreur du compilateur C3293'
title: Erreur du compilateur C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 5ba4256997eed12d3a380d5f3a4d1876da75fb8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144636"
---
# <a name="compiler-error-c3293"></a>Erreur du compilateur C3293

'accessor' : utilisez 'default' pour accéder à la propriété par défaut (indexeur) de la classe 'type'

L’accès à une propriété indexée est incorrect.  Pour plus d’informations, consultez [Comment : utiliser des propriétés en C++/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) .

**Visual studio 2017 et versions ultérieures**: dans visual studio 2015 et versions antérieures, le compilateur, dans certains cas, a identifié une propriété par défaut comme indexeur par défaut. Il était possible de contourner le problème en utilisant l’identificateur « default » pour accéder à la propriété. La solution de contournement elle-même est devenue problématique dès que default a été introduit comme mot clé dans C++11. Ainsi, dans Visual Studio 2017, les bogues qui nécessitaient la solution de contournement ont été corrigés, et le compilateur génère maintenant une erreur quand l’utilisateur recourt à « default » pour accéder à la propriété par défaut d’une classe.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3293 dans Visual Studio 2015 et versions antérieures.

```cpp
// C3293.cpp
// compile with: /clr /c
using namespace System;
ref class IndexerClass {
public:
   // default indexer
   property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier

   String ^s = "Hello";
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier
   Console::WriteLine(wc2);
}
```
