---
title: Erreur du compilateur C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: f22a01c5c26a55a5908c20f3b123971fadd43544
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742812"
---
# <a name="compiler-error-c3468"></a>Erreur du compilateur C3468

'type' : vous ne pouvez transférer un type que vers un assembly :

'`file`' n’est pas un assembly

Seuls les types contenus dans un assembly peuvent être transférés.

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un module.

```cpp
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

L’exemple suivant génère l’erreur C3468.

```cpp
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```
