---
title: Erreur du compilateur C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757395"
---
# <a name="compiler-error-c2014"></a>Erreur du compilateur C2014

la commande de préprocesseur doit commencer comme premier espace non blanc

Le signe `#` d’une directive de préprocesseur doit être le premier caractère d’une ligne qui n’est pas un espace blanc.

L’exemple suivant génère l’C2014 :

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

Solution possible :

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
