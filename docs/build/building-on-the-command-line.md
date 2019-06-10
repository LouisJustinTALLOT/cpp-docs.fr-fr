---
title: Utiliser Microsoft C++ ensemble d’outils à partir de la ligne de commande
description: Utilisez la chaîne d’outils du compilateur Microsoft C++ (MSVC) à partir de la ligne de commande en dehors de l’environnement de développement intégré (IDE) Visual Studio.
ms.custom: conceptual
ms.date: 06/06/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: b5e9bf266d79ee86cae84535641a52c7c52be391
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821137"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Utiliser Microsoft C++ ensemble d’outils à partir de la ligne de commande

Vous pouvez générer des applications C et C++ sur la ligne de commande en utilisant les outils inclus dans Visual Studio. Microsoft C++ ensemble d’outils du compilateur (MSVC) peut être également téléchargé sous forme de package autonome à partir de la [téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/) page. Il s’agit de la partie de la **Build Tools pour Visual Studio** package. Vous pouvez choisir de télécharger uniquement les outils que vous avez besoin pour C++ développement.

## <a name="how-to-use-the-command-line-tools"></a>Comment utiliser les outils en ligne de commande

Quand vous choisissez l’une des charges de travail C++ dans Visual Studio Installer, l’*ensemble d’outils de plateforme* Visual Studio est installé. Un ensemble d’outils de plateforme a tous les C et C++ outils pour une version spécifique de Visual Studio. Les outils incluent le C /C++ compilateurs, les éditeurs de liens, les assembleurs et d’autres outils de génération et les bibliothèques correspondantes. Vous pouvez utiliser tous ces outils en ligne de commande. Elles sont également utilisées en interne par l’IDE Visual Studio. Il existe des compilateurs hébergés x86 et hébergés en x64 64 distincts et outils de génération de code pour x86, x 64, ARM et ARM64 cibles. Chaque ensemble d’outils propre à une architecture de build hôte et cible particulière est stocké dans son propre répertoire.

Pour fonctionner correctement, les outils nécessitent de définir plusieurs variables d’environnement spécifiques. Ces variables sont utilisées pour ajouter les outils pour le chemin d’accès et pour définir incluent des fichiers, les fichier de bibliothèque et les emplacements du Kit de développement logiciel. Pour faciliter la définition de ces variables d’environnement, le programme d’installation crée des *fichiers de commandes* personnalisés lors de l’installation. Vous pouvez exécuter un de ces fichiers de commande pour définir un hôte spécifique et architecture de cible de build, version du SDK Windows et ensemble d’outils de plateforme. Pour plus de commodité, le programme d’installation crée également des raccourcis dans votre menu Démarrer. Les raccourcis démarrent une invite de commandes de développeur windows à l’aide de ces fichiers de commandes pour des combinaisons spécifiques de l’hôte et cible. Ces raccourcis vous assurer que toutes les variables d’environnement nécessaires sont défini et prêt à être utilisé.

Les variables d’environnement requises sont spécifiques à votre installation et de l’architecture de build que vous choisissez. Ils peuvent également être modifiés par les mises à jour de produit ou de mise à niveau. C’est pourquoi nous vous recommandons d’utiliser un fichier de raccourci ou la commande d’invite de commandes installée, au lieu de définir les variables d’environnement vous-même. Pour plus d’informations, consultez [définir les variables d’environnement et le chemin d’accès pour les builds de ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md).

Les ensembles d’outils, les fichiers de commandes et les raccourcis installés dépendent de votre processeur de l’ordinateur et les options que vous avez sélectionné lors de l’installation. Les outils hébergés x86 et entre les outils qui génèrent des code x86 et x64 sont toujours installés. Si vous avez Windows de 64 bits, les outils hébergés en x64 64 et des outils croisées de code x86 et x64 sont également installés. Si vous choisissez le paramètre facultatif C++ outils de plateforme Windows universelle, puis les outils x86 et x64 générer du code ARM et ARM64 également installés. D’autres charges de travail peuvent installer d’autres outils.

## <a name="developer_command_prompt_shortcuts"></a> Raccourcis d’invite de commandes développeur

Les raccourcis d’invite de commandes sont installés dans un dossier propre à la version de Visual Studio dans votre menu Démarrer. Voici la liste des principaux raccourcis d’invite de commandes et des architectures de build prises en charge :

- **Invite de commandes développeur** : définit l’environnement pour utiliser des outils natifs x86 32 bits pour générer du code natif x86 32 bits.
- **Invite de commandes des outils natifs x86** : définit l’environnement pour utiliser des outils natifs x86 32 bits pour générer du code natif x86 32 bits.
- **Invite de commandes des outils natifs x64** : définit l’environnement pour utiliser des outils natifs x64 64 bits pour générer du code natif x64 64 bits.
- **Invite de commandes des outils croisés x86_x64** : définit l’environnement pour utiliser des outils natifs x86 32 bits pour générer du code natif x64 64 bits.
- **Invite de commandes des outils croisés x64_x86** : définit l’environnement pour utiliser des outils natifs x64 64 bits pour générer du code natif x86 32 bits.

::: moniker range=">= vs-2019"

Les noms de dossier et les raccourcis de menu Démarrer varient selon la version installée de Visual Studio. Si vous définissez une, elles dépendent également l’installation **surnom**. Par exemple, supposons que vous avez installé Visual Studio 2019, et vous lui donnez un surnom de *dernière*. Le raccourci d’invite de commandes développeur est nommé **invite de commandes développeur pour 2019 VS (dernière version)** , dans un dossier nommé **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Les noms de dossier et les raccourcis de menu Démarrer varient selon la version installée de Visual Studio. Si vous définissez une, elles dépendent également l’installation **surnom**. Par exemple, supposons que vous avez installé Visual Studio 2017, et vous lui donnez un surnom de *dernière*. Le raccourci d’invite de commandes développeur est nommé **invite de commandes développeur pour VS 2017 (dernière version)** , dans un dossier nommé **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Les noms de dossier et les raccourcis de menu Démarrer varient selon la version installée de Visual Studio. Par exemple, supposons que vous avez installé Visual Studio 2015. Le raccourci d’invite de commandes développeur est nommé **invite de commandes développeur pour VS 2015**.

::: moniker-end

## <a name="developer_command_prompt"></a> Pour ouvrir une fenêtre d’invite de commandes développeur

1. Sur le bureau, ouvrez le menu **Démarrer** de Windows, puis faites-le défiler pour trouver et ouvrir le dossier correspondant à votre version de Visual Studio, par exemple, **Visual Studio 2019**.

1. Dans le dossier, choisissez le raccourci **Invite de commandes développeur** de votre version de Visual Studio. Ce raccourci ouvre une fenêtre d’invite de commandes développeur qui utilise l’architecture de build par défaut des outils natifs x86 32 bits pour générer du code natif x86 32 bits. Si vous préférez une architecture de build autre que celle par défaut, choisissez l’une des invites de commandes des outils natifs ou croisés pour spécifier l’architecture hôte et cible.

Pour encore plus rapidement ouvrir une invite de commandes développeur, entrez *invite de commandes développeur* dans la zone de recherche de bureau. Choisissez ensuite le résultat souhaité.

## <a name="developer_command_file_locations"></a> Emplacements des fichiers de commandes développeur

Si vous préférez définir l’environnement de génération dans une fenêtre d’invite de commande existante, vous pouvez utiliser un des fichiers de commande créées par le programme d’installation. Nous vous recommandons de que définir l’environnement dans une nouvelle fenêtre d’invite de commandes. Nous vous déconseillons basculez vers les environnements plus loin dans la même fenêtre de commande.

::: moniker range=">= vs-2019"

L’emplacement du fichier commande dépend de la version de Visual Studio que vous avez installé et sur les choix effectués lors de l’installation. Pour Visual Studio 2019, l’emplacement d’installation par défaut sur un système 64 bits est \\Program Files (x86)\\Microsoft Visual Studio\\2019\\*édition*. *Édition* peut-être Community, Professional, Enterprise, BuildTools ou un autre surnom que vous avez fournies.

::: moniker-end
::: moniker range="= vs-2017"

L’emplacement du fichier commande dépend de la version de Visual Studio que vous avez installé et sur les choix effectués lors de l’installation. Pour Visual Studio 2017, l’emplacement d’installation par défaut sur un système 64 bits est \\Program Files (x86)\\Microsoft Visual Studio\\2017\\*édition*. *Édition* peut-être Community, Professional, Enterprise, BuildTools ou un autre surnom que vous avez fournies.

::: moniker-end
::: moniker range="< vs-2017"

L’emplacement de fichier de commande varie selon la version de Visual Studio et le répertoire d’installation. Pour Visual Studio 2015, l’emplacement d’installation par défaut est \\Program Files (x86)\\Microsoft Visual Studio 14.0.

::: moniker-end

Le fichier de commandes d’invite de commandes développeur principal, VsDevCmd.bat, se trouve dans le Common7\\sous-répertoire Tools. Lorsque aucun paramètre est spécifié, il définit l’environnement à utiliser les outils natifs x86 pour générer des 32 bits x86 code.

::: moniker range=">= vs-2017"

Plusieurs fichiers de commande sont disponibles pour configurer des architectures de build spécifique. Les fichiers de commandes disponibles varient selon les charges de travail de Visual Studio et les options que vous avez installé. Dans Visual Studio 2017 et Visual Studio 2019, vous les trouverez dans le circuit virtuel\\auxiliaires\\Build sous-répertoire.

::: moniker-end
::: moniker range="< vs-2017"

Plusieurs fichiers de commande sont disponibles pour configurer des architectures de build spécifique. Les fichiers de commandes disponibles varient selon les charges de travail de Visual Studio et les options que vous avez installé. Dans Visual Studio 2015, ils se trouvent dans le VC, VC\\bin ou VC\\bin\\*architecture* , des sous-répertoires où *architecture* est un des natif ou options du compilateur croisé.

::: moniker-end

Ces fichiers de commandes définissent les paramètres par défaut et appellent VsDevCmd.bat pour configurer l’environnement de l’architecture de build spécifiée. Une installation classique peut inclure ces fichiers de commandes :

|Fichier de commandes|Architectures hôte et cible|
|---|---|
|**vcvars32.bat**| Utilisent les outils natifs x86 32 bits pour générer du code x86 32 bits.|
|**vcvars64.bat**| Utilisent les outils natifs x64 64 bits pour générer du code x64 64 bits.|
|**vcvarsx86_amd64.bat**| Utilisent les outils croisés natifs x86 32 bits pour générer du code x64 64 bits.|
|**vcvarsamd64_x86.bat**| Utilisent les outils croisés natifs x64 64 bits pour générer du code x86 32 bits.|
|**vcvarsx86_arm.bat**| Utilisent les outils croisés natifs x86 32 bits pour générer du code ARM.|
|**vcvarsamd64_arm.bat**| Utilisent les outils croisés natifs x64 64 bits pour générer du code ARM.|
|**vcvarsall.bat**| Utiliser des paramètres pour spécifier les architectures hôte et cible, Kit de développement logiciel Windows, les choix de la plateforme. Pour obtenir la liste des options prises en charge, effectuez un appel en utilisant un paramètre **/help**.|

> [!CAUTION]
> Le fichier vcvarsall.bat et d’autres fichiers de commandes Visual Studio peuvent varier d’un ordinateur à l’autre. Ne remplacez pas un fichier vcvarsall.bat manquant ou endommagé en utilisant un fichier provenant d'un autre ordinateur. Réexécutez le programme d’installation de Visual Studio pour remplacer le fichier manquant.
>
> Le fichier vcvarsall.bat varie également d'une version à l'autre. Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, n’exécutez pas vcvarsall.bat ni un autre fichier de commandes Visual Studio à partir de différentes versions dans la même fenêtre d’invite de commandes.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Utiliser les outils de développement dans une fenêtre Commande existante

Le moyen le plus simple de spécifier une architecture de build particulière dans une fenêtre Commande existante consiste à utiliser le fichier vcvarsall.bat. Utilisez vcvarsall.bat pour définir les variables d’environnement pour configurer la ligne de commande pour la compilation de 32 bits ou 64 bits native. Arguments vous permettent de spécifier une compilation croisée sur x86, x 64, ARM, ARM64 processeurs ou. Vous pouvez cibler des plateformes Microsoft Store, plateforme Windows universelle ou du bureau de Windows. Vous pouvez même spécifier quel Kit de développement logiciel Windows à utiliser et sélectionnez la version d’ensemble d’outils de plateforme.

Lorsqu’il est utilisé sans arguments, vcvarsall.bat configure les variables d’environnement pour utiliser le compilateur natif x86 actuel pour les cibles de bureau de Windows 32 bits. Vous pouvez ajouter des arguments pour configurer l’environnement pour utiliser n’importe quel natif ou les outils de compilateur. vcvarsall.bat affiche un message d’erreur si vous spécifiez une configuration qui n’est pas installée ou disponible sur votre ordinateur.

### <a name="vcvarsall-syntax"></a>Syntaxe de vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Cet argument facultatif spécifie l’architecture hôte et cible à utiliser. Si *architecture* n’est pas spécifié, l’environnement de génération par défaut est utilisé. Ces arguments sont pris en charge :

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
Spécifie éventuellement l’ensemble d’outils du compilateur Visual Studio à utiliser. Par défaut, l’environnement est défini pour utiliser l’ensemble d’outils du compilateur Visual Studio actuel.

::: moniker range=">= vs-2019"

Utilisez **-vcvars_ver = 14.2 x .yyyyy** pour spécifier une version spécifique de l’ensemble d’outils du compilateur de Visual Studio 2019.

Utilisez **-vcvars_ver = 14.16** pour spécifier la dernière version de l’ensemble d’outils du compilateur de Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Utilisez **-vcvars_ver = 14.16** pour spécifier la dernière version de l’ensemble d’outils du compilateur de Visual Studio 2017.

Utilisez **-vcvars_ver = 14.1 x .yyyyy** pour spécifier une version spécifique de l’ensemble d’outils du compilateur de Visual Studio 2017.

::: moniker-end

Utilisez **-vcvars_ver = 14.0** pour spécifier l’ensemble d’outils du compilateur de Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Pour configurer l’environnement de build dans une fenêtre d’invite de commandes existante

1. À l’invite de commandes, utilisez la commande CD pour accéder au répertoire d’installation de Visual Studio. Ensuite, réutilisez CD pour accéder au sous-répertoire qui contient les fichiers de commandes propres à la configuration. Pour Visual Studio 2019 et Visual Studio 2017, utilisez le *VC\\auxiliaires\\Build* sous-répertoire. Pour Visual Studio 2015, utilisez le *VC* sous-répertoire.

1. Entrez la commande qui correspond à votre environnement de développement préféré. Par exemple, pour générer du code ARM pour UWP sur une plateforme 64 bits, à l’aide du dernier Kit de développement logiciel Windows et Visual Studio du compilateur ensemble d’outils, vous devez utiliser cette ligne de commande :

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Créer votre propre raccourci d’invite de commandes

::: moniker range=">= vs-2019"

Ouvrez la boîte de dialogue Propriétés pour un raccourci d’invite de commandes développeur voir la cible de commande utilisée. Par exemple, la cible du raccourci **Invite de commandes des outils natifs x64 pour VS 2019** ressemble à ceci :

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Ouvrez la boîte de dialogue Propriétés pour un raccourci d’invite de commandes développeur voir la cible de commande utilisée. Par exemple, la cible pour le **x64 invite de commandes des outils natifs pour VS 2017** raccourci est quelque chose de similaire à :

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Ouvrez la boîte de dialogue Propriétés pour un raccourci d’invite de commandes développeur voir la cible de commande utilisée. Par exemple, la cible pour le **VS2015 x64 invite de commandes des outils natifs** raccourci est quelque chose de similaire à :

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64`

::: moniker-end

Les fichiers de commandes propres à l’architecture définissent le paramètre *architecture* et appellent vcvarsall.bat. Vous pouvez passer les mêmes options pour ces fichiers de commandes que vous transmettriez à vcvarsall.bat, ou vous pouvez simplement appeler directement les vcvarsall.bat. Pour spécifier des paramètres pour votre propre raccourci de commande, ajoutez-les à la fin de la commande entre guillemets doubles. Par exemple, Voici un raccourci pour générer le code ARM pour UWP sur une plateforme 64 bits, à l’aide de la dernière version du SDK de Windows. Pour utiliser un ensemble d’outils du compilateur antérieures, spécifiez le numéro de version. Utilisez quelque chose comme la cible de cette commande dans votre raccourci :

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.16"`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.0"`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64 -vcvars_ver=12.0`

::: moniker-end

Ajustez le chemin d’accès pour refléter votre répertoire d’installation de Visual Studio. Le fichier vcvarsall.bat comporte des informations supplémentaires sur les numéros de versions spécifiques.

## <a name="command-line-tools"></a>Outils de ligne de commande

Pour générer un C /C++ projet à l’invite de commande, Visual Studio fournit ces outils de ligne de commande :

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Utilisez le compilateur (cl.exe) pour compiler et lier les fichiers de code source dans les applications, les bibliothèques et les DLL.

[Lien](reference/linking.md)<br/>
Utilisez l'éditeur de liens (link.exe) pour lier les bibliothèques et les fichiers objets compilés dans les applications et les DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Utilisez MSBuild (msbuild.exe) et un fichier projet (.vcxproj) pour configurer une build et appeler l’ensemble d’outils indirectement. Il équivaut à exécuter la **Build** projet ou **générer la Solution** commande dans l’IDE Visual Studio. Exécution de MSBuild à partir de la ligne de commande est un scénario avancé et généralement pas recommandé.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Utilisez DEVENV (devenv.exe) combiné à un commutateur de ligne de commande comme **/Build** ou **/Clean** pour exécuter certaines commandes de génération sans afficher l’IDE Visual Studio. En règle générale, DEVENV est préférable à l’aide de MSBuild directement, car vous pouvez permettre à Visual Studio de gérer les complexités de MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Utilisez NMAKE (nmake.exe) sur Windows pour générer des projets C++ basés sur un makefile traditionnel.

Lorsque vous générez sur la ligne de commande, la commande F1 n’est pas disponible pour une aide instantanée. Au lieu de cela, vous pouvez utiliser un moteur de recherche pour obtenir des informations sur les avertissements, les erreurs et les messages, ou bien vous pouvez utiliser les fichiers d’aide hors connexion. Pour utiliser la recherche dans [docs.microsoft.com](https://docs.microsoft.com/cpp/), utilisez la zone de recherche en haut de la page.

## <a name="in-this-section"></a>Dans cette section

Ces articles expliquent comment créer des applications sur la ligne de commande et expliquent comment personnaliser l’environnement de génération de ligne de commande. Certains montrent comment utiliser des ensembles d’outils 64 bits et cibler x86, x 64, ARM, ARM64 plateformes et. Elles décrivent également utiliser les outils de ligne de commande MSBuild et NMAKE.

[Procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Fournit un exemple qui montre comment créer et compiler un C++ programme sur la ligne de commande.

[Procédure pas à pas : compiler un programme C sur la ligne de commande](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Décrit comment compiler un programme écrit dans le langage de programmation C.

[Procédure pas à pas : compilation d’un programme C++/CLI natif sur la ligne de commande](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Décrit comment créer et compiler un programme C++/CLI qui utilise le .NET Framework.

[Procédure pas à pas : compilation d’un programme C++/CX natif sur la ligne de commande](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Décrit comment créer et compiler un programme C++/CX qui utilise le Windows Runtime.

[Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Comment définir des variables d’environnement pour utiliser un ensemble d’outils 32 bits ou 64 bits pour cibler x86, x64, ARM, ARM64 plateformes et.

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
