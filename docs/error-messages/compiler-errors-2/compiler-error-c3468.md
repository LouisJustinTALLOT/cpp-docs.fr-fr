---
description: 'En savoir plus sur : erreur du compilateur C3468'
title: Erreur du compilateur C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: 7e6d58e012baa0163f33867069e7250da61177b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315736"
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
