---
description: 'En savoir plus sur : erreur du compilateur C2665'
title: Erreur du compilateur C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 784fe5ef0f24cd9e5fba99465d46f378b2b517fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210801"
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
