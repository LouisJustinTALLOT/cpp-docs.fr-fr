---
title: Fichiers de ressources de projet (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: d37c3602d8939db609fc8af42dd764655195b24b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041014"
---
# <a name="project-resource-files-c"></a>Fichiers de ressources de projet (C++)

Les ressources sont des éléments d’interface qui fournissent des informations à l’utilisateur. Les bitmaps, les icônes, les barres d’outils et les curseurs sont tous des ressources. Certaines ressources peuvent effectuer une action comme sélectionner une commande dans un menu ou entrer des données dans une boîte de dialogue.

Pour plus d’informations, consultez [Utilisation des ressources](../../windows/working-with-resource-files.md).

|Nom de fichier|Emplacement du répertoire|Emplacement dans l'Explorateur de solutions|Description|
|---------------|------------------------|--------------------------------|-----------------|
|*NomProj*.rc|*Nomproj*|Fichiers sources|Fichier de script de ressources pour le projet. Ce fichier contient les éléments suivants, selon le type du projet et la prise en charge sélectionnée pour le projet (par exemple, barres d’outils, boîtes de dialogue ou HTML) :<br /><br />- Définition du menu par défaut.<br />- Tables d’accélérateurs et de chaînes.<br />-Boîte de dialogue **à propos** de par défaut.<br />- Autres boîtes de dialogue.<br />-Fichier icône (res \\ *ProjName*. ico).<br />- Informations de version.<br />- Bitmaps.<br />- Barre d’outils.<br />- Fichiers HTML.<br /><br /> Le fichier de ressources inclut le fichier Afxres.rc pour les ressources standard des classes MFC (Microsoft Foundation Class).|
|Resource.h|*Nomproj*|Fichiers d’en-tête|Fichier d’en-tête des ressources qui contient les définitions des ressources utilisées par le projet.|
|*NomProj*.rc2|*NomProj*\res|Fichiers sources|Fichier de script qui contient les ressources supplémentaires utilisées par le projet. Vous pouvez ajouter le fichier .rc2 sous le fichier .rc du projet.<br /><br /> Un fichier .rc2 s’avère utile pour ajouter des ressources utilisées par plusieurs projets différents. Au lieu de créer les mêmes ressources pour chaque projet, vous pouvez les regrouper dans un fichier .rc2 et ajouter ce dernier au fichier .rc principal.|
|*NomProj*.def|*Nomproj*|Fichiers sources|Fichier de définition de module pour un projet DLL. Dans le cas d’un contrôle, ce fichier fournit le nom et la description du contrôle ainsi que la taille du tas au moment de l’exécution.|
|*NomProj*.ico|*NomProj*\res|Fichiers de ressources|Fichier icône pour le projet ou le contrôle. Cette icône s’affiche quand l’application est réduite. Elle figure également dans la boîte de dialogue **À propos de** relative à l’application. Par défaut, MFC fournit l’icône MFC et ATL, l’icône ATL.|
|*NomProj*Doc.ico|*NomProj*\res|Fichiers de ressources|Fichier icône pour un projet MFC qui offre une prise en charge de l’architecture document/vue.|
|Toolbar.bmp|*NomProj*\res|Fichiers de ressources|Fichier bitmap représentant l’application ou le contrôle dans une barre d’outils ou une palette. Cette bitmap est intégrée au fichier de ressources du projet. La barre d’outils et la barre d’état initiales sont construites dans la classe **CMainFrame**.|
|ribbon.mfcribbon-ms|*NomProj*\res|Fichiers de ressources|Fichier de ressources qui contient le code XML définissant les boutons, les contrôles et les attributs dans le ruban. Pour plus d'informations, consultez [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual Studio C++](file-types-created-for-visual-cpp-projects.md)
