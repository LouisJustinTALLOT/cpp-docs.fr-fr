---
title: Avertissement du compilateur (niveaux 2 et 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 9b6fb56045d53cd18689f3903bb3d7a08c3d4e4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198002"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Avertissement du compilateur (niveaux 2 et 3) C4008

'identifier' : 'attribute' attribut ignoré

Le compilateur a ignoré l’attribut `__fastcall`, **static**ou **inline** pour une fonction (avertissement de niveau 3) ou des données (avertissement de niveau 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Attribut`__fastcall` avec des données.

1. Attribut**static** ou **inline** avec la fonction **main** .
