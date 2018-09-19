---
title: Erreur du compilateur C2061 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 896fdb21c57e0f558b87ec23e2be309cf49f8095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057962"
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