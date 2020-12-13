---
description: 'En savoir plus sur : erreur du compilateur C3286'
title: Erreur du compilateur C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 38e3b405f9093baa266cf56e5bfc7f44c7566206
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339222"
---
# <a name="compiler-error-c3286"></a>Erreur du compilateur C3286

> '*specifier*' : une variable d’itération ne peut pas avoir de spécificateurs de classe de stockage

Une classe de stockage ne peut pas être spécifiée sur une variable d’itération. Pour plus d’informations, consultez [classes de stockage (C++)](../../cpp/storage-classes-cpp.md) et [pour chaque, dans](../../dotnet/for-each-in.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3286 et affiche également l’utilisation correcte.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
