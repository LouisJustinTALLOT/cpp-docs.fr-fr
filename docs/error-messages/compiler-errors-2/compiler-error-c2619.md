---
description: 'En savoir plus sur : erreur du compilateur C2619'
title: Erreur du compilateur C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: 2ca9a8379901703299e89e71671ec0270c1ff1e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123542"
---
# <a name="compiler-error-c2619"></a>Erreur du compilateur C2619

'identificateur' : un membre de données statique n'est pas autorisé dans un struct ou union anonyme

Un membre d’un struct ou d’une Union anonyme est déclaré **`static`** .

L'exemple suivant génère l'erreur C2619 et montre comment résoudre le problème en supprimant le mot clé static.

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```
