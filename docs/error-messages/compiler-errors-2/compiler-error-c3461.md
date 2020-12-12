---
description: 'En savoir plus sur : erreur du compilateur C3461'
title: Erreur du compilateur C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: 6158e0d6d38290a1925beba89fe77cba8f01c87b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113491"
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
