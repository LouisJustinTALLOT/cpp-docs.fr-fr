---
title: Erreur du compilateur C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: c1467a3c67cccf28cc6b9bd0f987fe77b8da8988
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757876"
---
# <a name="compiler-error-c2833"></a>Erreur du compilateur C2833

'operator opérateur’n’est pas un opérateur ou un type reconnu

Le mot `operator` doit être suivi d’un opérateur que vous souhaitez substituer ou d’un type que vous souhaitez convertir.

Pour obtenir la liste des opérateurs que vous pouvez définir dans un type managé, consultez [opérateurs définis par l’utilisateur](../../dotnet/user-defined-operators-cpp-cli.md).

L’exemple suivant génère l’C2833 :

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
