---
title: Erreur du compilateur C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: a6ffcb13d04f3c7c5ac62e147a2b6b2b305e11e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218167"
---
# <a name="compiler-error-c2833"></a>Erreur du compilateur C2833

> 'operator *opérateur-Name*'n’est pas un opérateur ou un type reconnu

Le mot **`operator`** doit être suivi d’un *nom d’opérateur* que vous souhaitez substituer ou d’un type que vous souhaitez convertir.

Pour obtenir la liste des opérateurs que vous pouvez définir dans un type managé, consultez [opérateurs définis par l’utilisateur](../../dotnet/user-defined-operators-cpp-cli.md).

L’exemple suivant génère l’C2833 :

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
