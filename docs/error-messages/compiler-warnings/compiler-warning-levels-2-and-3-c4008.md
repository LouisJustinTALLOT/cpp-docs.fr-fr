---
description: 'En savoir plus sur : avertissement du compilateur (niveaux 2 et 3) C4008'
title: Avertissement du compilateur (niveaux 2 et 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 6f13ef60efabeaffe549189431aa04c65a12cbe5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234421"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Avertissement du compilateur (niveaux 2 et 3) C4008

'identifier' : 'attribute' attribut ignoré

Le compilateur a ignoré **`__fastcall`** l' **`static`** attribut, ou **`inline`** pour une fonction (avertissement de niveau 3) ou des données (avertissement de niveau 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. **`__fastcall`** attribut avec des données.

1. **`static`** ou **`inline`** attribut avec la fonction **main** .
