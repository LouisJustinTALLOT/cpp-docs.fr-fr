---
title: Erreur du compilateur C2516
ms.date: 11/04/2016
f1_keywords:
- C2516
helpviewer_keywords:
- C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
ms.openlocfilehash: 2114ad048c2061b81f223c86536f23737bdf43fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540060"
---
# <a name="compiler-error-c2516"></a>Erreur du compilateur C2516

'name' : n’est pas une classe de base juridique

La classe est dérivée d’un nom de type défini par un `typedef` instruction.

L’exemple suivant génère l’erreur C2516 :

```
// C2516.cpp
typedef unsigned long ulong;
class C : public ulong {}; // C2516
```