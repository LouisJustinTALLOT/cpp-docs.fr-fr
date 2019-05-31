---
title: Configuration des programmes pour Windows XP
ms.date: 05/16/2019
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 55753737b4868f33487ed980eaf37a8801f59638
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450706"
---
# <a name="configuring-programs-for-windows-xp"></a>Configuration des programmes pour Windows XP

Comme Visual Studio prend en charge plusieurs ensembles d’outils de plateforme, vous pouvez cibler les systèmes d’exploitation et les bibliothèques Runtime qui ne sont pas pris en charge par l’ensemble d’outils par défaut. Par exemple, en changeant d’ensemble d’outils de plateforme, vous pouvez utiliser les améliorations de langage C++11, C++14 et C++17 prises en charge par le compilateur MSVC dans Visual Studio pour créer des applications qui ciblent Windows XP et Windows Server 2003. Vous pouvez également utiliser des ensembles d’outils de plateforme plus anciens pour maintenir le code hérité compatible binaire et continuer à tirer parti des dernières fonctionnalités de l’IDE Visual Studio.

Visual Studio 2019 et ultérieur n’inclut pas la prise en charge de la création de code pour Windows XP à l’aide de l’ensemble d’outils v142. La prise en charge du développement Windows XP à l’aide de l’ensemble d’outils v141 fourni dans Visual Studio 2017 est disponible en tant que composant facultatif dans Visual Studio Installer.

## <a name="install-the-windows-xp-platform-toolset"></a>Installer l’ensemble d’outils de plateforme Windows XP

Pour obtenir l’ensemble d’outils de plateforme et les composants afin de cibler Windows XP et Windows Server 2003 dans Visual Studio 2017, exécutez Visual Studio Installer. Quand vous installez initialement Visual Studio ou que vous choisissez **Modifier** pour modifier une installation existante, vérifiez que la charge de travail **Développement Desktop en C++** est sélectionnée. Dans la liste des composants facultatifs pour cette charge de travail, choisissez **Prise en charge de Windows XP pour C++** , puis choisissez **Installer** ou **Modifier**.

## <a name="windows-xp-targeting-experience"></a>Ciblage de Windows XP

L’ensemble d’outils de plateforme Windows XP fourni dans Visual Studio est une version du SDK Windows 7, mais il utilise le compilateur C++ actuel. Il configure également les propriétés du projet avec les valeurs par défaut appropriées, par exemple, la spécification d’un éditeur de liens compatible pour le ciblage de bas niveau. Seules les applications de bureau Windows créées avec un ensemble d’outils de plateforme Windows XP s’exécutent sur Windows XP et Windows Server 2003, mais ces applications peuvent aussi s’exécuter sur des systèmes d’exploitation Windows plus récents.

#### <a name="to-target-windows-xp"></a>Pour cibler Windows XP

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.

1. Dans la boîte de dialogue **Pages de propriétés** du projet, sous **Propriétés de configuration** > **Général**, définissez la propriété **Ensemble d’outils de plateforme** avec l’ensemble d’outils Windows XP souhaité. Par exemple, choisissez **Visual Studio 2017 - Windows XP (v141_xp)** afin de créer du code pour Windows XP et Windows Server 2003 à l’aide du compilateur Microsoft C++ dans Visual Studio 2017.

### <a name="c-runtime-support"></a>Prise en charge du runtime C++

Avec l’ensemble d’outils de plateforme Windows XP, la bibliothèque Runtime C (CRT), la bibliothèque standard C++, la bibliothèque ATL (Active Template), la bibliothèque du runtime d’accès concurrentiel (ConCRT), la bibliothèque de modèles parallèles (PPL), la bibliothèque MFC (Microsoft Foundation Class) et la bibliothèque C++ AMP (C++ Accelerated Massive Programming) incluent la prise en charge du runtime pour Windows XP et Windows Server 2003. Pour ces systèmes d’exploitation, les versions prises en charge sont Windows XP Service Pack 3 (SP3) pour x86, Windows XP Service Pack 2 (SP2) pour x64 et Windows Server 2003 Service Pack 2 (SP2) pour x86 et x64.

Ces bibliothèques sont prises en charge par les ensembles d’outils de plateforme installés par Visual Studio, en fonction de la cible :

|Bibliothèque|Ensemble d'outils de plateforme par défaut ciblant les applications de bureau Windows|Ensemble d’outils de plateforme par défaut ciblant les applications Store|Ensemble d’outils de plateforme Windows XP ciblant Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Bibliothèque standard C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Les applications écrites en C++/CLI et qui ciblent .NET Framework 4 s’exécutent sur Windows XP et Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Différences entre les ensembles d'outils

En raison de différences de prise en charge de plateforme et de bibliothèque, l’expérience de développement pour les applications qui utilisent un ensemble d’outils de plateforme Windows XP n’est pas aussi complète que pour les applications qui utilisent l’ensemble d’outils de plateforme par défaut Visual Studio.

- **Fonctionnalités du langage C++**

   Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2012 sont prises en charge dans les applications qui utilisent l’ensemble d’outils de plateforme v110\_xp. Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2013 sont prises en charge dans les applications qui utilisent l’ensemble d’outils de plateforme v120\_xp. Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2015 sont prises en charge dans les applications qui utilisent l’ensemble d’outils de plateforme v140\_xp. Visual Studio utilise le compilateur correspondant lors du développement à l’aide d’ensembles d’outils de plateforme plus anciens. Utilisez l’ensemble d’outils de plateforme Windows XP le plus récent pour tirer parti des fonctionnalités du langage C++ additionnelles implémentées dans cette version du compilateur.

- **Débogage distant**

   Les Outils de contrôle à distance de Visual Studio ne prennent pas en charge le débogage à distance sur Windows XP ou Windows Server 2003. Pour déboguer une application quand elle s’exécute sur Windows XP ou Windows Server 2003, vous pouvez utiliser un débogueur à partir d’une version antérieure de Visual Studio pour la déboguer localement ou à distance. L'expérience s'apparente à celle du débogage d'une application sur Windows Vista, qui est une cible d'exécution de l'ensemble d'outils de plateforme, mais pas une cible du débogage distant.

- **Analyse statique**

   Les ensembles d’outils de plateforme Windows XP ne prennent pas en charge l’analyse statique, car les annotations SAL pour le SDK Windows 7 et les bibliothèques Runtime ne sont pas compatibles. Quand vous souhaitez effectuer une analyse statique sur une application qui prend en charge Windows XP ou Windows Server 2003, vous pouvez basculer temporairement la solution afin de cibler l’ensemble d’outils de plateforme par défaut et d’effectuer l’analyse, puis revenir à l’ensemble d’outils de plateforme Windows XP pour générer l’application.

- **Débogage de DirectX Graphics**

   Comme le débogueur Graphics ne prend pas en charge l’API Direct3D 9, il ne peut pas être utilisé pour déboguer les applications qui utilisent Direct3D sur Windows XP ou Windows Server 2003. Cependant, si l'application implémente un autre convertisseur qui utilise les API Direct3D 10 ou Direct3D 11, le débogueur Graphics peut être utilisé pour diagnostiquer les problèmes liés à l'utilisation de ces API.

- **Développement HLSL**

   Par défaut, l’ensemble d’outils Windows XP ne compile pas les fichiers de code source HLSL. Pour compiler les fichiers HLSL, téléchargez et installez le Kit de développement logiciel (SDK) DirectX de juin 2010, puis définissez les répertoires VC du projet de façon à l'inclure. Pour plus d’informations, consultez la section « SDK DirectX n’inscrit pas les chemins Include/Bibliothèque avec Visual Studio 2010 » de la [page de téléchargement du kit SDK DirectX de juin 2010](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
