---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4953'
title: Avertissement du compilateur (niveau 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1f10f757297bd4b0e71ec5246024a3ce7a313689
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327943"
---
# <a name="compiler-warning-level-1-c4953"></a>Avertissement du compilateur (niveau 1) C4953

> '*Fonction*'inline a été modifié depuis la collecte des données de profil, données de profil non utilisées

Quand vous avez utilisé [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée qui a été recompilé après `/LTCG:PGINSTRUMENT` et qui possède une fonction (*function*) qui a été modifiée et dans laquelle des séries de tests existantes ont identifié la fonction comme candidate à l’incorporation (inlining). Toutefois, en raison de la recompilation du module, la fonction ne sera plus candidate à l’incorporation (inlining).

Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, exécutez `/LTCG:PGINSTRUMENT`, relancez toutes les séries de tests, puis exécutez `/LTCG:PGOPTIMIZE`.

Si `/LTCG:PGOPTIMIZE` avait été utilisé, cet avertissement aurait été remplacé par une erreur.
