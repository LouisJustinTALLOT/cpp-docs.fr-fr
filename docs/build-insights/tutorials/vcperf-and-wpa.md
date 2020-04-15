---
title: 'Tutorial: vcperf et Windows Performance Analyzer'
description: Tutorial sur la façon d’utiliser le vcperf et WPA pour analyser les traces de construction C .
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323422"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Tutorial: vcperf et Windows Performance Analyzer

::: moniker range="<=vs-2017"

Les outils build Insights sont disponibles dans Visual Studio 2019. Pour voir la documentation de cette version, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range="vs-2019"

Dans ce tutoriel, vous apprendrez à utiliser *vcperf.exe* pour recueillir une trace de votre build C. Vous apprendrez également à afficher cette trace dans Windows Performance Analyzer.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Étape 1 : Installer et configurer l’analyseur des performances windows

WPA est une visionneuse de traces disponible dans la trousse d’évaluation et de déploiement Windows (ADK). Il s’agit d’un utilitaire distinct qui ne fait pas partie des composants que vous pouvez installer avec l’installateur Visual Studio.

Une version de WPA qui prend en charge C Build Insights n’est actuellement disponible que dans le Windows ADK Insider Preview. Pour accéder à cet aperçu, vous devez vous inscrire au [programme Windows Insider](https://insider.windows.com). Vous n’avez pas besoin d’installer le système d’exploitation Windows 10 Insider Preview pour obtenir l’aperçu Windows ADK. Vous n’avez qu’à enregistrer votre compte Microsoft avec le programme Windows Insider.

### <a name="to-download-and-install-wpa"></a>Pour télécharger et installer WPA

REMARQUE : Windows 8 ou plus est nécessaire pour installer l’analyseur de performance Windows.

1. Naviguez sur la page de [téléchargement](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)Windows ADK Insider Preview .

1. Téléchargez l’aperçu Windows ADK Insider. C’est une image de disque.

1. Ouvrez l’image du disque et exécutez *l’installateur adksetup.exe.*

1. Invité pour les fonctionnalités que vous souhaitez installer, sélectionnez la boîte à **outils de performance Windows**. Vous pouvez sélectionner d’autres fonctionnalités si vous le souhaitez, mais elles ne sont pas tenues d’installer WPA.

   ![L’écran de sélection des fonctionnalités de l’installateur d’analyse des performances Windows](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>Configurer Build Insights

1. Lancer WPA.

1. Sélectionnez **Tables** > de sélection **de fenêtre (expérimentales)**.

1. Faites défiler vers le bas pour la section **Diagnostics.**

1. Sélectionnez toutes les vues MSVC Build Insights.

   ![Panneau de sélection de table de Windows Performance Analyzer](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Étape 2: Tracez votre build avec vcperf.exe

Pour afficher les données de L’insights de construction, collectez-les d’abord dans un fichier de traces en suivant ces étapes :

1. Ouvrez une invite de commande de développeur d’outils ou d’outils croisés pour Visual Studio 2019 en mode administrateur. (Cliquez à droite sur l’élément du menu Démarrer et choisissez **More** > **Run en tant qu’administrateur**.)

1. Dans la fenêtre d’invite de commande, entrez cette commande :

   **vcperf.exe /start _SessionName_**

   Choisissez un nom de session dont vous vous souviendrez pour *SessionName*.

1. Construisez votre projet comme vous le feriez normalement. Vous n’avez pas besoin d’utiliser la même fenêtre d’invitation de commande pour construire.

1. Dans la fenêtre d’invite de commande, entrez cette commande :

   **vcperf.exe /stop _SessionName_ _traceFile.etl_**

   Utilisez le même nom de session que vous avez choisi pour *SessionName* avant. Choisissez un nom approprié pour le fichier *trace trace trace tracefile.etl.*

Voici à quoi ressemble une séquence de commande *vcperf.exe* typique dans une fenêtre d’invitation de commande de développeur :

![Un scénario d’utilisation simple de vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Notes importantes sur vcperf.exe

- Les privilèges de l’administrateur sont nécessaires pour démarrer ou arrêter une trace *vcperf.exe.* Utilisez une fenêtre d’invitation de commande de développeur que vous ouvrez en utilisant **Run comme administrateur**.

- Une seule séance de traçage à la fois peut fonctionner sur une machine.

- N’oubliez pas le nom de session que vous avez utilisé pour commencer votre trace. Il peut être gênant d’arrêter une session de course sans connaître son nom.

- Tout comme *cl.exe* et *link.exe*, le service public de commande *vcperf.exe* est inclus dans une installation MSVC. Aucune étape supplémentaire n’est nécessaire pour obtenir ce composant.

- *vcperf.exe* recueille des informations sur tous les outils MSVC fonctionnant sur votre système. En conséquence, vous n’avez pas à démarrer votre build à partir de la même invite de commande que vous avez utilisé pour recueillir la trace. Vous pouvez construire votre projet à partir d’une invite de commande différente, ou même dans Visual Studio.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Étape 3 : Affichez votre trace dans Windows Performance Analyzer

Lancez WPA et ouvrez la trace que vous venez de recueillir. WPA devrait le reconnaître comme une trace de C Build Insights, et les vues suivantes devraient apparaître dans le panneau Graph Explorer sur la gauche:

- Build Explorer
- Fichiers
- Fonction

Si vous ne pouvez pas voir ces vues, vérifiez que WPA est configuré correctement, tel que décrit dans [l’étape 1](#configuration-steps). Vous pouvez afficher vos données de build en faisant glisser les vues dans la fenêtre d’analyse vide sur la droite, comme indiqué ici:

![Affichage d’une trace D’aperçus de construction de CMD dans l’analyseur de performance de Windows](media/wpa-viewing-trace.gif)

D’autres vues sont disponibles dans le panneau Graph Explorer. Faites-les glisser dans la fenêtre d’analyse lorsque vous êtes intéressé par les informations qu’ils contiennent. Un utile est le CPU (Sampled) vue, qui montre l’utilisation CPU tout au long de votre build.

## <a name="more-information"></a>Informations complémentaires

[Tutorial: Windows Performance Analyzer basics](wpa-basics.md)\
Renseignez-vous sur les opérations WPA courantes qui peuvent vous aider à analyser vos traces de construction.

[Référence: commandes de vcperf](/cpp/build-insights/reference/vcperf-commands)\
La référence de commande *vcperf.exe répertorie* toutes les options de commande disponibles.

[Référence: Vues d’analyseur de performance Windows](/cpp/build-insights/reference/wpa-views)\
Consultez cet article pour plus de détails sur les vues de L’APM.

[Analyseur de performance Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
Le site officiel de documentation WPA.

::: moniker-end
