---
title: Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande - Visual Studio
description: Utilisez la chaîne d’outils du compilateur Microsoft C++ (MSVC) à partir de la ligne de commande en dehors de l’environnement de développement intégré (IDE) Visual Studio.
ms.custom: conceptual
ms.date: 05/16/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 97626455ace0d3ad47b9011594e82c144d7ea27d
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837127"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande

Vous pouvez générer des applications C et C++ sur la ligne de commande en utilisant les outils inclus dans Visual Studio. Vous pouvez aussi télécharger l’ensemble d’outils du compilateur sous forme de package autonome à partir de la page des [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/). Celui-ci fait partie du package **Build Tools for Visual Studio**. Vous pouvez choisir de télécharger uniquement les outils dont vous avez besoin pour le développement C++.

## <a name="how-to-use-the-command-line-tools"></a>Comment utiliser les outils en ligne de commande

Quand vous choisissez l’une des charges de travail C++ dans Visual Studio Installer, l’*ensemble d’outils de plateforme* Visual Studio est installé. Un ensemble d’outils de plateforme comprend tous les outils C et C++ propres à une version spécifique de Visual Studio, notamment les compilateurs, les éditeurs de liens, les assembleurs et d’autres outils de build C/C++, ainsi que les bibliothèques correspondantes. Vous pouvez utiliser tous ces outils à partir de la ligne de commande. Notez qu’ils sont également utilisés en interne par l’IDE Visual Studio. Il existe des compilateurs et outils hébergés x86 et x64 distincts pour générer du code pour des cibles x86, x64, ARM et ARM64. Chaque ensemble d’outils propre à une architecture de build hôte et cible particulière est stocké dans son propre répertoire.

Les ensembles d’outils du compilateur installés dépendent du processeur de l’ordinateur et des options sélectionnées pendant l’installation. Au minimum sont installés les outils 32 bits hébergés x86 qui génèrent du code natif x86 32 bits et les outils croisés qui génèrent du code natif x64 64 bits. Si vous utilisez Windows 64 bits, sont également installés les outils 64 bits hébergés x64 qui génèrent du code natif 64 bits et les outils croisés qui génèrent du code natif 32 bits. Si vous choisissez d’installer les outils de plateforme Windows universelle (UWP) C++ facultatifs, alors les outils natifs 32 bits et 64 bits qui génèrent du code ARM sont également installés. D’autres charges de travail peuvent installer d’autres outils.

## <a name="environment-variables-and-developer-command-prompts"></a>Variables d’environnement et invites de commandes développeur

Pour fonctionner correctement, les outils nécessitent de définir plusieurs variables d’environnement spécifiques. Celles-ci sont utilisées pour les ajouter au chemin et définir un fichier Inclure, un fichier de bibliothèque et les emplacements du SDK. Pour faciliter la définition de ces variables d’environnement, le programme d’installation crée des *fichiers de commandes* personnalisés lors de l’installation. Vous pouvez exécuter l’un de ces fichiers de commandes dans une fenêtre d’invite de commandes pour définir une architecture de build hôte et cible spécifique, une version du SDK Windows, une plateforme cible et un ensemble d’outils de plateforme. Par souci pratique, le programme d’installation crée également des raccourcis dans votre menu Démarrer qui permettent d’ouvrir des fenêtres d’invite de commandes développeur à l’aide de ces fichiers de commandes, pour que toutes les variables d’environnement nécessaires soient définies et prêtes à l’emploi.

Les variables d’environnement nécessaires sont propres à votre installation et à l’architecture de build qui vous choisissez. Elles sont susceptibles d’être modifiées par des mises à niveau ou des mises à jour du produit. Par conséquent, nous recommandons vivement d’utiliser l’un des raccourcis d’invite de commandes ou des fichiers de commandes installés au lieu de définir vous-même les variables d’environnement dans Windows. Pour plus d’informations, consultez [Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="developer_command_prompt_shortcuts"></a> Raccourcis d’invite de commandes développeur

Les raccourcis d’invite de commandes sont installés dans un dossier propre à la version de Visual Studio dans votre menu Démarrer. Voici la liste des principaux raccourcis d’invite de commandes et des architectures de build prises en charge :

- **Invite de commandes développeur** : définit l’environnement pour utiliser des outils natifs x86 32 bits pour générer du code natif x86 32 bits.
- **Invite de commandes des outils natifs x86** : définit l’environnement pour utiliser des outils natifs x86 32 bits pour générer du code natif x86 32 bits.
- **Invite de commandes des outils natifs x64** : définit l’environnement pour utiliser des outils natifs x64 64 bits pour générer du code natif x64 64 bits.
- **Invite de commandes des outils croisés x86_x64** : définit l’environnement pour utiliser des outils natifs x86 32 bits pour générer du code natif x64 64 bits.
- **Invite de commandes des outils croisés x64_x86** : définit l’environnement pour utiliser des outils natifs x64 64 bits pour générer du code natif x86 32 bits.

Les noms du dossier du menu Démarrer et des raccourcis varient selon la version de Visual Studio que vous avez installée et le surnom de l’installation si vous en avez défini un. Par exemple, si vous avez installé Visual Studio 2019 et que vous avez surnommé son installation *Préversion*, le raccourci de l’invite de commandes développeur se nomme **Invite de commandes développeur pour VS 2019** dans un dossier nommé **Visual Studio 2019**.

## <a name="developer_command_prompt"></a> Pour ouvrir une fenêtre d’invite de commandes développeur

1. Sur le bureau, ouvrez le menu **Démarrer** de Windows, puis faites-le défiler pour trouver et ouvrir le dossier correspondant à votre version de Visual Studio, par exemple, **Visual Studio 2019**. Dans certaines versions antérieures de Visual Studio, les raccourcis se trouvent dans un sous-dossier appelé **Visual Studio Tools**.

1. Dans le dossier, choisissez le raccourci **Invite de commandes développeur** de votre version de Visual Studio. Ce raccourci ouvre une fenêtre d’invite de commandes développeur qui utilise l’architecture de build par défaut des outils natifs x86 32 bits pour générer du code natif x86 32 bits. Si vous préférez une architecture de build autre que celle par défaut, choisissez l’une des invites de commandes des outils natifs ou croisés pour spécifier l’architecture hôte et cible.

Un moyen encore plus rapide d’ouvrir une fenêtre d’invite de commandes développeur consiste à entrer *invite de commandes développeur* dans la zone de recherche du Bureau, puis à choisir le résultat souhaité.

## <a name="developer_command_file_locations"></a> Emplacements des fichiers de commandes développeur

Si vous préférez définir l’environnement de l’architecture de build dans une fenêtre d’invite de commandes existante, vous pouvez utiliser l’un des fichiers de commandes créés par le programme d’installation. Nous vous recommandons de faire ce choix uniquement dans une nouvelle fenêtre d’invite de commandes et nous vous déconseillons de changer ultérieurement d’environnement dans la même fenêtre Commande. L’emplacement de ces fichiers dépend de la version de Visual Studio que vous avez installée, ainsi que de l’emplacement et des choix de noms effectués pendant l’installation. Pour Visual Studio 2019, l’emplacement d’installation par défaut sur un ordinateur 64 bits est \Program Files (x86)\Microsoft Visual Studio\2019\*édition*, où *édition* peut être Community, Professional, Enterprise, BuildTools ou tout autre nom que vous avez indiqué. L’emplacement de Visual Studio 2017 est similaire. Pour Visual Studio 2015, l’emplacement d’installation par défaut se trouve dans \Program Files (x86) \Microsoft Visual Studio 14.0.

Le fichier de commandes de l’invite de commandes développeur principale, VsDevCmd.bat, se trouve dans le sous-répertoire Common7\Tools du répertoire d’installation. Quand aucun paramètre n’est spécifié, l’environnement et l’architecture de build hôte et cible utilisent les outils natifs x86 32 bits pour générer du code x86 32 bits.

Des fichiers de commandes supplémentaires sont disponibles pour configurer des architectures de build spécifiques, en fonction de l’architecture de votre processeur et des charges de travail et options Visual Studio que vous avez installées. Dans Visual Studio 2017 et Visual Studio 2019, ceux-ci se trouvent dans le sous-répertoire VC\Auxiliary\Build du répertoire d’installation de Visual Studio. Dans Visual Studio 2015, ceux-ci se trouvent dans les sous-répertoires VC, VC\bin ou VC\bin\\*architectures* du répertoire d’installation, où *architectures* correspond à l’une des options du compilateur natives ou croisées. Ces fichiers de commandes définissent les paramètres par défaut et appellent VsDevCmd.bat pour configurer l’environnement de l’architecture de build spécifiée. Une installation classique peut inclure ces fichiers de commandes :

|Fichier de commandes|Architectures hôte et cible|
|---|---|
|**vcvars32.bat**| Utilisent les outils natifs x86 32 bits pour générer du code x86 32 bits.|
|**vcvars64.bat**| Utilisent les outils natifs x64 64 bits pour générer du code x64 64 bits.|
|**vcvarsx86_amd64.bat**| Utilisent les outils croisés natifs x86 32 bits pour générer du code x64 64 bits.|
|**vcvarsamd64_x86.bat**| Utilisent les outils croisés natifs x64 64 bits pour générer du code x86 32 bits.|
|**vcvarsx86_arm.bat**| Utilisent les outils croisés natifs x86 32 bits pour générer du code ARM.|
|**vcvarsamd64_arm.bat**| Utilisent les outils croisés natifs x64 64 bits pour générer du code ARM.|
|**vcvarsall.bat**| Utilisent des paramètres pour spécifier les architectures hôte et cible, ainsi que les choix de plateforme et de SDK. Pour obtenir la liste des options prises en charge, effectuez un appel en utilisant un paramètre **/help**.|

> [!CAUTION]
> Le fichier vcvarsall.bat et d’autres fichiers de commandes Visual Studio peuvent varier d’un ordinateur à l’autre. Ne remplacez pas un fichier vcvarsall.bat manquant ou endommagé en utilisant un fichier provenant d'un autre ordinateur. Réexécutez le programme d’installation de Visual Studio pour remplacer le fichier manquant.
>
> Le fichier vcvarsall.bat varie également d'une version à l'autre. Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, n’exécutez pas vcvarsall.bat ni un autre fichier de commandes Visual Studio à partir de différentes versions dans la même fenêtre d’invite de commandes.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Utiliser les outils de développement dans une fenêtre Commande existante

Le moyen le plus simple de spécifier une architecture de build particulière dans une fenêtre Commande existante consiste à utiliser le fichier vcvarsall.bat. Vous pouvez utiliser vcvarsall.bat premièrement pour définir des variables d’environnement afin de configurer la ligne de commande pour une compilation native 32 bits ou 64 bits, ou pour une compilation croisée sur des processeurs x86, x64 ou ARM, deuxièmement pour cibler Microsoft Store, la plateforme Windows universelle ou les plateformes Windows Desktop, troisièmement pour spécifier quel SDK Windows utiliser et quatrièmement pour spécifier la version de l’ensemble d’outils de plateforme. Si aucun argument n’est fourni, vcvarsall.bat configure les variables d’environnement pour utiliser le compilateur natif 32 bits actuel pour des cibles Windows Desktop x86. Vous pouvez toutefois l’utiliser pour configurer l’un des outils du compilateur natifs ou croisés. Si vous spécifiez une configuration du compilateur qui n’est pas installée ni disponible sur l’architecture de build de votre ordinateur, un message d’erreur s’affiche.

### <a name="vcvarsall-syntax"></a>Syntaxe de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=**_vcversion_]

*architecture*<br/>
Cet argument facultatif spécifie l’architecture hôte et cible à utiliser. Si l’argument *architecture* n’est pas spécifié, l’environnement de build par défaut est utilisé. Ces arguments sont pris en charge :

|*architecture*|Compilateur|Architecture de l’ordinateur hôte|Architecture (cible) de sortie de build|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|natif 32 bits x86|x86, x64|x86|
|**x86\_amd64** ou **x86\_x64**|x64 sur x86 croisé|x86, x64|X64|
|**x86_arm**|ARM sur x86 croisé|x86, x64|ARM|
|**x86_arm64**|ARM64 sur x86 croisé|x86, x64|ARM64|
|**amd64** ou **x64**|x64 64 bits natif|X64|X64|
|**amd64\_x86** ou **x64\_x86**|x86 sur x64 croisé|X64|x86|
|**amd64\_arm** ou **x64\_arm**|ARM sur x64 croisé|X64|ARM|
|**amd64\_arm64** ou **x64\_arm64**|ARM64 sur x64 croisé|X64|ARM64|

*platform_type*<br/>
Cet argument facultatif vous permet de spécifier **store** ou **uwp** en tant que type de plateforme. Par défaut, l’environnement est défini pour générer des applications de bureau ou console.

*winsdk_version*<br/>
Spécifie éventuellement la version du SDK Windows à utiliser. Par défaut, le dernier SDK Windows installé est utilisé. Pour spécifier la version du SDK Windows, vous pouvez utiliser un numéro de SDK Windows 10 complet, comme **10.0.10240.0** ou spécifier **8.1** pour utiliser le SDK Windows 8.1.

*vcversion*<br/>
Spécifie éventuellement l’ensemble d’outils du compilateur Visual Studio à utiliser. Par défaut, l’environnement est défini pour utiliser l’ensemble d’outils du compilateur Visual Studio actuel. Utilisez **-vcvars_ver=14.0** pour spécifier l’ensemble d’outils du compilateur Visual Studio 2015 ou **-vcvars_ver=15.0** pour spécifier l’ensemble d’outils du compilateur Visual Studio 2017.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Pour configurer l’environnement de build dans une fenêtre d’invite de commandes existante

1. À l’invite de commandes, utilisez la commande CD pour accéder au répertoire d’installation de Visual Studio. Ensuite, réutilisez CD pour accéder au sous-répertoire qui contient les fichiers de commandes propres à la configuration. Pour Visual Studio 2017 et Visual Studio 2019, il s’agit du sous-répertoire VC\Auxiliary\Build. Pour Visual Studio 2015, utilisez le sous-répertoire VC.

1. Entrez la commande qui correspond à votre environnement de développement préféré. Par exemple, pour générer du code ARM pour UWP sur une plateforme 64 bits à l’aide du dernier SDK Windows et de l’ensemble d’outils du compilateur Visual Studio 2019, utilisez cette ligne de commande :

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Créer votre propre raccourci d’invite de commandes

Si vous ouvrez la boîte de dialogue Propriétés de l’un des raccourcis d’invite de commandes développeur existants, vous pouvez voir la cible de commande utilisée. Par exemple, la cible du raccourci **Invite de commandes des outils natifs x64 pour VS 2019** ressemble à ceci :

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

Les fichiers de commandes propres à l’architecture définissent le paramètre *architecture* et appellent vcvarsall.bat. Vous pouvez passer les mêmes options supplémentaires à ces fichiers de commandes que celles que vous passez à vcvarsall.bat, ou bien vous pouvez tout simplement appeler vcvarsall.bat directement. Pour spécifier des paramètres pour votre propre raccourci de commande, ajoutez-les à la fin de la commande entre guillemets doubles. Par exemple, pour configurer un raccourci permettant de générer du code ARM pour UWP sur une plateforme 64 bits à l’aide du dernier SDK Windows et d’un ensemble d’outils du compilateur antérieur à celui de la version actuelle, vous devez spécifier le numéro de version. Utilisez quelque chose comme la cible de cette commande dans votre raccourci :

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=15.0"`

Vous devez adapter le chemin pour qu’il reflète celui de votre répertoire d’installation de Visual Studio. Le fichier vcvarsall.bat comporte des informations supplémentaires sur les numéros de versions spécifiques.

## <a name="command-line-tools"></a>Outils en ligne de commande

Pour générer un projet C/C++ sur la ligne de commande, Visual Studio fournit ces outils en ligne de commande :

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilisez le compilateur (cl.exe) pour compiler et lier les fichiers de code source dans les applications, les bibliothèques et les DLL.

[Lien](reference/linking.md)<br/>
Utilisez l'éditeur de liens (link.exe) pour lier les bibliothèques et les fichiers objets compilés dans les applications et les DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Utilisez MSBuild (msbuild.exe) et un fichier projet (.vcxproj) pour configurer une build et appeler l’ensemble d’outils indirectement. Ceci équivaut à exécuter la commande **Générer un projet** ou **Générer la solution** dans l’environnement de développement intégré Visual Studio. L’exécution de MSBuild à partir de la ligne de commande est un scénario avancé qui n’est en général pas recommandé.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Utilisez DEVENV (devenv.exe) en association avec un commutateur de ligne de commande (par exemple, **/Build** ou **/Clean**) pour exécuter certaines commandes de génération sans afficher l’environnement de développement intégré Visual Studio. En général, cet outil est préféré à l’utilisation directe de MSBuild, car vous pouvez laisser Visual Studio gérer les complexités de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Utilisez NMAKE (nmake.exe) sur Windows pour générer des projets C++ basés sur un makefile traditionnel.

Quand vous générez sur la ligne de commande, la commande F1 n’est pas disponible pour une aide instantanée. Au lieu de cela, vous pouvez utiliser un moteur de recherche pour obtenir des informations sur les avertissements, les erreurs et les messages, ou bien vous pouvez utiliser les fichiers d’aide hors connexion. Pour utiliser la recherche dans [docs.microsoft.com](https://docs.microsoft.com/cpp/), entrez votre chaîne de recherche dans la zone de recherche située en haut de la page.

## <a name="in-this-section"></a>Dans cette section

Les articles répertoriés dans cette section de la documentation montrent comment générer des applications sur la ligne de commande. Ils expliquent aussi comment personnaliser l'environnement de build en ligne de commande pour utiliser les ensembles d'outils 64 bits et cibler les plateformes x86, x64 et ARM. Enfin, ils illustrent l'utilisation des outils de génération en ligne de commande MSBuild et NMAKE.

[Procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Fournit un exemple illustrant la création et la compilation un programme C++ simple sur la ligne de commande.

[Procédure pas à pas : compiler un programme C sur la ligne de commande](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Décrit comment compiler un programme écrit dans le langage de programmation C.

[Procédure pas à pas : compilation d’un programme C++/CLI natif sur la ligne de commande](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Décrit comment créer et compiler un programme C++/CLI qui utilise le .NET Framework.

[Procédure pas à pas : compilation d’un programme C++/CX natif sur la ligne de commande](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Décrit comment créer et compiler un programme C++/CX qui utilise le Windows Runtime.

[Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Décrit comment ouvrir une fenêtre d’invite de commandes avec les variables d’environnement nécessaires définies pour des builds sur la ligne de commande ciblant les plateformes x86, x64 et ARM, à l’aide d’un ensemble d’outils 32 bits ou 64 bits.

[NMAKE, référence](reference/nmake-reference.md)<br/>
Fournit des liens vers des articles qui décrivent l'utilitaire Microsoft Program Maintenance Utility (NMAKE.EXE).

[MSBuild sur la ligne de commande - C++](msbuild-visual-cpp.md)<br/>
Fournit des liens vers des articles qui expliquent comment utiliser msbuild.exe à partir de la ligne de commande.

## <a name="related-sections"></a>Rubriques connexes

[/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](reference/md-mt-ld-use-run-time-library.md)<br/>
Décrit comment utiliser ces options de compilateur pour utiliser une bibliothèque runtime Debug ou Release.

[Options du compilateur C/C++](reference/compiler-options.md)<br/>
Fournit des liens vers des articles qui présentent les options de compilateur C et C++, ainsi que CL.exe.

[Options de l’éditeur de liens MSVC](reference/linker-options.md)<br/>
Fournit des liens vers des articles qui présentent les options de l'éditeur de liens et LINK.exe.

[Outils de build MSVC supplémentaires](reference/c-cpp-build-tools.md)<br/>
Fournit des liens vers des outils de build C/C++ inclus dans Visual Studio.

## <a name="see-also"></a>Voir aussi

[Projets et systèmes de build](projects-and-build-systems-cpp.md)