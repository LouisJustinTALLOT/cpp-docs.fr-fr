---
title: Erreur du compilateur C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 0bd1e770e38fcb85164bfa205470ac55a12e1c87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466194"
---
# <a name="compiler-error-c2061"></a>Erreur du compilateur C2061

Erreur de syntaxe : identificateur 'identifier'

Le compilateur a détecté un identificateur là où il n’était pas attendu. Assurez-vous que l’option `identifier` est déclaré avant de l’utiliser.

Un initialiseur peut être mis entre parenthèses. Pour éviter ce problème, incluez le déclarateur entre parenthèses ou en faire un `typedef`.

Cette erreur peut également être provoquée quand le compilateur détecte une expression comme argument de modèle de classe ; Utilisez [typename](../../cpp/typename.md) pour indiquer au compilateur qu’il s’agit d’un type.

L’exemple suivant génère l’erreur C2061 :

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

L’erreur C2061 peut se produire si vous passez un nom d’instance à [typeid](../../windows/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```