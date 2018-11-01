---
title: Erreur du compilateur C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: dad6a64f145c3d49d3b43044ea76a11d35827943
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460539"
---
# <a name="compiler-error-c2833"></a>Erreur du compilateur C2833

'operator opérateur' n’est pas un opérateur ou type reconnu

Le mot `operator` doit être suivie d’un opérateur que vous souhaitez remplacer ou d’un type à convertir.

Pour obtenir la liste des opérateurs que vous pouvez définir dans un type managé, consultez [opérateurs définis par l’utilisateur](../../dotnet/user-defined-operators-cpp-cli.md).

L’exemple suivant génère l’erreur C2833 :

```
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```