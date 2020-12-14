---
description: 'En savoir plus sur : erreur du compilateur C2530'
title: Erreur du compilateur C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 07980fb6d87b4e84bc0b253ccd317eba02fa81af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258107"
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
