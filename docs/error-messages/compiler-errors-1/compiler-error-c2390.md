---
title: Erreur du compilateur C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 48012c0fe31b2017cad29cc98992c9b1121efa7c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221183"
---
# <a name="compiler-error-c2390"></a>Erreur du compilateur C2390

'identificateur' : classe de stockage incorrecte’specifier'

La classe de stockage n’est pas valide pour l’identificateur de portée globale. La classe de stockage par défaut est utilisée à la place de la classe non valide.

Solutions possibles :

- Si l’identificateur est une fonction, déclarez-la avec **`extern`** Storage.

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
