---
title: Erreur du compilateur C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: dc64852523b6b56bc506260576e3c79164628340
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735929"
---
# <a name="compiler-error-c2061"></a>Erreur du compilateur C2061

erreur de syntaxe : identificateur’identifier'

Le compilateur a trouvé un identificateur là où il n’était pas attendu. Assurez-vous que `identifier` est déclaré avant de l’utiliser.

Un initialiseur peut être placé entre parenthèses. Pour éviter ce problème, mettez le déclarateur entre parenthèses ou faites-en un `typedef`.

Cette erreur peut également se produire lorsque le compilateur détecte une expression comme argument de modèle de classe. Utilisez [TypeName](../../cpp/typename.md) pour indiquer au compilateur qu’il s’agit d’un type.

L’exemple suivant génère l’C2061 :

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 peut se produire si vous transmettez un nom d’instance à [typeid](../../extensions/typeid-cpp-component-extensions.md):

```cpp
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
