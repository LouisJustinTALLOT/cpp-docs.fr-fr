---
title: Erreur du compilateur C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 2c8164cad25d68ee61ff9fed7170482d5dfc9505
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474787"
---
# <a name="compiler-error-c2530"></a>Erreur du compilateur C2530

'identificateur' : les références doivent être initialisées

Vous devez initialiser une référence lorsqu’il a été déclaré, sauf si elle est déjà déclarée :

- Avec le mot clé [extern](../../cpp/using-extern-to-specify-linkage.md).

- En tant que membre d’une classe, une structure ou une union (et il est initialisé dans le constructeur).

- En tant que paramètre dans une définition ou déclaration de fonction.

- En tant que type de retour d’une fonction.

L’exemple suivant génère l’erreur C2530 :

```
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```