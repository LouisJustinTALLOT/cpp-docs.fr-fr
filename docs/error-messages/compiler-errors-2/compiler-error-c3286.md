---
title: Erreur du compilateur C3286 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3286
dev_langs:
- C++
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ea2a6dcccd6de6d4fc3081106123f4ab37f71a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052911"
---
# <a name="compiler-error-c3286"></a>Erreur du compilateur C3286

> «*spécificateur*' : une variable d’itération ne peut pas avoir de spécificateurs de classe de stockage

Une classe de stockage ne peut pas être spécifiée sur une variable d’itération. Pour plus d’informations, consultez [classes de stockage (C++)](../../cpp/storage-classes-cpp.md) et [pour chacun, dans](../../dotnet/for-each-in.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3286 et illustre également l’utilisation correcte.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```