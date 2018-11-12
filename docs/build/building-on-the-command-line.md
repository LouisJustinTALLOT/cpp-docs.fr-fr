---
title: Générer du Code C/C++ sur la ligne de commande
ms.custom: conceptual
ms.date: 06/21/2018
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: bc5080ff14cf8629c98077bf1e3e39e4b824b48b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452037"
---
# <a name="build-cc-code-on-the-command-line"></a>Générer du code C/C++ sur la ligne de commande

Vous pouvez créer des applications C et C++ sur la ligne de commande à l’aide des outils qui sont inclus dans Visual Studio.

## <a name="how-to-get-the-command-line-tools"></a>Comment obtenir les outils de ligne de commande

Lorsque vous choisissez une des charges de travail C++ dans Visual Studio Installer, il installe Visual Studio *ensemble d’outils de plateforme*. Un ensemble d’outils de plateforme dispose d’outils de tous les C et C++ pour une version spécifique de Visual Studio, y compris les compilateurs C/C++, éditeurs de liens, assembleurs et autres outils de génération, ainsi que les bibliothèques correspondantes. Vous pouvez utiliser tous ces outils en ligne de commande, et elles sont également utilisées en interne par l’IDE Visual Studio. Il existe des compilateurs hébergés x86 et hébergés en x64 64 distincts et outils pour générer le code pour x86, x 64, ARM et ARM64 cibles. Chaque ensemble d’outils pour une architecture de build hôte et cible particulière est stockée dans son propre répertoire.

Pour fonctionner correctement, les outils requièrent plusieurs variables d’environnement spécifiques à définir. Ils sont utilisés pour les ajouter au chemin d’accès et comment inclure le fichier, les fichier de bibliothèque et les emplacements du Kit de développement logiciel. Pour faciliter la définir ces variables d’environnement, le programme d’installation crée personnalisé *fichiers de commandes*, ou un groupe de fichiers, lors de l’installation. Vous pouvez exécuter un de ces fichiers de commande dans une fenêtre d’invite de commandes pour définir un hôte spécifique et architecture de build cible version du SDK Windows, plateforme cible et ensemble d’outils de plateforme. Pour plus de commodité, le programme d’installation crée également des raccourcis dans votre menu Démarrer (ou page de démarrage sur Windows 8.x) qui démarre l’invite de commandes de développeur windows à l’aide de ces fichiers de commandes, par conséquent, toutes les variables d’environnement nécessaires sont définie et prête à l’utilisation.

Les variables d’environnement requises sont spécifiques à votre installation et de l’architecture de build que vous choisissez et pouvez être modifiés par les mises à jour de produit ou de mise à niveau. Par conséquent, nous recommandons fortement d’utiliser un des raccourcis d’invite de commandes installée ou des fichiers de commandes au lieu de définir les variables d’environnement dans Windows vous-même. Pour plus d’informations, consultez [définir le chemin d’accès et les Variables d’environnement pour les générations de ligne de commande](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Les ensembles d’outils de ligne de commande, les fichiers de commandes et les raccourcis d’invite de commandes qui sont installés dépendent de votre processeur de l’ordinateur et les options sélectionnées lors de l’installation. Au minimum, les 32 bits hébergé x86 outils générer du code de x86 natif 32 bits et Cross-outils qui génèrent le code de x64 natif 64 bits sont installés. Si vous avez Windows de 64 bits, les outils hébergés en x64 64 64 bits qui générer du code natif 64 bits et croisée des outils qui génèrent du code natif 32 bits sont également installés. Si vous choisissez d’installer les outils de plateforme Windows universelle C++ facultatifs, puis les outils natifs 32 bits et 64 bits qui s’appuient les code ARM sont également installés. Autres charges de travail peuvent installer des outils supplémentaires.

## <a name="developer-command-prompt-shortcuts"></a>Raccourcis d’invite de commandes développeur

Les raccourcis d’invite de commande sont installés dans un dossier de Visual Studio spécifique à la version dans votre menu Démarrer. Voici une liste de raccourcis de l’invite de commandes base et les architectures de build qu'ils prennent en charge :

- **Invite de commandes développeur** -définit l’environnement à utiliser les outils 32 bits, natif x86 pour générer du code 32 bits, natif x86.
- **x86 invite de commandes des outils natifs** -définit l’environnement à utiliser les outils 32 bits, natif x86 pour générer du code 32 bits, natif x86.
- **x64 invite de commandes des outils natifs** -définit l’environnement à utiliser les outils 64 bits, natif x64 pour générer du code 64 bits, natif x64.
- **Invite de commande des outils Cross x86_x64** -définit l’environnement à utiliser les outils 32 bits, natif x86 pour générer du code 64 bits, natif x64.
- **Invite de commande des outils Cross x64_x86** -définit l’environnement à utiliser les outils 64 bits, natif x64 pour générer du code 32 bits, natif x86.

Les véritable Start menu contextuel noms des dossiers et varient selon la version de Visual Studio que vous avez installée et la surnom de l’installation si vous définissez une. Par exemple, si vous avez Visual Studio 2017 est installé et que vous avez étant donné qu’elle une installation de surnom de *aperçu*, le raccourci d’invite de commandes développeur est nommé **invite de commandes développeur pour VS 2017 (version préliminaire)**, dans un dossier nommé **Visual Studio 2017**.

Si vous avez installé le [Build Tools pour Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721) (qui inclut également l’ensemble d’outils du compilateur de Visual Studio 2015 Update 3), uniquement les spécifique de l’architecture native entre différents outils ou invite de commandes développeur options sont installées. et pas le général **invite de commandes développeur** raccourci.

<a name="developer_command_prompt"></a>
### <a name="to-open-a-developer-command-prompt-window"></a>Pour ouvrir une fenêtre d’invite de commandes développeur

1. Sur le bureau, ouvrez le Windows **Démarrer** menu, puis faites défiler pour rechercher et ouvrir le dossier correspondant à votre version de Visual Studio, par exemple, **Visual Studio 2017**. Dans certaines versions antérieures de Visual Studio, les raccourcis sont dans un sous-dossier appelé **Visual Studio Tools**.

1. Dans le dossier, choisissez le **invite de commandes développeur** pour votre version de Visual Studio. Ce raccourci démarre une fenêtre d’invite de commandes de développeur qui utilise l’architecture de build par défaut d’outils 32 bits, natif x86 pour générer du code 32 bits, natif x86. Si vous préférez une architecture de build de celle par défaut, choisissez une des natif ou pour spécifier l’architecture hôte et cible des invites de commandes des outils croisés.

Un moyen encore plus rapide pour ouvrir une fenêtre d’invite de commandes développeur consiste à entrer *invite de commandes développeur* dans la zone de recherche de bureau, puis choisissez le résultat souhaité.

## <a name="developer-command-files-and-locations"></a>Emplacements et des fichiers de commandes développeur

Si vous préférez définir l’environnement d’architecture de génération dans une fenêtre d’invite de commande existante, vous pouvez utiliser un des fichiers de commande (fichiers de commandes) créé par le programme d’installation pour définir l’environnement requis. Nous vous recommandons de seulement faire cela dans une nouvelle fenêtre d’invite de commandes, et nous déconseillons vous basculez vers les environnements plus loin dans la même fenêtre de commande. L’emplacement de ces fichiers dépend de la version de Visual Studio que vous avez installée et sur l’emplacement et d’affectation de noms des choix effectués lors de l’installation. Pour Visual Studio 2017, l’installation par défaut sur un ordinateur 64 bits se trouve dans \Program fichiers (x86) \Microsoft Visual Studio\2017\\*édition*, où *édition* peut-être la Communauté, Professionnel, entreprise, BuildTools ou un autre nom que vous avez fournies. Pour Visual Studio 2015, l’installation par défaut se trouve dans \Program Files (x86) \Microsoft Visual Studio 14.0.

Le fichier de commandes d’invite de commandes développeur principal, VsDevCmd.bat, se trouve dans le sous-répertoire Common7\Tools du répertoire d’installation. Lorsque aucun paramètre n’est spécifié, il définit l’environnement et l’hôte et la cible build architecture pour utiliser les outils de x86 natif de 32 bits pour générer des 32 bits x86 code.

Fichiers de commandes supplémentaires sont disponibles pour configurer des architectures de build spécifique, en fonction de votre architecture de processeur et les charges de travail de Visual Studio et les options que vous avez installé. Dans Visual Studio 2017, ceux-ci sont situés dans le sous-répertoire VC\Auxiliary\Build du répertoire d’installation de Visual Studio. Dans Visual Studio 2015, ceux-ci sont situés dans le VC, VC\bin ou VC\bin\\*architectures* sous-répertoires du répertoire d’installation, où *architectures* est un des natif ou options du compilateur croisé. Ces fichiers de commande de définir les paramètres par défaut et appellent VsDevCmd.bat pour configurer l’environnement d’architecture de build spécifiée. Une installation classique peut inclure ces fichiers de commandes :

|Fichier de commandes|Architectures d’hôte et cible|
|---|---|
|**vcvars32.bat**| Utilisez les outils de x86 natif 32 bits pour générer des 32 bits x86 code.|
|**vcvars64.bat**| Utilisez les outils de x64 natif 64 bits pour générer des x64 64 64 bits code.|
|**vcvarsx86_amd64.bat**| Utiliser les outils de croisée de x86 natif 32 bits pour générer x64 64 64 bits code.|
|**vcvarsamd64_x86.bat**| Utiliser les outils de croisée de x64 natif 64 bits pour générer des 32 bits x86 code.|
|**vcvarsx86_arm.bat**| Utilisez les outils de croisée de x86 natif de 32 bits pour générer le code d’ARM.|
|**vcvarsamd64_arm.bat**| Utilisez les outils de croisée de x64 natif de 64 bits pour générer le code d’ARM.|
|**vcvarsall.bat**| Utiliser des paramètres pour spécifier l’hôte et architectures cibles, ainsi que les choix de plate-forme et le Kit de développement logiciel. Pour obtenir la liste des options prises en charge, appelez en utilisant un **/Help** paramètre.|

> [!CAUTION]
> Le fichier vcvarsall.bat et autres fichiers de commandes de Visual Studio peuvent varier d’un ordinateur à l’autre. Ne remplacez pas un fichier vcvarsall.bat manquant ou endommagé en utilisant un fichier provenant d'un autre ordinateur. Réexécutez le programme d’installation de Visual Studio pour remplacer le fichier manquant.
>
> Le fichier vcvarsall.bat varie également d'une version à l'autre. Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, n’exécutez pas vcvarsall.bat ou un autre fichier de commandes de Visual Studio à partir de différentes versions dans la même fenêtre d’invite de commandes.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Utiliser les outils de développement dans une fenêtre de commande existante

Pour spécifier une architecture de build particulière dans une fenêtre de commande existante, le plus simple consiste à utiliser le fichier vcvarsall.bat. Vous pouvez utiliser vcvarsall.bat pour définir les variables d’environnement pour configurer la ligne de commande pour la compilation native de 32 bits ou 64 bits, ou pour une compilation croisée x86, x64 ou des processeurs ARM. pour cibler le Microsoft Store, plateforme Windows universelle ou plateformes de bureau de Windows ; Pour spécifier quel Kit de développement logiciel Windows à utiliser ; et pour spécifier la version d’ensemble d’outils de plateforme. Si aucun argument n’est fourni, vcvarsall.bat configure les variables d’environnement pour utiliser le compilateur natif 32 bits actuel pour x86 cibles de bureau de Windows. Toutefois, vous pouvez l’utiliser pour configurer un natif ou les outils de compilateur. Si vous spécifiez une configuration de compilateur qui n’est pas installée ou n’est pas disponible sur l’architecture de votre ordinateur de build, un message d’erreur s’affiche.

### <a name="vcvarsall-syntax"></a>syntaxe de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
Cet argument facultatif spécifie l’architecture hôte et cible à utiliser. Si *architecture* n’est pas spécifié, l’environnement de génération par défaut est utilisé. Ces arguments sont prises en charge :

|*architecture*|Compilateur|Architecture de l’ordinateur hôte|Créer l’architecture de sortie (cible)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|natif 32 bits x86|x86, x64|x86|
|**x86\_amd64** ou **x86\_x64**|x64 sur x86 croisé|x86, x64|X64|
|**x86_arm**|ARM sur x86 croisé|x86, x64|ARM|
|**x86_arm64**|ARM64 sur x86 croisé|x86, x64|ARM64|
|**AMD64** ou **x64**|x64 natif 64 bits|X64|X64|
|**AMD64\_x86** ou **x64\_x86**|x86 sur x64 croisé|X64|x86|
|**AMD64\_arm** ou **x64\_arm**|ARM sur x64 croisé|X64|ARM|
|**AMD64\_arm64** ou **x64\_arm64**|ARM64 sur x64 croisé|X64|ARM64|

*platform_type*<br/>
Cet argument facultatif vous permet de spécifier **stocker** ou **uwp** en tant que le type de plateforme. Par défaut, l’environnement est défini pour créer des applications de bureau ou de console.

*winsdk_version*<br/>
Spécifie éventuellement la version du SDK Windows à utiliser. Par défaut, le kit SDK Windows installée plus récente est utilisé. Pour spécifier la version du SDK Windows, vous pouvez utiliser un nombre de Windows 10 SDK complet, tel que **10.0.10240.0**, ou spécifiez **8.1** pour utiliser le SDK de Windows 8.1.

*vcversion*<br/>
Spécifie éventuellement l’ensemble d’outils du compilateur de Visual Studio à utiliser. Par défaut, l’environnement est défini pour utiliser l’ensemble d’outils du compilateur de Visual Studio 2017 en cours. Utilisez **-vcvars_ver = 14.0** pour spécifier l’ensemble d’outils du compilateur de Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Pour configurer l’environnement de génération dans une fenêtre d’invite de commandes existante

1. À l’invite de commandes, utilisez la commande CD pour remplacer dans le répertoire d’installation de Visual Studio. Ensuite, utilisez des CD à nouveau vers le sous-répertoire du répertoire qui contient les fichiers de commandes de configuration spécifiques. Pour Visual Studio 2017, il s’agit du sous-répertoire VC\Auxiliary\Build. Pour Visual Studio 2015, utilisez le sous-répertoire VC.

1. Entrez la commande pour votre environnement de développement préféré. Par exemple, pour générer le code d’ARM pour UWP sur une plateforme 64 bits à l’aide de la dernière version du SDK de Windows et l’ensemble d’outils du compilateur Visual Studio 2017 RTM, vous devez utiliser cette ligne de commande :

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>Créer votre propre raccourci d’invite de commandes

Si vous ouvrez la boîte de dialogue Propriétés de l’un des raccourcis d’invite de commandes de développeur existant, vous pouvez voir la cible de commande utilisée. Par exemple, la cible pour le **x64 invite de commandes des outils natifs pour VS 2017** raccourci est quelque chose de similaire à :

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

Ensemble des fichiers du lot spécifique de l’architecture la *architecture* vcvarsall.bat de paramètre et d’appel. Vous pouvez passer les mêmes options supplémentaires à ces fichiers de commandes que vous transmettriez à vcvarsall.bat, ou vous pouvez simplement appeler directement les vcvarsall.bat. Pour spécifier des paramètres pour votre propre raccourci de la commande, ajoutez-les à la fin de la commande dans des guillemets doubles. Par exemple, pour définir un raccourci pour générer le code ARM pour UWP sur une plateforme 64 bits à l’aide de la dernière version du SDK de Windows et l’ensemble d’outils du compilateur Visual Studio 2017 RTM, utiliser quelque chose comme cible de cette commande dans votre raccourci :

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

Vous devez ajuster le chemin d’accès pour refléter votre répertoire d’installation de Visual Studio.

## <a name="command-line-tools"></a>Outils de ligne de commande

Pour générer un projet C/C++ sur la ligne de commande, Visual Studio fournit ces outils de ligne de commande :

[CL](../build/reference/compiling-a-c-cpp-program.md)<br/>
Utilisez le compilateur (cl.exe) pour compiler et lier les fichiers de code source dans les applications, les bibliothèques et les DLL.

[Lien](../build/reference/linking.md)<br/>
Utilisez l'éditeur de liens (link.exe) pour lier les bibliothèques et les fichiers objets compilés dans les applications et les DLL.

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Utiliser MSBuild (msbuild.exe) pour générer des projets Visual C++ et des solutions Visual Studio. Cela équivaut à exécuter la **Build** projet ou **générer la Solution** commande dans l’IDE Visual Studio.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Utilisez DEVENV (devenv.exe) combiné à un commutateur de ligne de commande, par exemple, **/Build** ou **/Clean**— pour effectuer certaines commandes de génération sans afficher l’IDE Visual Studio.

[NMAKE](../build/nmake-reference.md)<br/>
Utilisez NMAKE (nmake.exe) pour automatiser les tâches qui génèrent des projets Visual C++ à l’aide d’un fichier makefile traditionnel.

Lorsque vous générez sur la ligne de commande, la commande F1 n’est pas disponible pour une aide instantanée. Au lieu de cela, vous pouvez utiliser un moteur de recherche pour obtenir des informations sur les avertissements, les erreurs et les messages, ou vous pouvez utiliser les fichiers d’aide hors connexion. Pour utiliser la recherche dans [docs.microsoft.com](https://docs.microsoft.com/cpp/), entrez votre chaîne de recherche dans la zone de recherche en haut de la page.

## <a name="in-this-section"></a>Dans cette section

Les articles répertoriés dans cette section de la documentation montrent comment générer des applications sur la ligne de commande. Ils expliquent aussi comment personnaliser l'environnement de build en ligne de commande pour utiliser les ensembles d'outils 64 bits et cibler les plateformes x86, x64 et ARM. Enfin, ils illustrent l'utilisation des outils de génération en ligne de commande MSBuild et NMAKE.

[Procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Fournit un exemple illustrant la création et la compilation un programme C++ simple sur la ligne de commande.

[Procédure pas à pas : Compilation d’un programme C sur la ligne de commande](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Décrit comment compiler un programme écrit dans le langage de programmation C.

[Procédure pas à pas : compilation d’un programme C++-CLI sur la ligne de commande](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Décrit comment créer et compiler un programme C++/CLI qui utilise le .NET Framework.

[Procédure pas à pas : compilation d’un programme C++-CX sur la ligne de commande](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Décrit comment créer et compiler un programme C++/CX qui utilise le Windows Runtime.

[Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Décrit comment ouvrir une fenêtre d’invite de commandes qui a les variables d’environnement requises défini pour les builds de ligne de commande qui ciblent x86, x64 et ARM des plateformes à l’aide d’un ensemble d’outils 32 bits ou 64 bits.

[NMAKE, référence](../build/nmake-reference.md)<br/>
Fournit des liens vers des articles qui décrivent l'utilitaire Microsoft Program Maintenance Utility (NMAKE.EXE).

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Fournit des liens vers des articles qui expliquent comment utiliser MSBuild.EXE.

## <a name="related-sections"></a>Rubriques connexes

[/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](../build/reference/md-mt-ld-use-run-time-library.md)<br/>
Décrit comment utiliser ces options de compilateur pour utiliser une bibliothèque runtime Debug ou Release.

[Options du compilateur C/C++](../build/reference/compiler-options.md)<br/>
Fournit des liens vers des articles qui présentent les options de compilateur C et C++, ainsi que CL.exe.

[Options de l’éditeur de liens](../build/reference/linker-options.md)<br/>
Fournit des liens vers des articles qui présentent les options de l'éditeur de liens et LINK.exe.

[Outils de génération C/C++](../build/reference/c-cpp-build-tools.md)<br/>
Fournit des liens vers les C/C++ outils de génération qui sont inclus dans Visual Studio.

## <a name="see-also"></a>Voir aussi

[Génération de programmes C/C++](../build/building-c-cpp-programs.md)