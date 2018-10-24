---
title: Fichiers de ressources (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 101d58eeb61335939db507ff6addd0c4fa7917f0
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861900"
---
# <a name="resource-files-c"></a>Fichiers de ressources (C++)

Les ressources sont des éléments d’interface qui fournissent des informations à l’utilisateur. Les bitmaps, les icônes, les barres d’outils et les curseurs sont tous des ressources. Certaines ressources peuvent être manipulées afin d’effectuer une action spécifique, telle que la sélection d’une commande dans un menu ou la saisie de données dans une boîte de dialogue.

Pour plus d’informations, consultez [Utilisation de ressources](../windows/working-with-resource-files.md).

|Nom de fichier|Emplacement du répertoire|Emplacement dans l'Explorateur de solutions|Description|
|---------------|------------------------|--------------------------------|-----------------|
|*NomProj*.rc|*Projname*|Fichiers sources|Fichier de script de ressources pour le projet. Ce fichier contient les éléments suivants, selon le type du projet et la prise en charge sélectionnée pour le projet (par exemple, barres d’outils, boîtes de dialogue ou HTML) :<br /><br />- Définition du menu par défaut.<br />- Tables d’accélérateurs et de chaînes.<br />- Boîte de dialogue **À propos de** par défaut.<br />- Autres boîtes de dialogue.<br />- Fichier icône (res\\*NomProj*.ico).<br />- Informations de version.<br />- Bitmaps.<br />- Barre d’outils.<br />- Fichiers HTML.<br /><br /> Le fichier de ressources inclut le fichier Afxres.rc pour les ressources standard des classes MFC (Microsoft Foundation Class).|
|Resource.h|*Projname*|Fichiers d'en-tête|Fichier d’en-tête des ressources qui contient les définitions des ressources utilisées par le projet.|
|*NomProj*.rc2|*NomProj*\res|Fichiers sources|Fichier de script qui contient les ressources supplémentaires utilisées par le projet. Vous pouvez ajouter le fichier .rc2 sous le fichier .rc du projet.<br /><br /> Un fichier .rc2 s’avère utile pour ajouter des ressources utilisées par plusieurs projets différents. Au lieu de créer les mêmes ressources pour chaque projet, vous pouvez les regrouper dans un fichier .rc2 et ajouter ce dernier au fichier .rc principal.|
|*NomProj*.def|*Projname*|Fichiers sources|Fichier de définition de module pour un projet DLL. Dans le cas d’un contrôle, ce fichier fournit le nom et la description du contrôle ainsi que la taille du tas au moment de l’exécution.|
|*NomProj*.ico|*NomProj*\res|Fichiers de ressources|Fichier icône pour le projet ou le contrôle. Cette icône s’affiche quand l’application est réduite. Elle figure également dans la boîte de dialogue **À propos de** relative à l’application. Par défaut, MFC fournit l’icône MFC et ATL, l’icône ATL.|
|*NomProj*Doc.ico|*NomProj*\res|Fichiers de ressources|Fichier icône pour un projet MFC qui offre une prise en charge de l’architecture document/vue.|
|Toolbar.bmp|*NomProj*\res|Fichiers de ressources|Fichier bitmap représentant l’application ou le contrôle dans une barre d’outils ou une palette. Cette bitmap est intégrée au fichier de ressources du projet. La barre d’outils et la barre d’état initiales sont construites dans la classe **CMainFrame**.|
|ribbon.mfcribbon-ms|*NomProj*\res|Fichiers de ressources|Fichier de ressources qui contient le code XML définissant les boutons, les contrôles et les attributs dans le ruban. Pour plus d'informations, consultez [Ribbon Designer (MFC)](../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)
