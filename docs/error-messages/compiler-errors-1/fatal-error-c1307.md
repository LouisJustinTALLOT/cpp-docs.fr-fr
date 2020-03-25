---
title: Erreur irrécupérable C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203344"
---
# <a name="fatal-error-c1307"></a>Erreur irrécupérable C1307

le programme a été modifié depuis que les données du profil ont été recueillies

Lors de l’utilisation de [/LTCG : PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), l’éditeur de liens a détecté un module d’entrée qui a été recompilé après/LTCG : PGINSTRUMENT et que le module a été remplacé par le point où les données de profil existantes ne sont plus pertinentes. Par exemple, si le graphique des appels a changé dans le module recompilé, le compilateur génère C1307.

Pour résoudre cette erreur, exécutez/LTCG : PGINSTRUMENT, relancez toutes les séries de tests et exécutez/LTCG : PGOPTIMIZE. Si vous ne pouvez pas exécuter/LTCG : PGINSTRUMENT et rétablir toutes les séries de tests, utilisez/LTCG : PGUPDATE au lieu de/LTCG : PGOPTIMIZE pour créer l’image optimisée.
