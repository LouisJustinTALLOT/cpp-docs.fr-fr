---
title: Erreur du compilateur C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745042"
---
# <a name="compiler-error-c2390"></a>Erreur du compilateur C2390

'identificateur' : classe de stockage incorrecte’specifier'

La classe de stockage n’est pas valide pour l’identificateur de portée globale. La classe de stockage par défaut est utilisée à la place de la classe non valide.

Solutions possibles :

- Si l’identificateur est une fonction, déclarez-le avec un stockage `extern`.

- Si l’identificateur est un paramètre formel ou une variable locale, déclarez-le avec le stockage automatique.

- Si l’identificateur est une variable globale, déclarez-le sans classe de stockage (stockage automatique).

## <a name="example"></a>Exemple

- L’exemple suivant génère l’C2390 :

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
