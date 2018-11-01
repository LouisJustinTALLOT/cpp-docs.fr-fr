---
title: Erreur du compilateur C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: 185bd35bb732f592c75912fe69d4491252fe9d0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476113"
---
# <a name="compiler-error-c3468"></a>Erreur du compilateur C3468

'type' : vous ne pouvez transférer un type que vers un assembly :

'`file`' n’est pas un assembly

Seuls les types contenus dans un assembly peuvent être transférés.

Pour plus d’informations, consultez [transfert de Type (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).

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