---
title: Bien démarrer avec C++ Build Insights
description: Une vue d’ensemble de l’utilisation des outils d’analyse des performances au moment de la génération qui font C++ partie de build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 862bfae3bdb27812306dcd356aecab812ea5181c
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298738"
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

Les deux principaux composants de cette technologie sont l’utilitaire de ligne de commande *vcperf. exe* et un complément pour la visionneuse de trace Windows Performance Analyzer (WPA). L’utilitaire est utilisé pour collecter les traces de votre Build, tandis que le complément vous permet de les afficher dans WPA. Suivez ces étapes pour commencer à utiliser ces deux outils.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Étape 1 : installer et configurer l’analyseur de performances Windows

WPA est une visionneuse de trace disponible dans le kit de déploiement et d’évaluation Windows (ADK). Il s’agit d’un utilitaire distinct qui ne fait pas partie des composants que vous pouvez installer à l’aide du programme d’installation de Visual Studio.

Une version de WPA qui prend C++ en charge Build Insights est actuellement disponible uniquement dans Windows ADK Insider preview. Pour accéder à cette version préliminaire, vous devez vous inscrire au [programme Windows Insider](https://insider.windows.com). Vous n’avez pas besoin d’installer le système d’exploitation Windows 10 Insider Preview pour obtenir la version préliminaire de Windows ADK. Vous devez uniquement inscrire votre compte Microsoft dans le programme Windows Insider.

### <a name="to-download-and-install-wpa"></a>Pour télécharger et installer WPA

Remarque : Windows 8 ou version ultérieure est requis pour l’installation de l’analyseur de performances Windows.

1. Accédez à la [page de téléchargement](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)de Windows ADK Insider preview.

1. Téléchargez Windows ADK Insider preview. Il s’agit d’une image de disque.

1. Ouvrez l’image de disque et exécutez le programme d’installation de *adksetup. exe* .

1. Lorsque vous êtes invité à entrer les fonctionnalités que vous souhaitez installer, sélectionnez **Windows performance Toolkit**. Vous pouvez sélectionner d’autres fonctionnalités si vous le souhaitez, mais elles ne sont pas requises pour installer WPA.

   ![Écran de sélection des fonctionnalités du programme d’installation de Windows Performance Analyzer](media/wpa-installation.png)

### <a name="configuration-steps"></a>Pour configurer Build Insights

1. Lancez WPA.

1. Sélectionnez **fenêtre** > **Sélectionner des tables (expérimental)** .

1. Faites défiler jusqu’à la section **Diagnostics** .

1. Sélectionnez toutes les vues MSVC Build Insights.

   ![Panneau de sélection de la table de l’analyseur de performances Windows](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Étape 2 : tracer votre build avec vcperf. exe

Pour afficher C++ les données de build Insights, commencez par les collecter dans un fichier de trace en procédant comme suit :

1. Ouvrez un outil natif ou une invite de commandes développeur Cross Tools pour Visual Studio 2019 en mode administrateur. (Cliquez avec le bouton droit sur l’élément de menu Démarrer, puis choisissez **plus** > **exécuter en tant qu’administrateur**.)

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

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Étape 3 : afficher votre suivi dans l’analyseur de performances Windows

Lancez WPA et ouvrez la trace que vous venez de collecter. WPA doit le reconnaître comme un C++ suivi de build Insights, et les affichages suivants doivent apparaître dans le volet de l’Explorateur graphique sur la gauche :

- Build Explorer
- Files
- Fonction

Si vous ne voyez pas ces affichages, vérifiez que l’activation de la configuration WPA est correctement configurée, comme décrit à l' [étape 1](#configuration-steps). Vous pouvez afficher vos données de build en faisant glisser les vues dans la fenêtre d’analyse vide à droite, comme illustré ici :

![Affichage d' C++ un suivi de build Insights dans l’analyseur de performances Windows](media/wpa-viewing-trace.gif)

D’autres vues sont disponibles dans le panneau de l’Explorateur graphique. Faites-les glisser dans la fenêtre d’analyse lorsque vous êtes intéressé par les informations qu’ils contiennent. Une vue utile est la vue UC (échantillonnée), qui montre l’utilisation de l’UC dans votre Build.

## <a name="more-information"></a>En savoir plus

[Notions de base de l’analyseur de performances Windows](wpa-basics.md)\
Découvrez les opérations WPA courantes qui peuvent vous aider à analyser vos suivis de Build.

informations de [référence sur vcperf. exe](vcperf-reference.md)\
La référence de commande *vcperf. exe* répertorie toutes les options de commande disponibles.

Informations de référence sur les vues de l' [Analyseur de performances Windows](wpa-views-reference.md)\
Reportez-vous à cet article C++ pour plus d’informations sur les vues de build Insights dans WPA.

\ de l' [Analyseur de performances Windows](/windows-hardware/test/wpt/windows-performance-analyzer)
Le site officiel de documentation WPA.

::: moniker-end
