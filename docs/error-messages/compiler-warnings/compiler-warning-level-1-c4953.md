---
title: Avertissement du compilateur (niveau 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 46f07227b5df62938cc51a7be4cf4f3595a0d947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174517"
---
# <a name="compiler-warning-level-1-c4953"></a>Avertissement du compilateur (niveau 1) C4953

> '*Fonction*'inline a été modifié depuis la collecte des données de profil, données de profil non utilisées

Quand vous avez utilisé [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée qui a été recompilé après `/LTCG:PGINSTRUMENT` et qui possède une fonction (*function*) qui a été modifiée et dans laquelle des séries de tests existantes ont identifié la fonction comme candidate à l’incorporation (inlining). Toutefois, en raison de la recompilation du module, la fonction ne sera plus candidate à l’incorporation (inlining).

Cet avertissement est à caractère informatif. Pour résoudre cet avertissement, exécutez `/LTCG:PGINSTRUMENT`, relancez toutes les séries de tests, puis exécutez `/LTCG:PGOPTIMIZE`.

Si `/LTCG:PGOPTIMIZE` avait été utilisé, cet avertissement aurait été remplacé par une erreur.
