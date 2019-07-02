---
title: Mise à niveau de projets à partir de versions antérieures de Visual C++
description: Découvrez comment mettre à niveau des projets Microsoft C++ à partir de versions antérieures de Visual Studio.
ms.date: 05/03/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: 25cf8d451c0efb5234fba5e56b6bfe7ceb7c2c08
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400814"
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>Mise à niveau de projets à partir de versions antérieures de Visual C++

Dans la plupart des cas, vous pouvez ouvrir un projet créé dans une version antérieure de Visual Studio. Toutefois, pour ce faire, Visual Studio met à niveau le projet. Si vous enregistrez le projet mis à niveau, il ne pourra plus être ouvert dans une version antérieure.

> [!IMPORTANT]
> Si vous essayez de convertir un projet qui l'a déjà été, Visual Studio vous demandera une confirmation car la reconversion supprime les fichiers existants.

De nombreux projets et solutions mis à niveau peuvent être générés avec succès et sans modification. Toutefois, certains projets peuvent requérir des modifications des paramètres, du code source, ou des deux. Nous vous recommandons de respecter les consignes suivantes pour résoudre les problèmes de paramètres en premier, puis si le projet demeure impossible à générer, les problèmes de code. Pour plus d’informations, consultez [Vue d’ensemble des problèmes de mise à niveau potentiels](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

1. Faites une copie des fichiers projet et solution existants. Installez la version actuelle de Visual Studio et la version antérieure côte à côte de façon à pouvoir comparer des versions de fichier si vous le souhaitez.

2. Dans la version actuelle de Visual Studio, ouvrez puis mettez à niveau la copie du projet ou de la solution et enregistrez-la.

3. Pour chaque projet converti, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**. Sous **Propriétés de configuration**, sélectionnez **Général** , puis pour **Ensemble d'outils de plateforme**, sélectionnez la version actuelle. (Par exemple, pour Visual Studio 2017, sélectionnez **v141**.)

4. Générez la solution. Si la génération échoue, modifiez les paramètres et régénérez.

Les sources de données sont contenues dans un projet de base de données distinct afin que vous puissiez plus facilement modifier et déboguer les procédures stockées dans ces sources. Si vous mettez à niveau un projet C++ qui contient des sources de données, il est procédé automatiquement à la création d’un projet de base de données différent.

Pour plus d’informations sur la façon de mettre à jour les versions de Windows ciblées, consultez [Modification de WINVER et _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

## <a name="in-this-section"></a>Dans cette section

[Mettre à niveau votre code vers la bibliothèque Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Modification de WINVER et _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Résoudre vos dépendances aux éléments internes de bibliothèque](fix-your-dependencies-on-library-internals.md)<br/>
[Problèmes de migration de virgule flottante](floating-point-migration-issues.md)<br/>
[Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md)<br/>
[Fonctionnalités Visual C++ dépréciées dans la préversion de Visual Studio 2019](features-deprecated-in-visual-studio.md)<br/>
[Modifications du système de génération](build-system-changes.md)

## <a name="see-also"></a>Voir aussi

[Nouveautés de Visual C++ dans Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historique des modifications de Visual C++ entre 2003 et 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Comportement non standard](../cpp/nonstandard-behavior.md)
