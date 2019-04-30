---
title: Avertissement du compilateur (niveau 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: b8f24df7465525b24ecd3871447bd873889b1e23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406390"
---
# <a name="compiler-warning-level-1-c4618"></a>Avertissement du compilateur (niveau 1) C4618

les paramètres pragma comportaient une chaîne vide. pragma ignoré

Une chaîne null a été spécifiée en tant qu’argument à un **#pragma**.

Le pragma a été traité sans l’argument.

L’exemple suivant génère l’erreur C4618 :

```
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```