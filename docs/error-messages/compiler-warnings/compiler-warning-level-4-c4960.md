---
title: Avertissement du compilateur (niveau 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: ff4a9b3d78a108a45abb18c22049b104e630bf15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280241"
---
# <a name="compiler-warning-level-4-c4960"></a>Avertissement du compilateur (niveau 4) C4960

'function' est trop grand pour être profilé

Quand vous avez utilisé [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée avec une fonction comprenant plus de 65 535 instructions. Une fonction de cette taille n’est pas disponible pour les optimisations guidées par profil.

Pour résoudre cet avertissement, réduisez la taille de la fonction.