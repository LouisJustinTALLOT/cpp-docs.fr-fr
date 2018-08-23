---
title: Configuration des programmes pour Windows XP | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1e4487b3-d815-4123-878b-5718b22f0fd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 205241f2306885800813597568ed9ae8cf3858b3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598231"
---
# <a name="configuring-programs-for-windows-xp"></a>Configuration des programmes pour Windows XP

Étant donné que Visual Studio prend en charge plusieurs ensembles d’outils de plateforme, vous pouvez cibler les systèmes d’exploitation et les bibliothèques runtime qui ne sont pas pris en charge par l’ensemble d’outils par défaut. Par exemple, en passant l’ensemble d’outils de plateforme, vous pouvez utiliser C ++ 11, C ++ 14 et les améliorations de langage C ++ 17 pris en charge par le compilateur Visual C++ dans Visual Studio pour créer des applications qui ciblent Windows XP et Windows Server 2003. Vous pouvez également utiliser des ensembles d’outils de plateforme plus anciens pour maintenir le code hérité compatible binaire et quand même tirer parti des dernières fonctionnalités de l’IDE Visual Studio.

## <a name="install-the-windows-xp-platform-toolset"></a>Installer l’ensemble d’outils de plateforme Windows XP
Pour obtenir les outils de plateforme et composants pour cibler Windows XP et Windows Server 2003 dans Visual Studio 2017, exécutez le programme d’installation Visual Studio. Lorsque vous installez initialement Visual Studio ou lorsque vous choisissez **modifier** pour modifier une installation existante, assurez-vous que le **développement Desktop en C++** charge de travail est sélectionné. Dans la liste des composants facultatifs pour cette charge de travail, choisissez **prise en charge de Windows XP pour C++**, puis choisissez **installer** ou **modifier**.

## <a name="windows-xp-targeting-experience"></a>Ciblage de Windows XP

L’ensemble d’outils de plateforme Windows XP qui est inclus dans Visual Studio est une version du SDK Windows 7, mais elle utilise le compilateur C++ actuel. Il configure également les propriétés du projet pour les valeurs par défaut appropriées, par exemple, la spécification d’un éditeur de liens compatible pour le ciblage de bas niveau. Uniquement les applications de bureau Windows sont créées à l’aide d’un ensemble d’outils de plateforme Windows XP s’exécutent sur Windows XP et Windows Server 2003, mais ces applications peuvent également exécuter sur les systèmes d’exploitation Windows plus récentes.

#### <a name="to-target-windows-xp"></a>Pour cibler Windows XP

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Propriétés**.

1. Dans le **Pages de propriétés** boîte de dialogue pour le projet, sous **propriétés de Configuration** > **général**, définissez le **ensemble d’outils de plateforme** propriété à l’ensemble d’outils Windows XP souhaité. Par exemple, choisissez **Visual Studio 2017 - Windows XP (v141_xp)** à créer du code pour Windows XP et Windows Server 2003 en utilisant le compilateur Microsoft Visual C++ 2017.

### <a name="c-runtime-support"></a>Prise en charge du runtime C++

Ainsi que l’ensemble d’outils de plateforme Windows XP, la bibliothèque de Runtime C (CRT), bibliothèque Standard C++, bibliothèque ATL (Active Template), bibliothèque de Runtime d’accès concurrentiel (ConCRT), bibliothèque de modèles parallèles (PPL), MFC Microsoft Foundation Class Library () et C++ AMP (C++ Accelerated Massive programmation) bibliothèque incluent la prise en charge du runtime pour Windows XP et Windows Server 2003. Pour ces systèmes d’exploitation, les versions minimales prises en charge sont Windows XP Service Pack 3 (SP3) pour x86, Windows XP Service Pack 2 (SP2) pour x64 et Windows Server 2003 Service Pack 2 (SP2) pour x86 et x64.

Ces bibliothèques sont prises en charge par les ensembles d’outils de plateforme installés par Visual Studio, en fonction de la cible :

|Bibliothèque|Ensemble d'outils de plateforme par défaut ciblant les applications de bureau Windows|Applications de Store ciblage de plateforme d’outils par défaut|Ensemble d’outils de la plateforme Windows XP ciblant Windows XP, Windows Server 2003|
|---|---|---|---|
|CRT|X|X|X|
|Bibliothèque standard C++|X|X|X|
|ATL|X|X|X|
|ConCRT/PPL|X|X|X|
|MFC|X||X|
|C++ AMP|X|X||

> [!NOTE]
> Les applications qui sont écrits en C / c++ / CLI et cibler le .NET Framework 4 s’exécutent sur Windows XP et Windows Server 2003.

### <a name="differences-between-the-toolsets"></a>Différences entre les ensembles d'outils

En raison de différences de prise en charge de plateforme et de bibliothèque, l’expérience de développement d’applications qui utilisent un ensemble d’outils de plateforme Windows XP n’est pas aussi complète que pour les applications qui utilisent l’ensemble d’outils de plateforme de Visual Studio par défaut.

- **Fonctionnalités du langage C++**

   Uniquement les fonctionnalités de langage C++ implémentées dans Visual Studio 2012 sont pris en charge dans les applications qui utilisent le v110\_ensemble d’outils de plateforme xp. Uniquement les fonctionnalités de langage C++ implémentées dans Visual Studio 2013 sont prises en charge dans les applications qui utilisent le v120\_ensemble d’outils de plateforme xp. Uniquement les fonctionnalités de langage C++ implémentées dans Visual Studio 2015 sont prises en charge dans les applications qui utilisent le v140\_ensemble d’outils de plateforme xp. Visual Studio utilise le compilateur correspondant lorsqu’il génère à l’aide des ensembles d’outils de plateforme plus anciens. Utilisez l’ensemble d’outils de plateforme Windows XP plus récent pour tirer parti des fonctionnalités du langage C++ supplémentaires implémentées dans cette version du compilateur.

- **Débogage distant**

   Les outils à distance pour Visual Studio ne prend pas en charge le débogage à distance sur Windows XP ou Windows Server 2003. Pour déboguer une application lorsqu’il s’exécute sur Windows XP ou Windows Server 2003, vous pouvez utiliser un débogueur à partir d’une version antérieure de Visual Studio pour le déboguer localement ou à distance. L'expérience s'apparente à celle du débogage d'une application sur Windows Vista, qui est une cible d'exécution de l'ensemble d'outils de plateforme, mais pas une cible du débogage distant.

- **Analyse statique**

   Les ensembles d’outils de plateforme Windows XP ne prennent pas en charge une analyse statique, car les annotations SAL pour le Kit de développement logiciel de Windows 7 et les bibliothèques runtime ne sont pas compatibles. Lorsque vous souhaitez effectuer une analyse statique sur une application qui prend en charge de Windows XP ou Windows Server 2003, vous pouvez basculer temporairement la solution pour cibler l’ensemble d’outils de plateforme par défaut pour effectuer l’analyse et revenez à l’ensemble d’outils de plateforme Windows XP pour générer l’application.

- **Débogage de DirectX graphics**

     Étant donné que le débogueur graphique ne prend pas en charge l’API de 9 Direct3D, il ne peut pas servir à déboguer des applications qui utilisent Direct3D sur Windows XP ou Windows Server 2003. Cependant, si l'application implémente un autre convertisseur qui utilise les API Direct3D 10 ou Direct3D 11, le débogueur Graphics peut être utilisé pour diagnostiquer les problèmes liés à l'utilisation de ces API.

- **Développement HLSL**

   Par défaut, l’ensemble d’outils Windows XP ne compile pas les fichiers de code source HLSL. Pour compiler les fichiers HLSL, téléchargez et installez le Kit de développement logiciel (SDK) DirectX de juin 2010, puis définissez les répertoires VC du projet de façon à l'inclure. Pour plus d’informations, consultez le « SDK DirectX n’inscrit pas chemins d’accès Include/bibliothèque avec Visual Studio 2010 « section de la [juin 2010 page de téléchargement du SDK DirectX](http://www.microsoft.com/download/details.aspx?displaylang=en&id=6812).
