---
title: Définir le compilateur C++ et les propriétés de build dans Visual Studio
description: Utilisez l’IDE de Visual Studio pour modifier les options du compilateur C++ et de l’éditeur de liens, ainsi que d’autres paramètres de génération.
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 3ee6b21cc1bcb8e33bc76d2efab58808bfc0aa2b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589872"
---
# <a name="set-compiler-and-build-properties"></a>Définir des propriétés de build et de compilateur

Dans l’IDE, toutes les informations nécessaires pour générer un projet sont exposées sous forme de *propriétés*. Ces informations comprennent le nom de l’application, l’extension (par exemple, DLL, LIB, EXE), les options de compilateur, les options de l’éditeur de liens, les paramètres de débogueur, les étapes de génération personnalisée et bien d’autres choses. En général, vous utilisez les *pages de propriétés* pour afficher et modifier ces propriétés. Pour accéder aux pages de propriétés, choisissez Propriétés du **projet**  >  **_ProjectName_ ** dans le menu principal, ou cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Propriétés**.

## <a name="default-properties"></a>Propriétés par défaut

Quand vous créez un projet, le système attribue des valeurs à différentes propriétés. Les valeurs par défaut varient légèrement en fonction du type de projet et des options que vous choisissez dans l’Assistant Application. Par exemple, un projet ATL a des propriétés relatives aux fichiers MIDL, mais elles sont absentes dans une application console de base. Les propriétés par défaut sont affichées dans le volet Général des pages de propriétés :

![Valeurs par défaut du projet Visual C&#43;&#43; ](media/visual-c---project-defaults.png "Visual C++ les paramètres par défaut du projet")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Application de propriétés aux configurations de build et aux plateformes cibles

Certaines propriétés, comme le nom de l’application, s’appliquent à toutes les variations de build, quelle que soit la plateforme cible, ou qu’il s’agisse d’une build debug ou release. Toutefois, la plupart des propriétés dépendent de la configuration. C’est parce que le compilateur doit connaître la plateforme sur laquelle le programme va s’exécuter ainsi que les options de compilateur à utiliser pour générer le code approprié. Par conséquent, quand vous définissez une propriété, faites bien attention à la configuration et à la plateforme auxquelles la nouvelle valeur doit s’appliquer. Doit-elle s’appliquer uniquement aux builds Debug Win32 ou aussi à Debug ARM et Debug x64 ? Par exemple, la propriété **Optimisation** est définie par défaut sur **Augmenter la vitesse (/O2)** dans une configuration Release, mais est désactivée dans la configuration Debug.

Les pages de propriétés sont conçues pour vous permettre de toujours voir, et si nécessaire modifier, la configuration et la plateforme auxquelles une valeur de propriété doit s’appliquer. L’illustration suivante montre les pages de propriétés avec les informations de configuration et de plateforme dans les zones de liste en haut. Quand la propriété **Optimisation** est définie ici, elle s’applique uniquement aux builds Debug Win32, qui est la configuration active, comme indiqué par les flèches rouges.

![Pages de propriétés de&#43;&#43; Visual C présentant une configuration active](media/visual-c---property-pages-showing-active-configuration.png "Pages de propriétés de Visual C++ présentant une configuration active")

L’illustration suivante montre la même page de propriétés de projet, mais la configuration a été remplacée par Release. Notez le changement de valeur de la propriété Optimisation. Notez également que la configuration active est toujours Debug. Vous pouvez définir ici les propriétés de n’importe quelle configuration, et pas seulement celles de la configuration active.

![Pages de propriétés de&#43;&#43; Visual C présentant la configuration Release](media/visual-c---property-pages-showing-release-config.png "Pages de propriétés de Visual C++ présentant la configuration Release")

## <a name="target-platforms"></a>Plateformes cibles

*Plateforme cible* fait référence au type d’appareil et/ou de système d’exploitation sur lequel doit s’exécuter l’exécutable. Vous pouvez générer un projet pour plusieurs plateformes. Les plateformes cibles disponibles pour les projets C++ varient selon le type de projet et sont entre autres : Win32, x64, ARM, Android et iOS.     La plateforme cible **x86** que vous pouvez voir dans le **Gestionnaire de configuration** est identique à **Win32** dans les projets C++ natifs. Win32 désigne Windows 32 bits et **x64** désigne Windows 64 bits. Pour plus d’informations sur ces deux plateformes, consultez [Exécution d’applications 32 bits](/windows/win32/WinProg64/running-32-bit-applications).

La valeur de plateforme cible **N’importe quelle UC** que vous pouvez voir dans le **Gestionnaire de configuration** n’a aucun effet sur les projets C++ natifs, elle concerne les projets C++/ CLI et d’autres types de projet .NET. Pour plus d’informations, consultez l’article [/CLRIMAGETYPE (Spécifier le type d’une image CLR)](reference/clrimagetype-specify-type-of-clr-image.md).

Pour plus d’informations sur la définition des propriétés d’une version Debug, consultez :

- [Paramètres de projet pour une configuration Debug C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Paramètres et préparation du débogueur](/visualstudio/debugger/debugger-settings-and-preparation)
- [Préparation du débogage : types de projets Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Spécifiez les fichiers de symbole (.pdb) et les fichiers source dans le débogueur Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>Options du compilateur C++ et de l’éditeur de liens

Les options du compilateur c++ et de l’éditeur de liens se trouvent sous les nœuds **C/c++** et **éditeur de liens** dans le volet gauche sous **Propriétés de configuration**. Celles-ci se traduisent directement par des options de ligne de commande qui seront passées au compilateur. Pour lire la documentation relative à une option spécifique, sélectionnez l’option dans le volet central et appuyez sur **F1**. Ou, vous pouvez parcourir la documentation de toutes les options disponibles dans [Options du compilateur MSVC](reference/compiler-options.md) et options de l' [éditeur de liens MSVC](reference/linker-options.md).

La boîte de dialogue **pages de propriétés** affiche uniquement les pages de propriétés pertinentes pour le projet actuel. Par exemple, si le projet n'a pas de fichier .idl, la page de propriétés MIDL n'est pas affichée. Pour plus d’informations sur le paramètre de chaque page de propriétés, consultez [pages de propriétés (C++)](reference/property-pages-visual-cpp.md).

## <a name="directory-and-path-values"></a>Valeurs de répertoire et de chemin d’accès

MSBuild prend en charge l’utilisation de constantes au moment de la compilation appelées « macros » pour certaines valeurs de chaîne, notamment les répertoires et les chemins d’accès. Celles-ci sont exposées dans les pages de propriétés, où vous pouvez vous y référer et les modifier à l’aide de l' [éditeur de propriétés](#property_editor).

L’illustration suivante montre les pages de propriétés d’un projet Visual Studio C++. Dans le volet gauche, la **règle** *Répertoires VC++* est sélectionnée et le volet droit répertorie les propriétés associées à cette règle. Les `$(...)` valeurs sont appelées *macros*. Une *macro* est une constante de compilation qui peut référencer une valeur définie par Visual Studio ou le système MSBuild, ou une valeur définie par l’utilisateur. En utilisant des macros au lieu de valeurs codées en dur telles que les chemins d’accès aux répertoires, vous pouvez partager plus facilement les paramètres des propriétés entre les ordinateurs et entre les versions de Visual Studio, et vous pouvez mieux vous assurer que les paramètres de votre projet participent correctement à l' [héritage de propriété](project-property-inheritance.md).

![Pages de propriétés du projet](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Vous pouvez utiliser l’éditeur de propriétés pour voir les valeurs de toutes les macros disponibles.

### <a name="predefined-macros"></a>Macros prédéfinies

*macros globales*<br/>
S'applique à tous les éléments dans une configuration de projet. Possède la syntaxe `$(name)`. Un exemple de macro globale est `$(VCInstallDir)`, qui stocke le répertoire racine de votre installation de Visual Studio. Une macro globale correspond à `PropertyGroup` dans MSBuild.

*macros d’élément*<br/>
Possède la syntaxe `%(name)`. Pour un fichier, une macro d'élément s'applique uniquement à ce fichier ; par exemple, vous pouvez utiliser `%(AdditionalIncludeDirectories)` pour spécifier les répertoires Include qui s'appliquent uniquement à un fichier particulier. Ce genre de macro d'élément correspond à des métadonnées `ItemGroup` dans MSBuild. Lorsqu'elle est utilisée dans le contexte d'une configuration de projet, une macro d'élément s'applique à tous les fichiers d'un certain type. Par exemple, la propriété de configuration des **définitions de préprocesseur** C/C++ peut prendre une `%(PreprocessorDefinitions)` macro d’élément qui s’applique à tous les fichiers. cpp du projet. Ce genre de macro d'élément correspond à des métadonnées `ItemDefinitionGroup` dans MSBuild. Pour plus d’informations, consultez [définitions d’éléments](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>macros définies par l'utilisateur

Vous pouvez créer des *macros définies par l’utilisateur* à utiliser comme variables dans les générations de projet. Par exemple, vous pouvez créer une macro définie par l'utilisateur qui fournit une valeur pour une étape de génération personnalisée ou un outil de génération personnalisée. Une macro définie par l'utilisateur est une paire nom/valeur. Dans un fichier projet, utilisez la notation **$(**<em>nom</em>**)** pour accéder à la valeur.

Une macro définie par l’utilisateur est stockée dans une feuille de propriétés. Si votre projet ne contient pas encore de feuille de propriétés, vous pouvez en créer un en suivant les étapes décrites dans [partager ou réutiliser des paramètres de projet Visual Studio](create-reusable-property-configurations.md).

#### <a name="to-create-a-user-defined-macro"></a>Pour créer une macro définie par l’utilisateur

1. Ouvrez la fenêtre **Gestionnaire de propriétés** . (Dans la barre de menus, choisissez **Afficher**  >  **Gestionnaire de propriétés** ou **Afficher**d'  >  **autres**  >  **Gestionnaire de propriétés**Windows.) Ouvrez le menu contextuel d’une feuille de propriétés (son nom se termine par. User), puis choisissez **Propriétés**. La boîte de dialogue **Pages de propriétés** pour cette feuille de propriétés s’ouvre.

1. Dans le volet gauche de la boîte de dialogue, sélectionnez **macros utilisateur**. Dans le volet droit, choisissez le bouton **Ajouter une macro** pour ouvrir la boîte de dialogue **Ajouter une macro utilisateur**.

1. Dans la boîte de dialogue, spécifiez un nom et une valeur pour la macro. Si vous le souhaitez, activez la case à cocher **définir cette macro en tant que variable d’environnement dans l’environnement de build** .

## <a name=""></a><a name="property_editor">Éditeur de propriétés</a>

Vous pouvez utiliser l'Éditeur de propriétés pour modifier certaines propriétés de type chaîne et sélectionner des macros comme valeurs. Pour accéder à l'Éditeur de propriétés, sélectionnez une propriété dans une page de propriétés, puis cliquez sur la flèche vers le bas située à droite. Si la liste déroulante contient **\<Edit>** , vous pouvez la choisir pour afficher l’éditeur de propriétés pour cette propriété.

![Un contrôle déroulant de propriété est utilisé pour accéder à l’éditeur de propriétés](media/property_editor_dropdown.png "Liste déroulante de l’éditeur de propriétés")

Dans l’éditeur de propriétés, vous pouvez choisir le bouton **macros** pour afficher les macros disponibles et leurs valeurs actuelles. L’illustration suivante montre l’Éditeur de propriétés pour la propriété **Autres répertoires Include** après la sélection du bouton **Macros**. Lorsque la case à cocher **hériter des paramètres par défaut du parent ou du projet** est activée et que vous ajoutez une nouvelle valeur, elle est ajoutée à toutes les valeurs qui sont actuellement héritées. Si vous désactivez la case à cocher, votre nouvelle valeur remplace les valeurs héritées. Dans la plupart des cas, laissez la case à cocher activée.

![Boîte de dialogue de l’éditeur de propriétés pour la propriété répertoires Include](media/propertyeditorvc.png "PropertyEditorVC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Ajouter un répertoire include au jeu de répertoires par défaut

Lorsque vous ajoutez un répertoire Include à un projet, il est important de ne pas remplacer tous les répertoires par défaut. La méthode appropriée pour ajouter un répertoire est d’ajouter le nouveau chemin, par exemple, "C:\MyNewIncludeDir\", puis la macro **$(IncludePath)** à la valeur de propriété.

## <a name="quickly-browse-and-search-all-properties"></a>Parcourir et rechercher rapidement toutes les propriétés

La page de propriétés **Toutes les options** (sous le nœud **Propriétés de configuration &#124; C/C++** dans la boîte de dialogue **Pages de propriétés**) offre un mode de navigation et de recherche rapide dans les propriétés disponibles au sein du contexte actuel. Elle comporte une zone de recherche spéciale et possède une syntaxe simple pour aider à filtrer les résultats :

Aucun préfixe :<br/>
Effectuer une recherche dans les noms de propriétés uniquement (la sous-chaîne ne respecte pas la casse).

'/' ou '-' :<br/>
Effectuer une recherche uniquement dans les commutateurs de compilation (le préfixe ne respecte pas la casse)

v :<br/>
Effectuer une recherche uniquement dans les valeurs (la sous-chaîne ne respecte pas la casse).

## <a name="set-environment-variables-for-a-build"></a>Définir des variables d’environnement pour une build

Le compilateur MSVC (cl.exe) reconnaît certaines variables d’environnement, plus spécifiquement LIB, LIBPATH, PATH et INCLUDe. Lorsque vous générez avec l’IDE, les propriétés définies dans la page de propriétés de la page de propriétés [Répertoires VC + +](reference/vcpp-directories-property-page.md) sont utilisées pour définir ces variables d’environnement. Si les valeurs LIB, LIBPATH et INCLUDE ont déjà été définies, par exemple par une invite de commandes développeur, elles sont remplacées par les valeurs des propriétés MSBuild correspondantes. La génération ajoute ensuite la valeur de la propriété de répertoires d'exécutables Répertoires VC++ à PATH. Vous pouvez définir une variable d’environnement définie par l’utilisateur en créant une macro définie par l’utilisateur, puis en activant la case à cocher **définir cette macro en tant que variable d’environnement dans l’environnement de génération**.

## <a name="set-environment-variables-for-a-debugging-session"></a>Définir des variables d’environnement pour une session de débogage

Dans le volet gauche de la boîte de dialogue **pages de propriétés** du projet, développez propriétés de **configuration** , puis sélectionnez **débogage**.

Dans le volet droit, modifiez les paramètres de projet **environnement** ou fusion de l' **environnement** , puis choisissez le bouton **OK** .

## <a name="in-this-section"></a>Dans cette section

[Partager ou réutiliser les paramètres de projet Visual Studio](create-reusable-property-configurations.md)<br/>
Comment créer un fichier. props avec des paramètres de build personnalisés qui peuvent être partagés ou réutilisés.

[Héritage de propriétés de projet](project-property-inheritance.md)<br/>
Décrit l’ordre d’évaluation des fichiers. props,. targets,. vcxproj et des variables d’environnement dans le processus de génération.

[Modifier les propriétés et les cibles sans changer le fichier projet](modify-project-properties-without-changing-project-file.md)<br/>
Comment créer des paramètres de build temporaires sans avoir à modifier un fichier projet.

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](creating-and-managing-visual-cpp-projects.md)<br/>
[Structure des fichiers .vcxproj et .props](reference/vcxproj-file-structure.md)<br/>
[Fichiers XML des pages de propriétés](reference/property-page-xml-files.md)<br/>
