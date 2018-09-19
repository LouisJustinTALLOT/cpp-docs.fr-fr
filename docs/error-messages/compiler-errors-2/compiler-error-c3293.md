---
title: Erreur du compilateur C3293 | Microsoft Docs
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3293
dev_langs:
- C++
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d45f342528b1ee6297ee6c11a01a0eceb710595
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050331"
---
# <a name="compiler-error-c3293"></a>Erreur du compilateur C3293

'accessor' : utilisez 'default' pour accéder à la propriété par défaut (indexeur) de la classe 'type'

L’accès à une propriété indexée est incorrect.  Consultez [Comment : utilisez les propriétés en C / c++ / CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) pour plus d’informations.

**Visual Studio 2017 et versions ultérieur**: dans Visual Studio 2015 et versions antérieur, le compilateur dans certains cas identifiait à tort une propriété par défaut comme un indexeur par défaut. Il était possible de contourner le problème en utilisant l’identificateur « default » pour accéder à la propriété. La solution de contournement elle-même est devenue problématique dès que default a été introduit comme mot clé dans C++11. Ainsi, dans Visual Studio 2017, les bogues qui nécessitaient la solution de contournement ont été corrigés, et le compilateur génère maintenant une erreur quand l’utilisateur recourt à « default » pour accéder à la propriété par défaut d’une classe.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3293 dans Visual Studio 2015 et versions antérieures.

```
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