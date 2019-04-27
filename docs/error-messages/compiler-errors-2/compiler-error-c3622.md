---
title: Erreur du compilateur C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222007"
---
# <a name="compiler-error-c3622"></a>Erreur du compilateur C3622

'classe' : une classe déclarée comme 'mot_clé' ne peut pas être instanciée.

Une tentative a été faite pour instancier une classe marquée en tant que [abstraite](../../extensions/abstract-cpp-component-extensions.md). Une classe marquée en tant que `abstract` peut être une classe de base, mais elle ne peut pas être instanciée.

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
