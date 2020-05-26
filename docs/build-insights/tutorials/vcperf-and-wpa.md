---
title: 'Didacticiel : vcperf et analyseur de performances Windows'
description: Didacticiel sur l’utilisation de vcperf et WPA pour analyser les traces de build C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 724df913400abb6d33c333f0a16c20fb982769bc
ms.sourcegitcommit: 98139766b548c55181ff5ec5ad3bfd9db2bf5c89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83865050"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Didacticiel : vcperf et analyseur de performances Windows

::: moniker range="<=vs-2017"

Les outils C++ Build Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range="vs-2019"

Dans ce didacticiel, vous allez apprendre à utiliser *vcperf. exe* pour collecter une trace de votre Build C++. Vous allez également apprendre à afficher ce suivi dans Windows Performance Analyzer.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Étape 1 : installer et configurer l’analyseur de performances Windows

WPA est une visionneuse de trace disponible dans le kit de déploiement et d’évaluation Windows (ADK). Il s’agit d’un utilitaire distinct qui ne fait pas partie des composants que vous pouvez installer à l’aide du programme d’installation de Visual Studio.

Une version de WPA qui prend en charge C++ Build Insights est actuellement disponible uniquement dans Windows ADK Insider preview. Pour accéder à cette version préliminaire, vous devez vous inscrire au [programme Windows Insider](https://insider.windows.com). Vous n’avez pas besoin d’installer le système d’exploitation Windows 10 Insider Preview pour obtenir la version préliminaire de Windows ADK. Vous devez uniquement inscrire votre compte Microsoft dans le programme Windows Insider.

### <a name="to-download-and-install-wpa"></a>Pour télécharger et installer WPA

Remarque : Windows 8 ou version ultérieure est requis pour l’installation de l’analyseur de performances Windows.

1. Accédez à la page de [Téléchargement](https://docs.microsoft.com/windows-hardware/get-started/adk-install)de Windows ADK.

1. Téléchargez et installez la dernière version de Windows ADK.

1. Lorsque vous êtes invité à entrer les fonctionnalités que vous souhaitez installer, sélectionnez **Windows performance Toolkit**. Vous pouvez sélectionner d’autres fonctionnalités si vous le souhaitez, mais elles ne sont pas requises pour installer WPA.

   ![Écran de sélection des fonctionnalités du programme d’installation de Windows Performance Analyzer](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a>Pour configurer WPA

L’affichage des suivis de build Insights C++ dans WPA requiert un complément spécial. Procédez comme suit pour l’installer :

1. Procurez-vous le complément en téléchargeant l’un des composants ci-dessous. Vous n’avez pas besoin d’utiliser les deux. Choisissez celui que vous trouvez le plus pratique.
    1. [Visual Studio 2019 version 16,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/), ou,
    1. [Package NuGet C++ Build Insights](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/).

1. Copiez le `perf_msvcbuildinsights.dll` fichier dans votre répertoire d’installation WPA.
    1. Dans Visual Studio 2019 version 16,6 et versions ultérieures, ce fichier se trouve ici : `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}` .
    1. Dans le package NuGet C++ Build Insights, ce fichier se trouve ici : `wpa\{Architecture}` .
    1. Dans les tracés ci-dessus, remplacez les variables entourées par des accolades comme suit :
        1. `{Edition}`est votre édition Visual Studio 2019 telle que Community, Professional ou Enterprise.
        1. `{Version}`est votre version de MSVC. Choisissez le plus élevé disponible.
        1. `{Architecture}`: choisissez `x64` si vous disposez d’une version 64 bits de Windows. Dans le cas contraire, choisissez `x86` .
    1. Le répertoire d’installation de WPA est généralement : `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit` .

1. Dans votre répertoire d’installation WPA, ouvrez le `perfcore.ini` fichier et ajoutez une entrée pour `perf_msvcbuildinsights.dll` .

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Étape 2 : tracer votre build avec vcperf. exe

Pour afficher les données de build Insights C++, commencez par les collecter dans un fichier de trace en procédant comme suit :

1. Ouvrez une **x64** invite de commandes des outils natifs x86 x64 **pour vs 2019** en mode administrateur. (Cliquez avec le bouton droit sur l’élément de menu Démarrer et choisissez **plus**  >  **Exécutez en tant qu’administrateur**.)
    1. Choisissez **x64** si vous disposez d’une version 64 bits de Windows. Dans le cas contraire, choisissez **x86**.

1. Dans la fenêtre d’invite de commandes, entrez la commande suivante :

   **vcperf. exe/Start _nom_session_**

   Choisissez un nom de session dont vous vous souviendrez pour *nom_session*.

1. Générez votre projet comme vous le feriez normalement. Vous n’avez pas besoin d’utiliser la même fenêtre d’invite de commandes pour générer.

1. Dans la fenêtre d’invite de commandes, entrez la commande suivante :

   **vcperf. exe/Stop _nom_session_ _traceFile. etl_**

   Utilisez le même nom de session que celui que vous avez choisi pour *nom_session* . Choisissez un nom approprié pour le fichier de trace *traceFile. etl* .

Voici à quoi ressemble une séquence de commande *vcperf. exe* typique dans une fenêtre d’invite de commandes développeur :

![Un simple scénario d’utilisation de vcperf. exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Remarques importantes sur vcperf. exe

- Des privilèges d’administrateur sont nécessaires pour démarrer ou arrêter une trace *vcperf. exe* . Utilisez une fenêtre d’invite de commandes développeur que vous ouvrez en utilisant **exécuter en tant qu’administrateur**.

- Une seule session de suivi à la fois peut s’exécuter sur un ordinateur.

- Veillez à mémoriser le nom de session que vous avez utilisé pour démarrer votre trace. Il peut être pénible d’arrêter une session en cours d’exécution sans connaître son nom.

- Tout comme *CL. exe* et *Link. exe*, l’utilitaire de ligne de commande *vcperf. exe* est inclus dans une installation MSVC. Aucune étape supplémentaire n’est requise pour obtenir ce composant.

- *vcperf. exe* collecte des informations sur tous les outils MSVC en cours d’exécution sur votre système. Par conséquent, vous n’avez pas besoin de démarrer votre build à partir de l’invite de commandes que vous avez utilisée pour collecter la trace. Vous pouvez générer votre projet à partir d’une autre invite de commandes, ou même dans Visual Studio.

### <a name="vcperfexe-is-open-source"></a>vcperf. exe est open-source

Si vous souhaitez générer et exécuter votre propre version de *vcperf. exe*, n’hésitez pas à le cloner à partir du [référentiel GitHub vcperf](https://github.com/microsoft/vcperf).

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Étape 3 : afficher votre suivi dans l’analyseur de performances Windows

Lancez WPA et ouvrez la trace que vous venez de collecter. WPA doit le reconnaître comme un suivi C++ Build Insights, et les affichages suivants doivent apparaître dans le volet de l’Explorateur graphique sur la gauche :

- Build Explorer
- Files
- Fonctions
- Instanciations de modèle

Si vous ne voyez pas ces affichages, vérifiez que l’activation de la configuration WPA est correctement configurée, comme décrit à l' [étape 1](#configuration-steps). Vous pouvez afficher vos données de build en faisant glisser les vues dans la fenêtre d’analyse vide à droite, comme illustré ici :

![Affichage d’une trace C++ Build Insights dans Windows Performance Analyzer](media/wpa-viewing-trace.gif)

D’autres vues sont disponibles dans le panneau de l’Explorateur graphique. Faites-les glisser dans la fenêtre d’analyse lorsque vous êtes intéressé par les informations qu’ils contiennent. Une vue utile est la vue UC (échantillonnée), qui montre l’utilisation de l’UC dans votre Build.

## <a name="more-information"></a>Informations complémentaires

[Didacticiel : notions de base de l’analyseur de performances Windows](wpa-basics.md)\
Découvrez les opérations WPA courantes qui peuvent vous aider à analyser vos suivis de Build.

[Référence : commandes vcperf](/cpp/build-insights/reference/vcperf-commands)\
La référence de commande *vcperf. exe* répertorie toutes les options de commande disponibles.

[Référence : vues de l’analyseur de performances Windows](/cpp/build-insights/reference/wpa-views)\
Reportez-vous à cet article pour plus d’informations sur les vues C++ Build Insights dans WPA.

[Analyseur de performances Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
Le site officiel de documentation WPA.

::: moniker-end
