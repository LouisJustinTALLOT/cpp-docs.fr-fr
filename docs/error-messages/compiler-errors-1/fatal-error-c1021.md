---
title: Erreur irrécupérable C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 861e768563cf737d6925d5753d80cd9269eff4fe
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756888"
---
# <a name="fatal-error-c1021"></a>Erreur irrécupérable C1021

Commande de préprocesseur non valide 'chaîne'

`string` n’est pas une [directive de préprocesseur](../../preprocessor/preprocessor-directives.md)valide. Pour résoudre cette erreur, utilisez un nom de préprocesseur valide pour `string`.

L’exemple suivant génère l’erreur C1021 :

```cpp
// C1021.cpp
#BadPreProcName    // C1021 delete line
```
