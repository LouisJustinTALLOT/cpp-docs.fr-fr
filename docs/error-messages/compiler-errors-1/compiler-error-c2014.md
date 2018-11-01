---
title: Erreur du compilateur C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 58cf9867a9e36b304ab9da79084bc01dff453892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462658"
---
# <a name="compiler-error-c2014"></a>Erreur du compilateur C2014

commande de préprocesseur doit commencer comme premier espace blanc

Le `#` signe d’une directive de préprocesseur doit être le premier caractère d’une ligne qui n’est pas un espace blanc.

L’exemple suivant génère l’erreur C2014 :

```
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

Solution possible :

```
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```