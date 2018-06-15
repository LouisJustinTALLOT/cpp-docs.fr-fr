---
title: Types de fichiers créés pour les projets Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header files [C++], Visual C++ projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7158e729d80d8b0456862ee6418f039b7f948fe
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33336015"
---
# <a name="file-types-created-for-visual-c-projects"></a>Types de fichiers créés pour les projets Visual C++
Cette rubrique décrit tous les types de fichiers associés aux projets Visual C++ pour les applications de bureau classiques. Les fichiers réellement inclus dans votre projet varient en fonction du type de projet et des options que vous sélectionnez quand vous utilisez un Assistant.  
  
-   [Fichiers projet et solution](../ide/project-and-solution-files.md)  
  
-   [Projets CLR](../ide/files-created-for-clr-projects.md)  
  
-   [Fichiers d’en-tête et fichiers sources de contrôle ou de programme ATL](../ide/atl-program-or-control-source-and-header-files.md)  
  
-   [Fichiers d'en-tête et fichiers sources de contrôle ou de programme MFC](../ide/mfc-program-or-control-source-and-header-files.md)  
  
-   [Fichiers d'en-tête précompilés](../ide/precompiled-header-files.md)  
  
-   [Fichiers de ressources](../ide/resource-files-cpp.md)  
  
-   [Fichiers d’aide (WinHelp)](../ide/help-files-winhelp.md)  
  
-   [Fichiers hint](../ide/hint-files.md)  
  
 Quand il s'agit de [créer un projet Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md), vous pouvez soit créer une nouvelle solution, soit ajouter un projet à une solution. Les applications élaborées sont généralement développées avec plusieurs projets dans une même solution.  
  
 En règle générale, les projets produisent un EXE ou une DLL. Les projets peuvent être interdépendantes : pendant le processus de génération, l'environnement Visual C++ vérifie les dépendances dans et entre les projets. Chaque projet contient du code source de base et, selon son type projet, un projet peut contenir divers autres fichiers correspondant aux différents aspects du projet. Le contenu de ces fichiers est indiqué par l'extension de fichier. L'environnement de développement Visual Studio tient compte des extensions de fichiers pour traiter le contenu des fichiers pendant la génération.  
  
 Le tableau suivant présente les fichiers courants d'un projet Visual C++ et les identifie à partir de leur extension de fichier.  
  
|Extension de fichier|Type|Sommaire|  
|--------------------|----------|--------------|  
|.asmx|Source|Fichier de déploiement.|  
|.asp|Source|Fichier ASP (Active Server Page).|  
|.atp|Projet|Fichier projet de modèle d'application.|  
|.bmp, .dib, .gif, .jpg, .jpe, .png|Ressource|Fichiers image généraux.|  
|.bsc|Compilation|Fichier de code d'explorateur.|  
|.cpp ; .c|Source|Fichiers de code source principaux de votre application.|  
|.cur|Ressource|Fichier graphique de bitmap de curseur.|  
|.dbp|Projet|Fichier projet de base de données.|  
|.disco|Source|Fichier document de découverte dynamique. Gère la découverte des services web XML.|  
|.exe, .dll|Projet|Fichiers exécutables ou de bibliothèque de liens dynamiques.|  
|.h|Source|Fichier d'en-tête (include).|  
|.htm, .html, .xsp, .asp, .htc, .hta, .xml|Ressource|Fichiers web communs.|  
|.HxC|Projet|Fichier projet d'aide.|  
|.ico|Ressource|Fichier graphique de bitmap d'icône.|  
|.idb|Compilation|Fichier d'état contenant des informations de dépendance entre les fichiers sources et les définitions de classe, qui peuvent être utilisés par le compilateur durant la régénération minimale et la compilation incrémentielle. Utilisez l'option de compilateur [/Fd](../build/reference/fd-program-database-file-name.md) pour spécifier le nom du fichier .idb. Pour plus d'informations, consultez [/Gm (Activer la régénération minimale)](../build/reference/gm-enable-minimal-rebuild.md) .|  
|.idl|Compilation|Fichier de langage de définition d'interface. Pour plus d’informations, consultez [Fichier IDL (Interface Definition Language)](http://msdn.microsoft.com/library/windows/desktop/aa378712) dans le SDK Windows.|  
|.ilk|Liaison|Fichier de liaison incrémentielle. Pour plus d'informations, consultez [/INCREMENTAL](../build/reference/incremental-link-incrementally.md) .|  
|.map|Liaison|Fichier texte contenant des informations sur l'éditeur de liens. Utilisez l'option de compilateur [/Fm](../build/reference/fm-name-mapfile.md) pour nommer le fichier .map. Pour plus d'informations, consultez [/MAP](../build/reference/map-generate-mapfile.md) .|  
|.mfcribbon-ms|Ressource|Fichier de ressources contenant le code XML qui définit boutons, contrôles et attributs du ruban. Pour plus d'informations, consultez [Ribbon Designer (MFC)](../mfc/ribbon-designer-mfc.md).|  
|.obj, .o||Fichiers objets, compilés mais sans liens.|  
|.pch|Débogage|Fichier d'en-tête précompilé.|  
|.rc, .rc2|Ressource|[Fichiers de script de ressources](../windows/working-with-resource-files.md) pour générer des ressources.|  
|.sbr|Compilation|Fichier intermédiaire d'explorateur de source. Fichier d'entrée de [BSCMAKE](../build/reference/bscmake-options.md).|  
|.sln|Solution|Fichier [solution](http://msdn.microsoft.com/en-us/a45c299d-69f5-4b67-879d-1383417df0a7) .|  
|.suo|Solution|Fichier d'options de solution.|  
|.txt|Ressource|Fichier texte, généralement le fichier « Lisez-moi ».|  
|.vap|Projet|Fichier projet Visual Studio Analyzer.|  
|.vbg|Solution|Fichier de groupe de projets compatible.|  
|.vbp, .vip, .vbproj|Projet|Fichier projet Visual Basic.|  
|.vcxitems|Projet|Projet d’éléments partagés permettant de partager des fichiers de code entre plusieurs projets C++. Pour plus d'informations, consultez [Fichiers projet et Makefiles](../ide/project-and-solution-files.md) .|
|.vcxproj|Projet|Fichier projet Visual C++. Pour plus d'informations, consultez [Fichiers projet et Makefiles](../ide/project-and-solution-files.md) .|  
|.vcxproj.filters|Projet|Quand vous ajoutez un fichier à un projet via l'Explorateur de solutions, le fichier de filtres détermine à quel emplacement le fichier est ajouté dans l'arborescence de l'Explorateur de solutions, en fonction de son extension de nom de fichier.|  
|.vdproj|Projet|Fichier projet de déploiement Visual Studio.|  
|.vmx|Projet|Fichier projet de macro.|  
|.vup|Projet|Fichier projet d'utilitaire.|  
  
 Pour plus d'informations sur les autres fichiers associés à Visual Studio, consultez [Types de fichiers et extensions de fichiers dans Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).  
  
 Les fichiers projet sont organisés en dossiers dans l'Explorateur de solutions. Visual C++ crée un dossier pour les fichiers sources, les fichiers d'en-tête et les fichiers de ressources, mais vous pouvez réorganiser ces dossiers ou en créer de nouveaux. Vous pouvez utiliser des dossiers pour organiser explicitement des clusters logiques de fichiers au sein de la hiérarchie d'un projet. Par exemple, vous pouvez créer des dossiers dans le but d'y déposer tous les fichiers sources de votre interface utilisateur, les spécifications, la documentation ou des suites de tests. Tous les noms de dossiers de fichiers doivent être uniques.  
  
 Quand vous ajoutez un élément à un projet, vous l'ajoutez à toutes les configurations de ce projet, que cet élément puisse ou non être généré. Par exemple, si vous avez un projet nommé MonProjet et que vous y ajoutez un élément, cet élément est ajouté aux configurations de projet Debug et Release.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion de projets Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)   
 [Types de projets Visual C++](../ide/visual-cpp-project-types.md)   
 [Prise en charge d’autres langues par l’Assistant](../ide/wizard-support-for-other-languages.md)