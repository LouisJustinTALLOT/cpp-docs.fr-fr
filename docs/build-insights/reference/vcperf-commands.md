---
title: 'Référence: commandes de vcperf'
description: Référence pour l’utilitaire de commande vcperf.exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323249"
---
# <a name="reference-vcperf-commands"></a>Référence: commandes de vcperf

::: moniker range="<=vs-2017"

Les outils build Insights sont disponibles dans Visual Studio 2019. Pour voir la documentation de cette version, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range="vs-2019"

Cet article répertorie et décrit les commandes disponibles en *vcperf.exe*, et comment les utiliser.

## <a name="commands-to-start-and-stop-traces"></a>Commandes de commencer et d’arrêter les traces

*IMPORTANT : les commandes suivantes exigent toutes des privilèges administratifs.*

| Option           | Arguments et description |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Dit *vcperf.exe* de commencer une trace sous le nom de session donné. Il ne peut y avoir qu’une seule session active à la fois sur une machine donnée. <br/><br/> Si `/nocpusampling` l’option est *spécifiée, vcperf.exe* ne recueille pas d’échantillons de processeur. Il empêche l’utilisation de la vue d’utilisation du processeur (échantillonné) dans Windows Performance Analyzer, mais rend les traces collectées plus petites. <br/><br/> Une fois le tracé commencé, *vcperf.exe* revient immédiatement. Les événements sont collectés à l’échelle du système pour tous les processus fonctionnant sur la machine. Cela signifie que vous n’avez pas besoin de construire votre projet à partir de la même invite de commande que celui que vous avez utilisé pour exécuter *vcperf.exe*. Par exemple, vous pouvez construire votre projet à partir de Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Arrête la trace identifiée par le nom de la session donnée. Exécute une étape post-traitement sur la trace pour générer un fichier visible dans Windows Performance Analyzer (WPA). Pour obtenir la meilleure expérience de visionnement, utilisez une version de WPA qui inclut l’add-in build Insights. Pour plus d’informations, voir [Démarrer avec CMD Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Le `<outputFile.etl>` paramètre précise où enregistrer le fichier de sortie. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Arrête la trace identifiée par le nom de la session donnée et écrit les données brutes non traitées dans le fichier de sortie spécifié. Le fichier qui en résulte n’est pas destiné à être consulté dans WPA. <br/><br/> L’étape post-traitement `/stop` impliquée dans la commande peut parfois être longue. Vous pouvez `/stopnoanalyze` utiliser la commande pour retarder cette étape post-traitement. Utilisez `/analyze` la commande lorsque vous êtes prêt à produire un fichier visible dans Windows Performance Analyzer. |

## <a name="miscellaneous-commands"></a>Commandes diverses

| Option     | Arguments et description |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Accepte un fichier de traces brutes produit par la `/stopnoanalyze` commande. Exécute une étape post-traitement sur cette trace pour générer un fichier visible dans Windows Performance Analyzer. Pour obtenir la meilleure expérience de visionnement, utilisez une version de WPA qui inclut l’add-in build Insights. Pour plus d’informations, voir [Démarrer avec CMD Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Voir aussi

[Commencez avec les aperçus de construction de CMD](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Tutorial: Windows Performance Analyzer basics](/cpp/build-insights/tutorials/wpa-basics)\
[Référence: Vues d’analyseur de performance Windows](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
