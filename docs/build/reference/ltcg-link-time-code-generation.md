---
title: /LTCG (génération de Code lien) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc4266e8b01201226c53584bed9f90ed9dcabef7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703731"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Génération de code durant l'édition de liens)

Utilisez **LTCG** pour effectuer l’optimisation de l’ensemble du programme, ou pour créer l’instrumentation de l’optimisation guidée par profil (PGO), effectuez la formation et créer guidée par profil optimisé builds.

## <a name="syntax"></a>Syntaxe

> **/LTCG**[**:**{**INCRÉMENTIEL**|**NOSTATUS**|**ÉTAT** | **OFF**}]<br/>

Ces options sont déconseillées à compter de Visual Studio 2015 :

> **/ LTCG :**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Arguments

**INCRÉMENTIELLE** (facultatif)<br/>
Spécifie que l’éditeur de liens s’applique uniquement ensemble du programme optimisation ou lien de génération de code (LTCG) à l’ensemble des fichiers affectés par une modification, au lieu de l’ensemble du projet. Par défaut, cet indicateur n'est pas défini quand **LTCG** est spécifié, et l’ensemble du projet est lié à l’aide d’optimisation de l’ensemble du programme.

**NOSTATUS** &#124; **état** (facultatif)<br/>
Spécifie si l'éditeur de liens affiche un indicateur de progression qui montre le pourcentage d'exécution du lien. Par défaut, ces informations d'état ne sont pas affichées.

**DÉSACTIVER** (facultatif)<br/>
Désactive la génération de code au moment de la liaison. Ce comportement est le même que lorsque **LTCG** n’est pas spécifié sur la ligne de commande.

**PGINSTRUMENT** (facultatif)<br/>
Cette option est déconseillée à compter de Visual Studio 2015. Au lieu de cela, utilisez **LTCG** et [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) pour générer une version instrumentée de l’optimisation guidée par profil. Les données recueillies à partir des séries de tests instrumentées sont utilisées pour créer une image optimisée. Pour plus d’informations, consultez [optimisation guidée par profil](profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG : PGI**.

**PGOPTIMIZE** (facultatif)<br/>
Cette option est déconseillée à compter de Visual Studio 2015. Au lieu de cela, utilisez **LTCG** et [/useprofile](useprofile.md) pour générer une image optimisée. Pour plus d’informations, consultez [optimisation guidée par profil](../../build/reference/profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG : PGO**.

**PGUPDATE** (facultatif)<br/>
Cette option est déconseillée à compter de Visual Studio 2015. Au lieu de cela, utilisez **LTCG** et **/useprofile** pour reconstruire une image optimisée. Pour plus d’informations, consultez [optimisation guidée par profil](../../build/reference/profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG : pgu**.

## <a name="remarks"></a>Notes

Le **LTCG** option indique à l’éditeur de liens pour appeler le compilateur et l’optimisation de l’ensemble du programme. Vous pouvez également effectuer l’optimisation guidée par profil. Pour plus d’informations, consultez [optimisation guidée par profil](../../build/reference/profile-guided-optimizations.md).

Avec les exceptions suivantes, vous ne pouvez pas ajouter les options de l’éditeur de liens à la combinaison PGO de **LTCG** et **/useprofile** qui n’ont pas été spécifiés dans la combinaison de l’initialisation PGO précédente de  **/LTCG** et **/genprofile** options :

- [/BASE](../../build/reference/base-base-address.md)

- [/FIXED](../../build/reference/fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](../../build/reference/map-generate-mapfile.md)

- [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)

- [/OUT](../../build/reference/out-output-file-name.md)

- [/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](../../build/reference/pdb-use-program-database.md)

- [/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)

- [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)

Toutes les options de l’éditeur de liens qui sont spécifiées avec le **LTCG** et **/genprofile** options d’initialisation PGO n’ont pas à être spécifié lorsque vous générez à l’aide de **LTCG** et **/Useprofile**; elles sont implicites.

Le reste de cet article explique **LTCG** en termes de génération de code de l’édition de liens.

**/LTCG** est implicite avec [/GL](../../build/reference/gl-whole-program-optimization.md).

L’éditeur de liens appelle la génération du code au moment de la liaison s’il est passé à un module qui a été compilé à l’aide de **/GL** ou un module MSIL (consultez [fichiers .netmodule en tant qu’entrée de l’éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md)). Si vous ne spécifiez pas explicitement **LTCG** lorsque vous passez **/GL** ou des modules MSIL à l’éditeur de liens, et éventuellement l’éditeur de liens détecte et redémarre la liaison à l’aide de **LTCG**. Spécifiez explicitement **LTCG** lorsque vous passez **/GL** et modules MSIL à l’éditeur de liens pour accélérer au maximum la génération.

Pour encore améliorer les performances, utilisez **LTCG : INCREMENTAL**. Cette option indique à l’éditeur de liens d’optimiser uniquement le jeu de fichiers qui est affecté par la modification d’un fichier source, au lieu de l’ensemble du projet. Ceci peut réduire considérablement le temps nécessaire à l’édition des liens. Ce n’est pas la même option comme la liaison incrémentielle.

**/LTCG** n’est pas valide pour une utilisation avec [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).

Lorsque **LTCG** sert à lier des modules compilés à l’aide de [/Og](../../build/reference/og-global-optimizations.md), [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), ou [/Ox](../../build/reference/ox-full-optimization.md), optimisations suivantes sont effectuées :

- Expansion inline entre modules

- Allocation de registre interprocédurale (seulement sur les systèmes d’exploitation 64 bits)

- Convention d’appel personnalisée (x86 uniquement)

- Déplacement TLS réduit (x86 uniquement)

- Alignement de pile double (x86 uniquement)

- Levée d’ambiguïté améliorée de la mémoire (meilleures informations d’interférence pour les variables globales et les paramètres d’entrée)

> [!NOTE]
> L’éditeur de liens détermine les optimisations qui ont été utilisées pour compiler chaque fonction et applique les mêmes optimisations au moment de la liaison.

À l’aide de **LTCG** et **/Ogt** provoque une optimisation à double alignement.

Si **LTCG** et **/Ogs** sont spécifiés, double alignement n’est pas effectuée. Si la plupart des fonctions d’une application est compilée pour la rapidité, avec quelques fonctions compilées pour la taille (par exemple, à l’aide de la [optimiser](../../preprocessor/optimize.md) pragma), le compilateur aligne double les fonctions qui sont optimisées pour la taille si celles-ci appellent fonctions qui requièrent le double alignement.

Si le compilateur peut identifier tous les sites d’appel d’une fonction, le compilateur ignore les modificateurs de convention d’appel explicites sur une fonction et tente d’optimiser la convention d’appel de la fonction :

- passer des paramètres dans les registres

- réorganiser les paramètres pour l’alignement

- supprimer les paramètres inutilisés

Si une fonction est appelée via un pointeur de fonction, ou si une fonction est appelée en dehors d’un module qui est compilé à l’aide de **/GL**, le compilateur ne tente pas d’optimiser la convention d’appel de la fonction.

> [!NOTE]
> Si vous utilisez **LTCG** et redéfinir `mainCRTStartup`, votre application peut avoir un comportement imprévisible au code utilisateur qui s’exécute avant l’initialisation des objets globaux. Il existe trois façons de résoudre ce problème : ne pas redéfinir `mainCRTStartup`, ne pas compiler le fichier qui contient `mainCRTStartup` à l’aide de **LTCG**, ou initialiser les variables globales et les objets de manière statique.

### <a name="ltcg-and-msil-modules"></a>/LTCG et les modules MSIL

Les modules compilés avec [/GL](../../build/reference/gl-whole-program-optimization.md) et [/clr](../../build/reference/clr-common-language-runtime-compilation.md) peuvent être utilisés comme entrée dans l'éditeur de liens si **/LTCG** est spécifié.

- **/LTCG** peut accepter des fichiers objets natifs et fichiers d’objet managé/natif mixte (compilée à l’aide de **/CLR**). Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

- **/ LTCG : PGI** n’accepte pas les modules natifs compilés à l’aide de **/GL** et   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **général** page de propriétés.

1. Modifiez la propriété **Optimisation de l’ensemble du programme** .

Vous pouvez également appliquer **LTCG** à des builds spécifiques en choisissant **générer** > **optimisation guidée par profil** sur la barre de menus, ou en choisissant une du profil Options d’optimisation guidées dans le menu contextuel du projet.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
- [Options de l’éditeur de liens](../../build/reference/linker-options.md)
