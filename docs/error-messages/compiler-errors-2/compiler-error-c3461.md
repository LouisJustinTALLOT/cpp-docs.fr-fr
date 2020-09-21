---
title: Erreur du compilateur C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: c5195e0a9bba1bc9e5962f3d3ae1795bb098be3d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742877"
---
# <a name="compiler-error-c3461"></a>Erreur du compilateur C3461

'type' : seul un type managé peut être transféré

Le transfert de type se produit uniquement sur les types CLR.  Pour plus d’informations, consultez [classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md) .

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

L’exemple suivant génère l’erreur C3461.

```cpp
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
