---
title: Erreur du compilateur C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 95ca5ea846f9cd45bdb1e9706ae377589d37a285
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756017"
---
# <a name="compiler-error-c2665"></a>Erreur du compilateur C2665

'fonction' : aucune des surcharges nombre1 ne peut convertir le paramètre nombre2 à partir du type’type'

Un paramètre de la fonction surchargée ne peut pas être converti en type requis.  Solutions possibles :

- Fournissez un opérateur de conversion.

- Utilisez la conversion explicite.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2665.

```cpp
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
