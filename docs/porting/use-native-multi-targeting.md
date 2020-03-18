---
title: Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets
ms.date: 10/25/2019
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
ms.openlocfilehash: aff21121c181131b04ad22d75f03b7cbb222228a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422093"
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets

En règle générale, nous vous recommandons de mettre à jour vos projets quand vous installez la dernière version de Visual Studio. En règle générale, les avantages procurés par les nouveaux IDE, compilateur, bibliothèques et outils conpensent largement le coût de la mise à jour de vos projets et code. Toutefois, nous savons que vous ne serez peut-être pas en mesure de mettre à jour certains projets. Vous pouvez avoir des fichiers binaires, liés à d’anciennes bibliothèques ou plateformes, que vous ne pouvez pas mettre à niveau pour des raisons de maintenance. Votre code peut utiliser des constructions de langage non standard qui ne fonctionneraient pas si vous optiez pour un compilateur plus récent. Votre code peut s’appuyer sur des bibliothèques tierces compilées pour une version spécifique de Visual C++. Ou vous pouvez produire pour des tiers des bibliothèques qui doivent cibler une ancienne version de Visual C++ spécifique.

Heureusement, vous pouvez utiliser Visual Studio 2017 et Visual Studio 2015 pour générer des projets qui ciblent les bibliothèques et les ensembles d’outils du compilateur plus anciens. Vous n’êtes pas obligé de mettre à niveau un projet Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 ou Visual Studio 2015 pour tirer parti des nouvelles fonctionnalités de l’IDE :

  - Nouvelles fonctionnalités de refactorisation C++ et fonctionnalités expérimentales pour l’édition
  - Nouvelles fenêtre de débogage Outils de diagnostics et fenêtre Liste d’erreurs
  - Fenêtre de gestion des points d’arrêt et des exceptions revisitée, nouveaux conseils sur les performances
  - Nouveaux outils de navigation et de recherche de code
  - Nouvelles corrections rapides C++ et les extensions Productivity Power Tools

Vous pouvez également cibler des projets Visual Studio 2008, mais vous ne pouvez pas les utiliser en l’état. Pour plus d’informations, consultez la section **Instructions pour Visual Studio 2008**.

Les dernières versions de Visual Studio prennent en charge le multiciblage natif et les allers-retours des projets. Grâce au multiciblage natif, la dernière version de l’IDE peut effectuer une génération à l’aide des ensembles d’outils installés par les versions antérieures de Visual Studio. Grâce à la procédure d’aller-retour, la dernière version de l’IDE peut charger les projets créés par une version précédente de l’IDE sans y apporter de modifications. Si vous installez la dernière version de Visual Studio côte à côte avec votre version existante, vous pouvez utiliser la nouvelle version de l’IDE avec le compilateur et les outils de la version existante pour générer vos projets. Les autres membres de votre équipe peuvent continuer à utiliser les projets dans la version antérieure de Visual Studio.

Quand vous utilisez un ensemble d’outils plus ancien, vous pouvez tirer parti de nombreuses fonctionnalités du dernier IDE, mais pas des dernières avancées des outils de génération, des bibliothèques et du compilateur C++. Par exemple, vous ne pouvez pas utiliser les nouvelles améliorations de la conformité au langage, les nouvelles fonctionnalités de débogage et d’analyse du code ou profiter du débit de génération plus rapide qu’offre le dernier ensemble d’outils. En outre, certaines fonctionnalités de l’IDE ne sont pas compatibles avec les ensembles d’outils plus anciens. Par exemple, les informations de type peuvent être manquantes dans le profileur de mémoire et l’opération de refactorisation **Convertir en littéral de chaîne brute** génère du code conforme à C++11 qui n’est pas compilé si vous utilisez les ensembles d’outils Visual Studio 2012 ou antérieurs.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Comment utiliser le multiciblage natif dans Visual Studio

Une fois que vous avez installé Visual Studio côte à côte avec l’ancienne version, ouvrez votre projet existant dans la nouvelle version de Visual Studio. Quand le projet est chargé, Visual Studio vous demande si vous souhaitez le mettre à niveau pour utiliser les derniers compilateur et bibliothèques C++. Étant donné que vous souhaitez que le projet conserve les anciens compilateur et bibliothèques, choisissez le bouton **Annuler**.

Visual Studio est persistant quant à la mise à niveau de votre projet. Pour éviter l’affichage de la boîte de dialogue de mise à niveau chaque fois que vous chargez le projet, vous pouvez définir la propriété suivante dans vos projets ou dans les fichiers .props ou .targets qu’ils importent :

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Vous devez supprimer cette propriété quand vous souhaitez mettre à niveau vos projets.

Si vous choisissez de ne pas effectuer de mise à niveau, Visual Studio n’apporte aucune modification à vos fichiers projet ou solution. Quand vous générez le projet, les fichiers binaires générés sont entièrement compatibles avec ceux que vous avez générés avec l’ancienne version de Visual Studio. En effet, Visual Studio utilise le compilateur C++ et lie les bibliothèques avec lesquelles était fourni l’ancien IDE. C’est également la raison pour laquelle la boîte de dialogue de mise à niveau vous conseille de conserver l’ancienne version de Visual Studio si vous choisissez **Annuler**.

## <a name="instructions-for-visual-studio-2008"></a>Instructions pour Visual Studio 2008

Visual Studio 2008 avait son propre système de build dédié pour C++ appelé **VCBuild**. À compter de Visual Studio 2010, les projets Visual Studio C++ ont été changés pour utiliser **MSBuild**. Cela signifie que si vous effectuez une mise à niveau de manière permanente ou multiple, vous devez passer par une étape de mise à jour pour générer vos projets Visual Studio 2008 dans la dernière version de Visual Studio. Votre projet mis à jour génère toujours des fichiers binaires qui sont entièrement compatibles avec les fichiers binaires créés à l’aide de l’IDE de Visual Studio 2008.

Tout d’abord, outre la version actuelle de Visual Studio, vous devez installer Visual Studio 2010 sur le même ordinateur que Visual Studio 2008. Seul Visual Studio 2010 installe les scripts **MSBuild** nécessaires au ciblage des projets Visual Studio 2008.

Ensuite, vous devez mettre à jour vos projets et solution Visual Studio 2008 vers la version actuelle de Visual Studio. Nous vous recommandons de créer une sauvegarde de vos projets et de vos fichiers solution avant d’effectuer la mise à niveau. Pour démarrer le processus de mise à niveau, ouvrez la solution dans la version actuelle de Visual Studio. Quand vous obtenez l’invite de mise à niveau, passez en revue les informations présentées, puis choisissez **OK** pour démarrer la mise à niveau. Si la solution comporte plusieurs projets, vous devez mettre à jour L’Assistant crée les fichiers projet .vcxproj côté à côte avec les fichiers .vcproj existants. Tant que vous avez également une copie du fichier .sln d’origine, la mise à niveau n’a aucun autre impact sur vos projets Visual Studio 2008 existants.

> [!NOTE]
> Les étapes suivantes s’appliquent uniquement aux scénarios de multi-ciblage. Si vous envisagez de mettre à niveau de façon permanente le projet vers un ensemble d’outils ultérieur, l’étape suivante consiste à enregistrer le projet, à l’ouvrir dans Visual Studio 2019 et à résoudre les problèmes de build qui s’y trouvent.

Une fois la mise à niveau terminée, si le rapport de journal contient des erreurs ou des avertissements pour l’un de vos projets, examinez-les attentivement. La conversion de **VCBuild** vers **MSBuild** peut entraîner des problèmes. Veillez à comprendre et à implémenter toutes les actions répertoriées dans le rapport. Pour plus d’informations sur le rapport de journal de mise à niveau et sur les problèmes qui peuvent se produire durant la conversion de **VCBuild** vers **MSBuild**, consultez ce billet de blog consacré au [multiciblage natif C++](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/).

Une fois que la mise à niveau du projet est terminée et que vous avez résolu les problèmes éventuellement signalés dans le fichier journal, votre solution cible réellement le dernier ensemble d’outils. En guise d’étape finale, modifiez les propriétés de chaque projet dans la solution pour utiliser l’ensemble d’outils de Visual Studio 2008. Une fois la solution chargée dans la version actuelle de Visual Studio, pour chaque projet dans la solution, ouvrez la boîte de dialogue **Pages de propriétés** liée au projet : cliquez avec le bouton droit sur le projet dans l’**Explorateur de solutions**, puis sélectionnez **Propriétés**. Dans la boîte de dialogue **Pages de propriétés**, définissez la valeur de la liste déroulante **Configuration** sur **Toutes les configurations**. Dans **Propriétés de configuration**, sélectionnez **Général**, puis définissez **Ensemble d’outils de plateforme** sur **Visual Studio 2008 (v90)** .

Après cette modification, le compilateur et les bibliothèques Visual Studio 2008 sont utilisés pour générer les fichiers binaires du projet quand vous générez la solution dans la version actuelle de Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Installer un ancien ensemble d’outils Visual Studio

Peut-être que vous avez un ancien projet Visual Studio que vous ne pouvez pas ou ne souhaitez pas mettre à niveau, mais que vous ne disposez pas de la version correspondante de l’ensemble d’outils de plateforme. Dans ce cas, pour obtenir l’ensemble d’outils, vous pouvez installer l’édition Visual Studio Community ou Express gratuite de la version dont vous avez besoin. Chaque version de Visual Studio à partir de Visual Studio 2008 peut installer le compilateur, les outils et les bibliothèques dont vous avez besoin pour cibler cette version à partir de la version actuelle de Visual Studio. Dans le Centre de téléchargement Microsoft, recherchez une version particulière de Visual Studio, puis téléchargez-la. Assurez-vous de choisir les options d’installation C++ pendant l’installation. Une fois l’installation terminée, exécutez cette version de Visual Studio pour installer les mises à jour. En outre, vérifiez si des modifications Windows Update sont requises. Vous pouvez être amené à répéter ce processus de vérification de mise à jour plusieurs fois pour obtenir chaque mise à jour.

Pour connaître les téléchargements actuellement disponibles, consultez [Télécharger d’anciennes versions de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Quand ces produits sont installés, la liste déroulante de propriétés **Ensemble d’outils de plateforme** dans la boîte de dialogue **Pages de propriétés** est automatiquement mise à jour pour afficher les ensembles d’outils disponibles. Vous pouvez maintenant utiliser la dernière version de Visual Studio pour générer des projets compatibles avec ces versions antérieures de l’ensemble d’outils sans avoir à convertir ou mettre à niveau les projets.

## <a name="see-also"></a>Voir aussi

[Mise à niveau de projets à partir de versions antérieures de VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Améliorations de la conformité de C++ dans Visual Studio](../overview/cpp-conformance-improvements.md)
