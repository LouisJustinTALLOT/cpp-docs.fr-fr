---
title: Erreur du compilateur C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 1d82d367c5b77f54548403b7b142aa740919b6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756563"
---
# <a name="compiler-error-c3465"></a>Erreur du compilateur C3465

pour pouvoir utiliser le type 'type', vous devez faire référence à l’assembly 'assembly'

Le transfert de type fonctionne pour une application cliente jusqu’à ce que vous recompiliez le client. Pour ce faire, vous avez besoin d’une référence pour chaque assembly contenant la définition d’un type utilisé dans votre application cliente.

Pour plus d’informations, consultez [transfert de typeC++(/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère un assembly qui contient le nouvel emplacement d’un type.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Exemple

L’exemple suivant génère un assembly qui contenait auparavant la définition du type, mais qui contient désormais la syntaxe de transfert du type.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Exemple

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
