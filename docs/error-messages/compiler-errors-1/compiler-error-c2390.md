---
title: Erreur du compilateur C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 89f6ebb02326413e8dca67d333e555321da4e645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595870"
---
# <a name="compiler-error-c2390"></a>Erreur du compilateur C2390

'identificateur' : classe de stockage incorrecte 'spécificateur'

La classe de stockage n’est pas valide pour l’identificateur de portée globale. La classe de stockage par défaut est utilisée à la place de la classe non valide.

Solutions possibles :

- Si l’identificateur est une fonction, déclarez-le avec `extern` stockage.

- Si l’identificateur est un paramètre formel ou une variable locale, déclarez-le à l’aide du stockage automatique.

- Si l’identificateur est une variable globale, déclarez-le sans classe de stockage (stockage automatique).

## <a name="example"></a>Exemple

- L’exemple suivant génère l’erreur C2390 :

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```