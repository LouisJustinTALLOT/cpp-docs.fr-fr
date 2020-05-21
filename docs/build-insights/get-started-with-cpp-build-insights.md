---
title: Bien démarrer avec C++ Build Insights
description: Une vue d’ensemble de C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28d7e0758ea521af424129c546297fc97e3d6659
ms.sourcegitcommit: 8c8ed02a6f3bcb5ee008e3fe30ba7595d7c4c922
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83759223"
---
# <a name="get-started-with-c-build-insights"></a>Bien démarrer avec C++ Build Insights

::: moniker range="<=vs-2017"

Les outils C++ Build Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights est un ensemble d’outils qui offre une meilleure visibilité de la chaîne d’outils Microsoft Visual C++ (MSVC). Les outils recueillent des données sur vos builds C++ et les présentent dans un format qui peut vous aider à répondre à des questions courantes, telles que :

- Mes Builds sont-elles suffisamment parallélisée ?
- Que dois-je inclure dans mon en-tête précompilé (PCH) ?
- S’agit-il d’un goulot d’étranglement spécifique, je dois me concentrer sur l’augmentation de la vitesse de génération ?

Les principaux composants de cette technologie sont les suivants :

- *vcperf. exe*, un utilitaire de ligne de commande que vous pouvez utiliser pour collecter les traces de vos builds,
- une extension Windows Performance Analyzer (WPA) qui vous permet d’afficher les traces de build dans WPA, et
- le kit de développement logiciel (SDK) C++ Build Insights, un kit de développement logiciel pour la création de vos propres outils qui consomment des données de build Insights C++.

## <a name="documentation-sections"></a>Sections de la documentation

[Didacticiel : vcperf et analyseur de performances Windows](tutorials/vcperf-and-wpa.md)\
Découvrez Comment collecter des traces de génération pour vos projets C++ et comment les afficher dans WPA.

[Didacticiel : principes de base des performances Windows](tutorials/wpa-basics.md)\
Découvrez des conseils WPA utiles pour analyser vos suivis de Build.

[Kit de développement logiciel (SDK) C++ Build Insights](reference/sdk/overview.md)\
Vue d’ensemble du kit de développement logiciel (SDK) C++ Build Insights.

## <a name="articles"></a>Articles

Lisez ces articles sur le blog officiel de l’équipe C++ pour plus d’informations sur C++ Build Insights :

[Présentation de C++ Build Insights](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[Analyser vos builds par programmation avec le kit de développement logiciel (SDK) C++ Build Insights](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[Recherche des goulots d’étranglement de build avec C++ Build Insights](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[Builds plus rapides avec des suggestions PCH de C++ Build Insights](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end
