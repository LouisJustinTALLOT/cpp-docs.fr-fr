---
title: Avertissement du compilateur (niveau 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1948342e1ff97c38ca3a44694dc7e7d399d96825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568039"
---
# <a name="compiler-warning-level-1-c4953"></a>Avertissement du compilateur (niveau 1) C4953

> Inlinee '*fonction*' a été modifié depuis le profil de données ont été collectées, les données de profil non utilisées

Quand vous avez utilisé [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée qui a été recompilé après `/LTCG:PGINSTRUMENT` et qui possède une fonction (*function*) qui a été modifiée et dans laquelle des séries de tests existantes ont identifié la fonction comme candidate à l’incorporation (inlining). Toutefois, en raison de la recompilation du module, la fonction ne sera plus candidate à l’incorporation (inlining).

Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, exécutez `/LTCG:PGINSTRUMENT`, relancez toutes les séries de tests, puis exécutez `/LTCG:PGOPTIMIZE`.

Si `/LTCG:PGOPTIMIZE` avait été utilisé, cet avertissement aurait été remplacé par une erreur.