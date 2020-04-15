---
title: Bien démarrer avec C++ Build Insights
description: Un aperçu de haut niveau de C ' Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325712"
---
# <a name="get-started-with-c-build-insights"></a>Bien démarrer avec C++ Build Insights

::: moniker range="<=vs-2017"

Les outils build Insights sont disponibles dans Visual Studio 2019. Pour voir la documentation de cette version, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range="vs-2019"

Build Insights est une collection d’outils qui offre une visibilité accrue dans la chaîne d’outils Microsoft Visual CMD (MSVC). Les outils recueillent des données sur votre CMD et les présentent dans un format qui peut vous aider à répondre à des questions courantes, comme :

- Mes builds sont-elles suffisamment parallélisées ?
- Que dois-je inclure dans mon en-tête pré-compilé (PCH)?
- Y a-t-il un goulot d’étranglement spécifique sur qui je devrais me concentrer pour augmenter mes vitesses de construction?

Les principaux composants de cette technologie sont les principaux éléments :

- *vcperf.exe*, un utilitaire de ligne de commande que vous pouvez utiliser pour recueillir des traces pour vos builds,
- une extension d’analyseur de performance Windows (WPA) qui vous permet de visualiser des traces de construction dans WPA, et
- le CMD Build Insights SDK, un kit de développement logiciel pour la création de vos propres outils qui consomment les données de construction de CMD Build Insights.

Cliquez sur les liens ci-dessous pour commencer rapidement avec ces composants:

[Tutorial: vcperf et Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Découvrez comment collecter des traces de construction pour vos projets CMD et comment les voir dans WPA.

[Tutorial: Windows Performance Basics](tutorials/wpa-basics.md)\
Découvrez des conseils WPA utiles pour analyser vos traces de construction.

[Construire des aperçus SDK](reference/sdk/overview.md)\
Un aperçu de la SDK Build Insights.

::: moniker-end
