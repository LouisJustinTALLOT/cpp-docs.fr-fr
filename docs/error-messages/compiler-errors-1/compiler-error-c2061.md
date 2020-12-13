---
description: 'En savoir plus sur : erreur du compilateur C2061'
title: Erreur du compilateur C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: e857f4c4de90fadecdd7b7062306391b4222bcf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328721"
---
# <a name="compiler-error-c2061"></a>Erreur du compilateur C2061

erreur de syntaxe : identificateur’identifier'

Le compilateur a trouvé un identificateur là où il n’était pas attendu. Assurez `identifier` -vous que est déclaré avant de l’utiliser.

Un initialiseur peut être placé entre parenthèses. Pour éviter ce problème, mettez le déclarateur entre parenthèses ou faites-en un **`typedef`** .

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
