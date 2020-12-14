---
description: 'En savoir plus sur : erreur du compilateur C2013'
title: Erreur du compilateur C2013
ms.date: 11/04/2016
f1_keywords:
- C2013
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
ms.openlocfilehash: 2f883c24be5e02c58553ca6f7abe4f588ae8a2da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220966"
---
# <a name="compiler-error-c2013"></a>Erreur du compilateur C2013

'>' manquant

Il manque un signe supérieur de fermeture à une directive `#include` . Ajoutez le signe supérieur de fermeture pour corriger l’erreur.

L’exemple suivant génère l’erreur C2013 :

```cpp
// C2013.cpp
#include <stdio.h    // C2013
```

Solution possible :

```cpp
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```
