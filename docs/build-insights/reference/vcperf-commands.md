---
title: 'Référence : commandes vcperf'
description: Référence pour l’utilitaire de ligne de commande vcperf.exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 42ca422e11824bdbdad4e42e7b55950317095703
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922203"
---
# <a name="reference-vcperf-commands"></a>Référence : commandes vcperf

::: moniker range="<=msvc-150"

Les outils C++ Build Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range="msvc-160"

Cet article répertorie et décrit les commandes disponibles dans *vcperf.exe* , et explique comment les utiliser.

## <a name="commands-to-start-and-stop-traces"></a>Commandes pour démarrer et arrêter des traces

*IMPORTANT : les commandes suivantes nécessitent toutes des privilèges d’administrateur.*

| Option           | Arguments et description |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Indique à *vcperf.exe* de démarrer une trace sous le nom de session donné. Il ne peut y avoir qu’une seule session active à la fois sur un ordinateur donné. <br/><br/> Si l' `/nocpusampling` option est spécifiée, *vcperf.exe* ne collecte pas les échantillons de l’UC. Il empêche l’utilisation de la vue utilisation de l’UC (échantillonnée) dans l’analyseur de performances Windows, mais rend les traces collectées plus petites. <br/><br/> Une fois le suivi démarré, *vcperf.exe* est retourné immédiatement. Les événements sont collectés à l’ensemble du système pour tous les processus en cours d’exécution sur l’ordinateur. Cela signifie que vous n’avez pas besoin de générer votre projet à partir de la même invite de commandes que celle que vous avez utilisée pour exécuter *vcperf.exe* . Par exemple, vous pouvez générer votre projet à partir de Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Arrête la trace identifiée par le nom de session donné. Exécute une étape de suivi du traitement sur la trace pour générer un fichier affichable dans Windows Performance Analyzer (WPA). Pour une expérience d’affichage optimale, utilisez une version de WPA qui comprend le complément C++ Build Insights. Pour plus d’informations, consultez [prise en main de C++ Build Insights](../get-started-with-cpp-build-insights.md). Le `<outputFile.etl>` paramètre spécifie l’emplacement où enregistrer le fichier de sortie. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Arrête la trace identifiée par le nom de session donné et écrit les données brutes non traitées dans le fichier de sortie spécifié. Le fichier résultant n’est pas destiné à être affiché dans WPA. <br/><br/> L’étape de validation impliquée dans la `/stop` commande peut parfois être longue. Vous pouvez utiliser la `/stopnoanalyze` commande pour différer cette étape de publication. Utilisez la `/analyze` commande lorsque vous êtes prêt à créer un fichier affichable dans Windows Performance Analyzer. |

## <a name="miscellaneous-commands"></a>Commandes diverses

| Option     | Arguments et description |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Accepte un fichier de trace brut produit par la `/stopnoanalyze` commande. Exécute une étape de suivi sur ce suivi pour générer un fichier affichable dans l’analyseur de performances Windows. Pour une expérience d’affichage optimale, utilisez une version de WPA qui comprend le complément C++ Build Insights. Pour plus d’informations, consultez [prise en main de C++ Build Insights](../get-started-with-cpp-build-insights.md). |

## <a name="see-also"></a>Voir aussi

[Prise en main de C++ Build Insights](../get-started-with-cpp-build-insights.md)\
[Didacticiel : notions de base de l’analyseur de performances Windows](../tutorials/wpa-basics.md)\
[Référence : vues de l’analyseur de performances Windows](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
