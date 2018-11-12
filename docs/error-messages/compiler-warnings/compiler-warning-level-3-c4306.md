---
title: Avertissement du compilateur (niveau 3) C4306
ms.date: 08/27/2018
f1_keywords:
- C4306
helpviewer_keywords:
- C4306
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
ms.openlocfilehash: 78ec291b555838b1af63287e3d24fdb809afd7c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582024"
---
# <a name="compiler-warning-level-3-c4306"></a>Avertissement du compilateur (niveau 3) C4306

> «*identificateur*' : conversion de '*type1*'en'*type2*' d’une taille supérieure

L’identificateur est de type converti en un pointeur de plus grande. Les bits de poids fort non remplis du nouveau type seront remplis de zéros.

Cet avertissement peut indiquer une conversion non désirée. Le pointeur résultant n’est peut-être pas valid.