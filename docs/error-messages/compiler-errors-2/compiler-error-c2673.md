---
description: 'En savoir plus sur : erreur du compilateur C2673'
title: Erreur du compilateur C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 1b7d634e4c1b62860a648ef5327ffd8b888c7d7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282066"
---
# <a name="compiler-error-c2673"></a>Erreur du compilateur C2673

'fonction' : les fonctions globales n’ont pas de pointeurs’This'

Une fonction globale a tenté d’accéder à **`this`** .

L’exemple suivant génère l’C2673 :

```cpp
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```
