---
description: 'En savoir plus sur : erreur du compilateur C2389'
title: Erreur du compilateur C2389
ms.date: 11/04/2016
f1_keywords:
- C2389
helpviewer_keywords:
- C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
ms.openlocfilehash: 1f9d34be47376564bf7c6fc221cf6f5b01e7850f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123966"
---
# <a name="compiler-error-c2389"></a>Erreur du compilateur C2389

'opérateur' : opérande 'nullptr' non conforme

**`nullptr`** ne peut pas être un opérande.

L’exemple suivant génère l’erreur C2389 :

```cpp
// C2389.cpp
// compile with: /clr
int main() {
   throw nullptr;   // C2389
}
```
