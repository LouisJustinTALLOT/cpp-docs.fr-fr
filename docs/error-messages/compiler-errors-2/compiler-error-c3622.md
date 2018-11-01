---
title: Erreur du compilateur C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518090"
---
# <a name="compiler-error-c3622"></a>Erreur du compilateur C3622

'classe' : une classe déclarée comme 'mot_clé' ne peut pas être instanciée.

Une tentative a été faite pour instancier une classe marquée en tant que [abstraite](../../windows/abstract-cpp-component-extensions.md). Une classe marquée en tant que `abstract` peut être une classe de base, mais elle ne peut pas être instanciée.

## <a name="example"></a>Exemple

L’exemple suivant génère C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
