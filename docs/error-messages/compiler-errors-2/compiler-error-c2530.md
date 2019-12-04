---
title: Erreur du compilateur C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737125"
---
# <a name="compiler-error-c2530"></a>Erreur du compilateur C2530

'identificateur' : les références doivent être initialisées

Vous devez initialiser une référence lorsqu’elle a été déclarée, sauf si elle est déjà déclarée :

- Avec le mot clé [extern](../../cpp/using-extern-to-specify-linkage.md).

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
