---
description: 'En savoir plus sur : fichiers d’aide (aide HTML)'
title: Fichiers d'aide (aide HTML)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: 0a2b92300683fcc4f0ced365a6750f6e73da10f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191600"
---
# <a name="help-files-html-help"></a>Fichiers d'aide (aide HTML)

Les fichiers suivants sont créés quand vous ajoutez la prise en charge de l’aide de type HTML à votre application en cochant la case **Aide contextuelle**, puis en sélectionnant **Format d’aide HTML** dans la page [Fonctionnalités avancées](../../mfc/reference/advanced-features-mfc-application-wizard.md) de l’Assistant Application MFC.

|Nom de fichier|Emplacement du répertoire|Emplacement dans l'Explorateur de solutions|Description|
|---------------|------------------------|--------------------------------|-----------------|
|*NomProj*.hhp|*NomProj*\hlp|fichiers d'aide HTML|Fichier projet d’aide. Il contient les données nécessaires à la compilation des fichiers d’aide en un fichier .hxs ou .chm.|
|*NomProj*.hhk|*NomProj*\hlp|fichiers d'aide HTML|Contient un index des rubriques d’aide.|
|*NomProj*.hhc|*NomProj*\hlp|fichiers d'aide HTML|Contenu du projet d’aide.|
|Makehtmlhelp.bat|*Nomproj*|Fichiers sources|Fichier utilisé par le système pour générer le projet d’aide lors de la compilation du projet.|
|Afxcore.htm|*NomProj*\hlp|Rubriques d’aide HTML|Contient les rubriques d’aide standard relatives aux objets de l’écran et commandes MFC. Ajoutez vos propres rubriques d’aide à ce fichier.|
|Afxprint.htm|*NomProj*\hlp|Rubriques d’aide HTML|Contient les rubriques d’aide relatives aux commandes d’impression.|
|*.jpg; \*.gif|*NomProj*\hlp\Images|Fichiers de ressources|Contient les images des différentes rubriques d’aide générées.|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual Studio C++](file-types-created-for-visual-cpp-projects.md)
