---
title: Erreur du compilateur C2530 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f41f9ec64e2074ed5e0cd2654f2b6bfec886bc07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103184"
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