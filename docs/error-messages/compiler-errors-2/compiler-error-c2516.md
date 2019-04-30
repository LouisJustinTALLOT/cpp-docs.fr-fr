---
title: Erreur du compilateur C2516
ms.date: 11/04/2016
f1_keywords:
- C2516
helpviewer_keywords:
- C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
ms.openlocfilehash: 2114ad048c2061b81f223c86536f23737bdf43fb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344760"
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