---
title: Fonctions non prototypées
ms.date: 11/04/2016
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
ms.openlocfilehash: 38207be6111dadc338593e55b683b88e0480e1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633426"
---
# <a name="unprototyped-functions"></a>Fonctions non prototypées

Pour les fonctions pas entièrement prototypées, l’appelant passe les valeurs entières en tant que nombres entiers et des valeurs à virgule flottante double précision. Pour les valeurs à virgule flottante, le Registre entier et le Registre à virgule flottante contiendra la valeur float si l’appelé attend la valeur dans les registres d’entiers.

```
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)