---
title: Avertissement du compilateur (niveau 4) C4960
ms.date: 11/04/2016
f1_keywords:
- C4960
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
ms.openlocfilehash: 286d3a1953c6c6badf15b712feac99afafe8b0a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198118"
---
# <a name="compiler-warning-level-4-c4960"></a>Avertissement du compilateur (niveau 4) C4960

'function' est trop grand pour être profilé

Quand vous avez utilisé [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée avec une fonction comprenant plus de 65 535 instructions. Une fonction de cette taille n’est pas disponible pour les optimisations guidées par profil.

Pour résoudre cet avertissement, réduisez la taille de la fonction.
