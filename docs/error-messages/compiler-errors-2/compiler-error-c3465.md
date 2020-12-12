---
description: 'En savoir plus sur : erreur du compilateur C3465'
title: Erreur du compilateur C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: ab5d55b5e21241eb2bbab00524f3c81baaace88f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113452"
---
# <a name="compiler-error-c3465"></a>Erreur du compilateur C3465

pour pouvoir utiliser le type 'type', vous devez faire référence à l’assembly 'assembly'

Le transfert de type fonctionne pour une application cliente jusqu’à ce que vous recompiliez le client. Pour ce faire, vous avez besoin d’une référence pour chaque assembly contenant la définition d’un type utilisé dans votre application cliente.

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère un assembly qui contient le nouvel emplacement d’un type.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

L’exemple suivant génère un assembly qui contenait auparavant la définition du type, mais qui contient désormais la syntaxe de transfert du type.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

L’exemple suivant génère l’erreur C3465.

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
