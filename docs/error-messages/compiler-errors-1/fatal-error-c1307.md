---
title: Erreur irrécupérable C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552267"
---
# <a name="fatal-error-c1307"></a>Erreur irrécupérable C1307

le programme a été modifié depuis que les données du profil ont été recueillies

Lorsque vous utilisez [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), l’éditeur de liens a détecté un module d’entrée qui a été recompilé après/LTCG : PGINSTRUMENT et que le module a été remplacé par le point où les données de profil existantes ne sont plus pertinentes. Par exemple, si le graphique des appels est modifié dans le module recompilé, le compilateur générera C1307.

Pour résoudre cette erreur, exécutez/LTCG : PGINSTRUMENT, restauration par progression de toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE. Si vous ne pouvez pas exécuter/LTCG : PGINSTRUMENT et restauration par progression que toutes les test s’exécute, utilisez/LTCG : PGUPDATE au lieu / LTCG : PGOPTIMIZE pour créer l’image optimisée.