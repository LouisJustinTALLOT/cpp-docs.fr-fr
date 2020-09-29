---
title: Erreur du compilateur C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 4eca5579f6bf132452a813d8dd99193df5f76b92
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500545"
---
# <a name="compiler-error-c2530"></a>Erreur du compilateur C2530

'identificateur' : les références doivent être initialisées

Vous devez initialiser une référence lorsqu’elle a été déclarée, sauf si elle est déjà déclarée :

- Avec le mot clé [extern](../../cpp/extern-cpp.md).

- En tant que membre d’une classe, d’une structure ou d’une Union (et il est initialisé dans le constructeur).

- En tant que paramètre dans une déclaration ou une définition de fonction.

- Comme type de retour d’une fonction.

L’exemple suivant génère l’C2530 :

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
