---
description: 'En savoir plus sur : erreur irrécupérable C1307'
title: Erreur irrécupérable C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 235d51f272669ba3b205eea5c3703b40dc1e9077
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177885"
---
# <a name="fatal-error-c1307"></a>Erreur irrécupérable C1307

le programme a été modifié depuis que les données du profil ont été recueillies

Lors de l’utilisation de [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), l’éditeur de liens a détecté un module d’entrée qui a été recompilé après/LTCG : PGINSTRUMENT et que le module a été remplacé par le point où les données de profil existantes ne sont plus pertinentes. Par exemple, si le graphique des appels a changé dans le module recompilé, le compilateur génère C1307.

Pour résoudre cette erreur, exécutez/LTCG : PGINSTRUMENT, relancez toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE. Si vous ne pouvez pas exécuter/LTCG : PGINSTRUMENT et rétablir toutes les séries de tests, utilisez/LTCG : PGUPDATE au lieu de/LTCG : PGOPTIMIZE pour créer l’image optimisée.
