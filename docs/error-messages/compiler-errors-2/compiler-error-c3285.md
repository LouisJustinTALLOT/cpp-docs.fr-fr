---
title: Erreur du compilateur C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: 6bc211fb2394a9a2989702c13e19bd63ea8a5ad7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444627"
---
# <a name="compiler-error-c3285"></a>Erreur du compilateur C3285

Une instruction for each ne peut pas fonctionner sur des variables de type 'type'

L’instruction `for each` répète un groupe d’instructions incorporées pour chaque élément d’un tableau ou d’une collection d’objets.

Pour plus d'informations, voir [for each, in](../../dotnet/for-each-in.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3285.

```
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```