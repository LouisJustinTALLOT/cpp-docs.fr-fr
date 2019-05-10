---
title: Avertissement du compilateur (niveau 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: c68e84daa2ca1aa023123203bb851e92758f9e40
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447677"
---
# <a name="compiler-warning-level-1-c4237"></a>Avertissement du compilateur (niveau 1) C4237

mot clé 'mot_clé' n’est pas encore pris en charge, mais réservé pour une utilisation ultérieure

Un mot clé dans le C++ spécification n’est pas implémentée dans Microsoft C++ compilateur, mais le mot clé n’est pas disponible comme symbole défini par l’utilisateur.

L’exemple suivant génère l’erreur C4237 :

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```