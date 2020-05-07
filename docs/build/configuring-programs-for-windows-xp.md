---
title: Configuration des programmes pour Windows XP
description: Comment installer et utiliser les ensembles d’outils Windows XP C++ dans Visual Studio.
ms.date: 03/16/2020
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
ms.openlocfilehash: 92364d7fd25ac617baacc125b279fb0ee9c92f62
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440483"
---
# <a name="configuring-programs-for-windows-xp"></a>Configuration des programmes pour Windows XP

Visual Studio prend en charge plusieurs ensembles d’outils de plateforme. Cela signifie qu’il est possible de cibler les systèmes d’exploitation et les bibliothèques d’exécution qui ne sont pas pris en charge par l’ensemble d’outils par défaut. Par exemple, en basculant sur l’ensemble d’outils de plateforme, vous pouvez utiliser le compilateur C++ Visual Studio 2017 pour créer des applications qui ciblent Windows XP et Windows Server 2003. Vous pouvez également utiliser des ensembles d’outils de plateforme plus anciens pour maintenir le code hérité compatible binaire et continuer à tirer parti des dernières fonctionnalités de l’IDE Visual Studio.

::: moniker range="vs-2019"

L’ensemble d’outils V142 fourni dans Visual Studio 2019 ne prend pas en charge la création de code pour Windows XP. La prise en charge du développement Windows XP à l’aide de l’ensemble d’outils v141_xp Visual Studio 2017 est disponible en tant qu’option de composant individuel dans le Visual Studio Installer.

::: moniker-end

## <a name="install-the-windows-xp-platform-toolset"></a>Installer l’ensemble d’outils de plateforme Windows XP

::: moniker range="<=vs-2017"

Pour faire en sorte que l’ensemble d’outils et les composants de la plateforme Visual Studio 2017 ciblent Windows XP et Windows Server 2003, exécutez le Visual Studio Installer. Lorsque vous installez Visual Studio pour la première fois ou lorsque vous modifiez une installation existante, assurez-vous que la charge **de travail développement Desktop en C++** est sélectionnée. Dans la liste des composants facultatifs pour cette charge de travail, choisissez **Prise en charge de Windows XP pour C++**, puis choisissez **Installer** ou **Modifier**.

::: moniker-end

::: moniker range="vs-2019"

Pour faire en sorte que les composants et l’ensemble d’outils de plateforme v141_xp ciblent Windows XP et Windows Server 2003, exécutez le Visual Studio Installer. Lorsque vous installez Visual Studio pour la première fois, ou lorsque vous modifiez une installation existante, assurez-vous que la charge **de travail développement Desktop en C++** est sélectionnée. Dans l’onglet **composants individuels** , sous **compilateurs, outils de génération et runtimes**, choisissez **prise en charge C++ de Windows XP pour les outils \[vs 2017 (V141) déconseillé]**, puis choisissez **installer** ou **modifier**.

::: moniker-end

## <a name="windows-xp-targeting-experience"></a>Ciblage de Windows XP

L’ensemble d’outils de plateforme Windows XP inclus dans Visual Studio est une version du kit de développement logiciel (SDK) Windows 7, mais il utilise le compilateur C++ Visual Studio 2017. Il configure également les propriétés du projet avec les valeurs par défaut appropriées, par exemple, la spécification d’un éditeur de liens compatible pour le ciblage de bas niveau. Seules les applications de bureau Windows créées à l’aide d’un ensemble d’outils de plateforme Windows XP peuvent s’exécuter sous Windows XP et Windows Server 2003. Ces applications peuvent également s’exécuter sur des systèmes d’exploitation Windows plus récents.

### <a name="to-target-windows-xp"></a>Pour cibler Windows XP

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** du projet, sélectionnez **Propriétés** > de configuration**général**. Affectez à la propriété **ensemble d’outils de plateforme** la valeur de votre ensemble d’outils Windows XP préféré. Par exemple, choisissez **Visual Studio 2017 - Windows XP (v141_xp)** afin de créer du code pour Windows XP et Windows Server 2003 à l’aide du compilateur Microsoft C++ dans Visual Studio 2017.

### <a name="c-runtime-support"></a>Prise en charge du runtime C++

Avec l’ensemble d’outils de la plateforme Windows XP, plusieurs bibliothèques incluent la prise en charge du runtime pour Windows XP et Windows Server 2003. Ces bibliothèques sont les suivantes : bibliothèque Runtime C (CRT), bibliothèque standard C++, Active Template Library (ATL), bibliothèque runtime d’accès concurrentiel (ConCRT), bibliothèque de modèles parallèles (PPL), bibliothèque MFC (Microsoft Foundation Class) (MFC) et C++ AMP bibliothèque (programmation massive accélérée C++). Pour ces systèmes d’exploitation, les versions minimales prises en charge sont les suivantes : Windows XP Service Pack 3 (SP3) pour x86, Windows XP Service Pack 2 (SP2) pour x64 et Windows Server 2003 Service Pack 2 (SP2) pour x86 et x64.

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

En raison des différences de prise en charge de la plateforme et de la bibliothèque, l’expérience de développement pour les applications qui utilisent un ensemble d’outils de plateforme Windows XP n’est pas aussi complète que pour les applications qui utilisent l’ensemble d’outils de plateforme par défaut de Visual Studio.

- **Fonctionnalités du langage C++**

   Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2012 sont prises en charge dans les applications qui utilisent l’ensemble d’outils de plateforme v110\_xp. Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2013 sont prises en charge dans les applications qui utilisent l’ensemble d’outils de plateforme v120\_xp. Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2015 sont prises en charge dans les applications qui utilisent l’ensemble d’outils de plateforme v140\_xp. Seules les fonctionnalités du langage C++ implémentées dans Visual Studio 2017 sont prises en charge dans\_les applications qui utilisent l’ensemble d’outils de plateforme V141 XP. Visual Studio utilise le compilateur correspondant lors du développement à l’aide d’ensembles d’outils de plateforme plus anciens. Utilisez l’ensemble d’outils de plateforme Windows XP le plus récent pour tirer parti des fonctionnalités du langage C++ additionnelles implémentées dans cette version du compilateur.

- **Débogage distant**

   Les Outils de contrôle à distance de Visual Studio ne prennent pas en charge le débogage à distance sur Windows XP ou Windows Server 2003. Pour déboguer une application localement ou à distance sur Windows XP ou Windows Server 2003, utilisez un débogueur à partir d’une version antérieure de Visual Studio. Elle est similaire au débogage d’une application sur Windows Vista, qui est une cible d’exécution de l’ensemble d’outils de plateforme, mais pas une cible de débogage distant.

- **Analyse statique**

   Les ensembles d’outils de plateforme Windows XP ne prennent pas en charge l’analyse statique, car les annotations SAL pour le SDK Windows 7 et les bibliothèques Runtime ne sont pas compatibles. Vous pouvez toujours effectuer une analyse statique sur une application qui prend en charge Windows XP ou Windows Server 2003. Basculez temporairement la solution pour cibler l’ensemble d’outils de plateforme par défaut pour l’analyse, puis revenez à l’ensemble d’outils de plateforme Windows XP pour générer l’application.

- **Débogage de DirectX Graphics**

   Étant donné que le débogueur Graphics ne prend pas en charge l’API Direct3D 9, il ne peut pas être utilisé pour déboguer des applications qui utilisent Direct3D sur Windows XP ou Windows Server 2003. Toutefois, si l’application implémente un convertisseur alternatif basé sur des API Direct3D 10 ou Direct3D 11, vous pouvez utiliser le débogueur Graphics pour diagnostiquer les problèmes.

- **Développement HLSL**

   L’ensemble d’outils Windows XP ne compile pas les fichiers de code source HLSL par défaut. Pour compiler les fichiers HLSL, téléchargez et installez le Kit de développement logiciel (SDK) DirectX de juin 2010, puis définissez les répertoires VC du projet de façon à l'inclure. Pour plus d’informations, consultez la section « SDK DirectX n’inscrit pas les chemins Include/Bibliothèque avec Visual Studio 2010 » de la [page de téléchargement du kit SDK DirectX de juin 2010](https://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
