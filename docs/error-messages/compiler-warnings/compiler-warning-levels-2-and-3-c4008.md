---
title: Compilateur avertissement (niveaux 2 et 3) C4008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd052b8dd6a0b70dd90ca076d0085675b33dc621
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091177"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Avertissement du compilateur (niveaux 2 et 3) C4008

'identifier' : 'attribute' attribut ignoré

Le compilateur a ignoré l’attribut `__fastcall`, **static**ou **inline** pour une fonction (avertissement de niveau 3) ou des données (avertissement de niveau 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Attribut`__fastcall` avec des données.

1. Attribut**static** ou **inline** avec la fonction **main** .