---
title: Bien démarrer avec C++ Build Insights
description: Une vue d’ensemble de C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332005"
---
# <a name="get-started-with-c-build-insights"></a>Bien démarrer avec C++ Build Insights

::: moniker range="<=vs-2017"

Les C++ outils de génération Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights est un ensemble d’outils qui offre une meilleure visibilité de la chaîne d’outils C++ Microsoft Visual (MSVC). Les outils recueillent des données C++ sur vos builds et les présentent dans un format qui peut vous aider à répondre à des questions courantes, telles que :

- Mes Builds sont-elles suffisamment parallélisée ?
- Que dois-je inclure dans mon en-tête précompilé (PCH) ?
- S’agit-il d’un goulot d’étranglement spécifique, je dois me concentrer sur l’augmentation de la vitesse de génération ?

Les principaux composants de cette technologie sont les suivants :

- *vcperf. exe*, un utilitaire de ligne de commande que vous pouvez utiliser pour collecter les traces de vos builds,
- une extension Windows Performance Analyzer (WPA) qui vous permet d’afficher les traces de build dans WPA, et
- le C++ Kit de développement logiciel (SDK) de build Insights, un kit de développement logiciel pour C++ la création de vos propres outils qui consomment des données de build Insights.

Cliquez sur les liens ci-dessous pour commencer rapidement à utiliser ces composants :

[Didacticiel : vcperf et Windows performance analyzer](tutorials/vcperf-and-wpa.md)\
Découvrez Comment collecter des traces de génération pour C++ vos projets et comment les afficher dans WPA.

[Didacticiel : notions de base](tutorials/wpa-basics.md) sur les performances de Windows\
Découvrez des conseils WPA utiles pour analyser vos suivis de Build.

\ du [Kit de développement logiciel (SDK) Build Insights C++ ](reference/sdk/overview.md)
Vue d’ensemble du C++ Kit de développement logiciel (SDK) Build Insights.

::: moniker-end
