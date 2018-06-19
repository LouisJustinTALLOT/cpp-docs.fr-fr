---
title: L’optimisation dans le Hub performances et Diagnostics guidée par profil | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8a586ef48f87f90dd5f191f9fcaea6f30af5c56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378962"
---
# <a name="profile-guided-optimization-in-the-visual-studio-2013-performance-and-diagnostics-hub"></a>L’optimisation dans Visual Studio 2013 Hub performances et Diagnostics guidée par profil

Si vous utilisez Visual Studio 2013, l’optimisation guidée par profil pour le plug-in dans le Hub performances et Diagnostics de Visual C++ simplifie l’expérience de l’optimisation guidée par profil pour les développeurs. Vous pouvez [télécharger le plug-in](http://go.microsoft.com/fwlink/p/?LinkId=327915) depuis le site Web de Visual Studio. Le plug-in n’est pas pris en charge dans les versions ultérieures de Visual Studio.

L'optimisation guidée par profil (PGO) vous aide à créer des builds d'applications natives x86 et x64 qui sont optimisées pour la manière dont les utilisateurs interagissent avec elles. PGO est un processus en plusieurs étapes : vous créez une build de l’application instrumentée pour le profilage, puis vous effectuez la « formation ». Autrement dit, vous exécutez l’application instrumentée via des scénarios d’interaction utilisateur courants. Vous enregistrez les données de profilage capturées, puis vous régénérez votre application en utilisant les résultats pour guider l'optimisation de l'ensemble du programme. Bien que vous puissiez exécuter ces étapes individuellement dans Visual Studio ou sur la ligne de commande, le plug-in PGO centralise et simplifie le processus. Le plug-in PGO définit toutes les options requises, vous guide tout au long de chaque étape, affiche l'analyse, puis utilise les résultats pour configurer la build et optimiser la taille ou la vitesse de chaque fonction. Le plug-in PGO facilite également la réexécution de votre formation d’application et la mise à jour des données d’optimisation de build lorsque vous modifiez votre code.

## <a name="prerequisites"></a>Prérequis

Vous devez [télécharger le plug-in PGO](http://go.microsoft.com/fwlink/p/?LinkId=327915) et l’installer dans Visual Studio avant de pouvoir l’utiliser dans le Hub performances et Diagnostics.

## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>Procédure pas à pas : utilisation du plug-in PGO pour optimiser une application

D'abord, vous allez créer une application de bureau Win32 de base dans Visual Studio. Si vous possédez déjà une application native que vous souhaitez optimiser, vous pouvez l'utiliser et ignorer cette étape.

### <a name="to-create-an-app"></a>Pour créer une application

1. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé**, **modèles**, **Visual C++**, puis sélectionnez  **MFC**.

1. Dans le volet central, sélectionnez **Application MFC**.

1. Spécifiez un nom pour le projet, par exemple, **SamplePGOProject**: dans le **nom** boîte. Sélectionnez le bouton **OK** .

1. Sur le **vue d’ensemble** page de la **Assistant Application MFC** boîte de dialogue, choisissez le **Terminer** bouton.

Ensuite, affectez à la configuration de build de votre application la valeur Mise en production pour la préparer aux étapes de génération et de formation PGO.

### <a name="to-set-the-build-configuration"></a>Pour définir la configuration de build

1. Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**.

1. Dans le **Configuration Manager** boîte de dialogue, choisissez le **Configuration de la Solution Active** bouton de liste déroulante et sélectionnez **version**. Choisissez le **fermer** bouton.

Ouvrir le Hub performances et Diagnostics, dans la barre de menus, choisissez **analyser**, **performances et Diagnostics**. Cela ouvre une page de session de diagnostic qui contient les outils d'analyse disponibles pour votre type de projet.

![PGO dans le Hub performances et Diagnostics](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")

Dans **outils disponibles**, sélectionnez le **optimisation guidée par profil** case à cocher. Choisissez le **Démarrer** bouton pour démarrer le plug-in PGO.

![Page d’introduction PGO](../../build/reference/media/pgofig1start.png "PGOFig1Start")

Le **optimisation guidée par profil** page décrit les étapes du plug-in utilise pour améliorer les performances de votre application. Choisissez le **Démarrer** bouton.

![Page d’instrumentation PGO](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")

Dans le **Instrumentation** section, vous utilisez la **formation est initialement activée** permet de choisir s’il faut inclure la phase de démarrage de votre application dans le cadre de la formation. Si cette option n’est pas activée, les données de formation ne sont pas stockées dans une application instrumentée en cours d’exécution tant que vous n’activez pas explicitement la formation.

Choisissez le **Instrument** pour générer votre application avec un ensemble spécial d’options du compilateur. Le compilateur insère des instructions de sonde dans le code généré. Ces instructions enregistrent les données de profilage pendant la phase de formation.

![Page de build instrumentée PGO](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")

Lorsque la génération instrumentée de votre application est terminée, l'application est lancée automatiquement.

Si les erreurs ou avertissements se produisent pendant la génération, corrigez-les, puis choisissez **Restart Build** pour redémarrer la génération instrumentée.

Lorsque votre application est lancée, vous pouvez utiliser la **Start Training** et **Pause Training** des liaisons dans le **formation** section pour contrôler quand les informations de profilage sont enregistrée. Vous pouvez utiliser la **arrêter l’Application** et **démarrer l’Application** des liens pour arrêter et redémarrer l’application.

![Page de formation PGO](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")

Pendant la formation, parcourez vos scénarios utilisateur pour capturer les informations de profilage dont le plug-in PGO a besoin pour optimiser le code. Lorsque vous avez terminé la formation, fermez votre application, ou choisissez la **arrêter l’Application** lien. Choisissez le **analyser** bouton pour démarrer la phase d’analyse.

Lorsque l’analyse est terminée, le **analyse** section affiche un rapport des informations de profilage capturées pendant la phase de formation du scénario utilisateur. Vous pouvez utiliser ce rapport pour examiner les fonctions que votre application a appelées le plus et dans lesquelles elle a passé le plus de temps. Le plug-in PGO utilise les informations pour déterminer les fonctions d'application à optimiser pour la vitesse et celles à optimiser pour la taille. Le plug-in PGO configure les optimisations de build pour créer l’application la plus petite et la plus rapide pour les scénarios utilisateur que vous avez enregistrés pendant la formation.

![Page d’analyse PGO](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")

Si la formation a capturé les informations de profilage attendues, vous pouvez choisir **enregistrer les modifications** pour enregistrer les données de profil analysées dans votre projet pour optimiser des builds futures. Pour ignorer les données de profil et recommencer la formation à partir du début, choisissez **Redo Training**.

Le fichier de données de profil est enregistré dans votre projet dans un **PGO Training Data** dossier. Ces données sont utilisées pour contrôler les paramètres d'optimisation de build du compilateur dans votre application.

![Le fichier de données PGO dans l’Explorateur de solutions](../../build/reference/media/pgofig6data.png "PGOFig6Data")

Après l'analyse, le plug-in PGO définit les options de build dans votre projet afin d'utiliser les données de profil pour optimiser sélectivement votre application pendant la compilation. Vous pouvez continuer à modifier et à générer votre application avec les mêmes données de profil. Lorsque l'application est générée, la sortie de génération indique le nombre de fonctions et d'instructions optimisées à l'aide des données de profil.

![Diagnostics de sortie PGO](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")

Si vous apportez des modifications de code significatives pendant le développement, vous devrez peut-être recycler votre application pour obtenir les meilleures optimisations. Nous vous recommandons de recycler votre application lorsque la sortie de génération indique que moins de 80 % des fonctions ou instructions ont été optimisées à l'aide des données de profil.