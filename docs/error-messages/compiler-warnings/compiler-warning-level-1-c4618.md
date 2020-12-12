---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4618'
title: Avertissement du compilateur (niveau 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: 824a55dab68fe45a94cacb1924bed46b87b7c0eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208682"
---
# <a name="compiler-warning-level-1-c4618"></a>Avertissement du compilateur (niveau 1) C4618

les paramètres pragma comportaient une chaîne vide ; pragma ignoré

Une chaîne NULL a été fournie en tant qu’argument à un **#pragma**.

Le pragma a été traité sans l’argument.

L’exemple suivant génère l’C4618 :

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```
