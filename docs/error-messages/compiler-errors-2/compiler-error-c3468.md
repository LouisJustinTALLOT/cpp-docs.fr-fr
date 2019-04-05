---
title: Erreur du compilateur C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: e3870fa21e2b4a932937edd49091980406a5ff0d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777230"
---
# <a name="compiler-error-c3468"></a>Erreur du compilateur C3468

'type' : vous ne pouvez transférer un type que vers un assembly :

'`file`' n’est pas un assembly

Seuls les types contenus dans un assembly peuvent être transférés.

Pour plus d’informations, consultez [transfert de Type (C++ / c++ / CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant crée un module.

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3468.

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```