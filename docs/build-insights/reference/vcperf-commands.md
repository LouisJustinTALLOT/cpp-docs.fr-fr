---
title: 'Référence : commandes vcperf'
description: Référence pour l’utilitaire de ligne de commande vcperf. exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332221"
---
# <a name="reference-vcperf-commands"></a>Référence : commandes vcperf

::: moniker range="<=vs-2017"

Les C++ outils de génération Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Cet article répertorie et décrit les commandes disponibles dans *vcperf. exe*, et explique comment les utiliser.

## <a name="commands-to-start-and-stop-traces"></a>Commandes pour démarrer et arrêter des traces

*IMPORTANT : les commandes suivantes nécessitent toutes des privilèges d’administrateur.*

| Option           | Arguments et description |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Indique à *vcperf. exe* de démarrer une trace sous le nom de session donné. Il ne peut y avoir qu’une seule session active à la fois sur un ordinateur donné. <br/><br/> Si l’option `/nocpusampling` est spécifiée, *vcperf. exe* ne collecte pas les exemples de processeur. Il empêche l’utilisation de la vue utilisation de l’UC (échantillonnée) dans l’analyseur de performances Windows, mais rend les traces collectées plus petites. <br/><br/> Une fois le suivi démarré, *vcperf. exe* est retourné immédiatement. Les événements sont collectés à l’ensemble du système pour tous les processus en cours d’exécution sur l’ordinateur. Cela signifie que vous n’avez pas besoin de générer votre projet à partir de la même invite de commandes que celle utilisée pour exécuter *vcperf. exe*. Par exemple, vous pouvez générer votre projet à partir de Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Arrête la trace identifiée par le nom de session donné. Exécute une étape de suivi du traitement sur la trace pour générer un fichier affichable dans Windows Performance Analyzer (WPA). Pour une expérience d’affichage optimale, utilisez une version de WPA qui comprend C++ le complément Build Insights. Pour plus d’informations, consultez [prise en C++ main de build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). Le paramètre `<outputFile.etl>` spécifie l’emplacement où enregistrer le fichier de sortie. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Arrête la trace identifiée par le nom de session donné et écrit les données brutes non traitées dans le fichier de sortie spécifié. Le fichier résultant n’est pas destiné à être affiché dans WPA. <br/><br/> L’étape de publication impliquée dans la commande `/stop` peut parfois être longue. Vous pouvez utiliser la commande `/stopnoanalyze` pour retarder cette étape de publication. Utilisez la commande `/analyze` lorsque vous êtes prêt à créer un fichier affichable dans Windows Performance Analyzer. |

## <a name="miscellaneous-commands"></a>Commandes diverses

| Option     | Arguments et description |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Accepte un fichier de trace brut produit par la commande `/stopnoanalyze`. Exécute une étape de suivi sur ce suivi pour générer un fichier affichable dans l’analyseur de performances Windows. Pour une expérience d’affichage optimale, utilisez une version de WPA qui comprend C++ le complément Build Insights. Pour plus d’informations, consultez [prise en C++ main de build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Voir aussi

[Prise en main C++ de la\ de build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)
[Didacticiel : notions de base de l’analyseur de performances Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Référence : vues de l’analyseur de performances Windows](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
