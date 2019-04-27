---
title: Avertissement du compilateur (niveau 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: 04fcb99e1dd1e348716e25affb22b54079d53aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207381"
---
# <a name="compiler-warning-level-1-c4237"></a>Avertissement du compilateur (niveau 1) C4237

mot clé 'mot_clé' n’est pas encore pris en charge, mais réservé pour une utilisation ultérieure

Un mot clé dans la spécification C++ n’est pas implémenté dans le compilateur Visual C++, mais le mot clé n’est pas disponible comme symbole défini par l’utilisateur.

L’exemple suivant génère l’erreur C4237 :

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```