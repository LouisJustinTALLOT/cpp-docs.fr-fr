---
title: Erreur irrécupérable C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 35b94e6cea177121c38d06706b42437ec610c38a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587102"
---
# <a name="fatal-error-c1021"></a>Erreur irrécupérable C1021

Commande de préprocesseur non valide 'chaîne'

`string` n’est pas une [directive de préprocesseur](../../preprocessor/preprocessor-directives.md)valide. Pour résoudre cette erreur, utilisez un nom de préprocesseur valide pour `string`.

L’exemple suivant génère l’erreur C1021 :

```
// C1021.cpp
#BadPreProcName    // C1021 delete line
```