---
title: Types de fichiers créés pour les C++ projets Visual Studio
ms.date: 04/08/2019
helpviewer_keywords:
- header files [C++], Visual Studio projects
- ActiveX controls [C++], Help files
- def files
- project items [C++], files
- Visual Studio C++ projects, files and directories
- resource files, created by wizard
- files [C++], extensions
- Help files, for ActiveX controls
- Web projects [C++], adding items
- .def files
- licensing ActiveX controls
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
ms.openlocfilehash: 078c83a9c95c1b143af2037240d5cc0a16211827
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492871"
---
# <a name="file-types-created-for-visual-studio-c-projects"></a>Types de fichiers créés pour les C++ projets Visual Studio

De nombreux types de fichiers sont associés à des projets Visual Studio pour les applications de bureau classiques. Les fichiers réellement inclus dans votre projet varient en fonction du type de projet et des options que vous sélectionnez quand vous utilisez un Assistant.

- [Fichiers projet et solution](project-and-solution-files.md)

- [Projets CLR](files-created-for-clr-projects.md)

- [Fichiers d’en-tête et fichiers sources de contrôle ou de programme ATL](atl-program-or-control-source-and-header-files.md)

- [Fichiers d'en-tête et fichiers sources de contrôle ou de programme MFC](mfc-program-or-control-source-and-header-files.md)

- [Fichiers d'en-tête précompilés](../creating-precompiled-header-files.md)

- [Fichiers de ressources](resource-files-cpp.md)

- [Fichiers d’aide (WinHelp)](help-files-winhelp.md)

- [Fichiers hint](hint-files.md)

Lorsque vous créez un projet Visual Studio, vous pouvez le créer dans une nouvelle solution, ou vous pouvez ajouter un projet à une solution existante. Les applications élaborées sont généralement développées avec plusieurs projets dans une même solution.

En règle générale, les projets produisent un EXE ou une DLL. Les projets peuvent être dépendants les uns des autres; pendant le processus de génération, l’environnement Visual Studio vérifie les dépendances dans et entre les projets. Chaque projet a généralement le code source principal. Selon le type de projet, il peut avoir de nombreux autres fichiers contenant différents aspects du projet. Le contenu de ces fichiers est indiqué par l'extension de fichier. L'environnement de développement Visual Studio tient compte des extensions de fichiers pour traiter le contenu des fichiers pendant la génération.

Le tableau suivant présente les fichiers courants d’un projet Visual Studio et les identifie avec leur extension de fichier.

|Extension de fichier|Type|Sommaire|
|--------------------|----------|--------------|
|.asmx|Source|Fichier de déploiement.|
|.asp|source|Fichier ASP (Active Server Page).|
|.atp|Projet|Fichier projet de modèle d'application.|
|.bmp, .dib, .gif, .jpg, .jpe, .png|Ressource|Fichiers image généraux.|
|.bsc|Compilation|Fichier de code d'explorateur.|
|.cpp, .c|source|Fichiers de code source principaux de votre application.|
|.cur|Ressource|Fichier graphique de bitmap de curseur.|
|.dbp|Projet|Fichier projet de base de données.|
|.disco|source|Fichier document de découverte dynamique. Gère la découverte des services web XML.|
|.exe, .dll|Projet|Fichiers exécutables ou de bibliothèque de liens dynamiques.|
|.h|source|Fichier d'en-tête (include).|
|.htm, .html, .xsp, .asp, .htc, .hta, .xml|Ressource|Fichiers web communs.|
|.HxC|Projet|Fichier projet d'aide.|
|.ico|Ressource|Fichier graphique de bitmap d'icône.|
|.idb|Compilation|Fichier d’état contenant des informations de dépendance entre les fichiers sources et les définitions de classe. Il peut être utilisé par le compilateur lors de la compilation incrémentielle. Utilisez l'option de compilateur [/Fd](fd-program-database-file-name.md) pour spécifier le nom du fichier .idb.|
|.idl|Compilation|Fichier de langage de définition d'interface. Pour plus d’informations, consultez [Fichier IDL (Interface Definition Language)](/windows/win32/Rpc/the-interface-definition-language-idl-file) dans le SDK Windows.|
|.ilk|Liaison|Fichier de liaison incrémentielle. Pour plus d’informations, consultez [/INCREMENTAL](incremental-link-incrementally.md).|
|.map|Liaison|Fichier texte contenant des informations sur l'éditeur de liens. Utilisez l'option de compilateur [/Fm](fm-name-mapfile.md) pour nommer le fichier .map. Pour plus d’informations, consultez [/Map](map-generate-mapfile.md).|
|.mfcribbon-ms|Ressource|Fichier de ressources qui contient le code XML qui définit les boutons, les contrôles et les attributs MFC dans le ruban. Pour plus d'informations, consultez [Ribbon Designer](../../mfc/ribbon-designer-mfc.md).|
|.obj, .o||Fichiers objets, compilés mais sans liens.|
|.pch|Débogage|Fichier d'en-tête précompilé.|
|.rc, .rc2|Ressource|[Fichiers de script de ressources](../../windows/working-with-resource-files.md) pour générer des ressources.|
|.sbr|Compilation|Fichier intermédiaire d'explorateur de source. Fichier d'entrée de [BSCMAKE](bscmake-options.md).|
|.sln|Solution|Fichier [solution](/visualstudio/ide/solutions-and-projects-in-visual-studio) .|
|.suo|Solution|Fichier d'options de solution.|
|.txt|Ressource|Fichier texte, généralement le fichier « Lisez-moi ».|
|.vap|Projet|Fichier projet Visual Studio Analyzer.|
|.vbg|Solution|Fichier de groupe de projets compatible.|
|.vbp, .vip, .vbproj|Projet|Fichier projet Visual Basic.|
|.vcxitems|Projet|Projet d’éléments partagés permettant de partager des fichiers de code entre plusieurs projets C++. Pour plus d’informations, consultez [fichiers projet et solution](project-and-solution-files.md).|
|.vcxproj|Projet|Fichier projet Visual Studio. Pour plus d’informations, consultez [fichiers projet et solution](project-and-solution-files.md).|
|.vcxproj.filters|Projet|Utilisé lorsque vous utilisez Explorateur de solutions pour ajouter un fichier à un projet. Le fichier de filtres définit l’emplacement dans l’arborescence Explorateur de solutions pour ajouter le fichier, en fonction de son extension de nom de fichier.|
|.vdproj|Projet|Fichier projet de déploiement Visual Studio.|
|.vmx|Projet|Fichier projet de macro.|
|.vup|Projet|Fichier projet d'utilitaire.|

Pour plus d'informations sur les autres fichiers associés à Visual Studio, consultez [Types de fichiers et extensions de fichiers dans Visual Studio .NET](/visualstudio/ide/reference/project-and-solution-file-types).

Les fichiers projet sont organisés en dossiers dans l'Explorateur de solutions. Visual Studio crée un dossier pour les fichiers sources, les fichiers d’en-tête et les fichiers de ressources, mais vous pouvez réorganiser ces dossiers ou en créer d’autres. Vous pouvez utiliser des dossiers pour organiser explicitement des clusters logiques de fichiers au sein de la hiérarchie d'un projet. Par exemple, vous pouvez créer des dossiers pour contenir tous les fichiers sources de l’interface utilisateur. Ou des dossiers pour des spécifications, de la documentation ou des suites de tests. Tous les noms de dossiers de fichiers doivent être uniques.

Lorsque vous ajoutez un élément à un projet, vous ajoutez l’élément à toutes les configurations de ce projet. L’élément est ajouté s’il peut être généré ou non. Par exemple, si vous avez un projet nommé MonProjet et que vous y ajoutez un élément, cet élément est ajouté aux configurations de projet Debug et Release.

## <a name="see-also"></a>Voir aussi

[Création et gestion de projets C++ Visual Studio](../creating-and-managing-visual-cpp-projects.md)<br>
[Types de C++ projets Visual Studio](visual-cpp-project-types.md)<br>