---
title: Fichiers créés pour les projets CLR
ms.date: 11/04/2016
helpviewer_keywords:
- Visual Studio C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: e41544adb040175fc8e53ab0e6bc4f8275891580
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446312"
---
# <a name="files-created-for-clr-projects"></a>Fichiers créés pour les projets CLR

Quand vous utilisez des modèles Visual C++ pour créer vos projets, plusieurs fichiers sont créés, selon le modèle que vous utilisez. Le tableau suivant liste tous les fichiers qui sont créés par des modèles de projet pour les projets .NET Framework.

|Nom de fichier|Description du fichier|
|---------------|----------------------|
|AssemblyInfo.cpp|Fichier qui contient des informations (autrement dit, des attributs, fichiers, ressources, types, informations de gestion des versions, informations de signature, etc.) permettant de modifier les métadonnées de l’assembly du projet. Pour plus d’informations, consultez [Contenu d’un assembly](/dotnet/framework/app-domains/assembly-contents).|
|*nomproj*.asmx|Fichier texte qui référence les classes managées qui encapsulent la fonctionnalité du service web XML.|
|*nomproj*.cpp|Principal fichier source et point d’entrée dans l’application créée par Visual Studio à votre intention. Identifie le fichier .dll et l’espace de noms du projet. Fournissez votre propre code dans ce fichier.|
|*nomproj*.vsdisco|Fichier de déploiement XML contenant des liens vers d’autres ressources qui décrivent le service web XML.|
|*nomproj*.h|Principal fichier Include pour le projet, qui contient l’ensemble des déclarations, symboles globaux et directives `#include` pour d’autres fichiers d’en-tête.|
|*nomproj*.sln|Fichier solution utilisé dans l’environnement de développement pour regrouper tous les éléments de votre projet dans une solution unique.|
|*nomproj*.suo|Fichier d’options de solution utilisé dans l’environnement de développement.|
|*nomproj*.vcxproj|Fichier projet utilisé dans l’environnement de développement, où sont stockées les informations spécifiques à ce projet.|
|ReadMe.txt|Fichier qui décrit chaque fichier de votre projet en utilisant les noms de fichiers réels créés par le modèle.|