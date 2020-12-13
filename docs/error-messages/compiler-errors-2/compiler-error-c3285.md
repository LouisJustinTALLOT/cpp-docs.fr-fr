---
description: 'En savoir plus sur : erreur du compilateur C3285'
title: Erreur du compilateur C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: d5b57b878ed47118e1857558b9d633bb5ef7286c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339330"
---
# <a name="compiler-error-c3285"></a>Erreur du compilateur C3285

Une instruction for each ne peut pas fonctionner sur des variables de type 'type'

L’instruction `for each` répète un groupe d’instructions incorporées pour chaque élément d’un tableau ou d’une collection d’objets.

Pour plus d'informations, voir [for each, in](../../dotnet/for-each-in.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3285.

```cpp
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```
