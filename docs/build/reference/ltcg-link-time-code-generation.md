---
title: /LTCG (Génération de code durant l'édition de liens)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: 1e33d62694fe782b1a1719fa3c5a36c6fb04670a
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400628"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Génération de code durant l'édition de liens)

Utilisez **/LTCG** pour effectuer une optimisation de l’ensemble du programme ou pour créer une instrumentation d’optimisation guidée par profil (PGO), effectuer l’entraînement et créer des générations optimisées guidées par profil.

## <a name="syntax"></a>Syntaxe

> **/LTCG**[ **:** {**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]

Ces options sont dépréciées à partir de Visual Studio 2015 :

> **/LTCG:** {**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}

### <a name="arguments"></a>Arguments

**INCREMENTAL**<br/>
(Facultatif) Spécifie que l’éditeur de liens applique uniquement une optimisation de l’ensemble du programme ou la génération de code durant l’édition de liens (LTCG) à l’ensemble des fichiers affectés par une modification, au lieu de le faire à l’ensemble du projet. Par défaut, cet indicateur n’est pas défini quand **/LTCG** est spécifié, et l’ensemble du projet est lié à l’aide de l’optimisation de l’ensemble du programme.

**NOSTATUS** &#124; **STATUS**<br/>
(Facultatif) Spécifie si l’éditeur de liens affiche un indicateur de progression qui montre le pourcentage d’exécution du lien. Par défaut, ces informations d'état ne sont pas affichées.

**OFF**<br/>
(Facultatif) Désactive la génération de code durant l’édition de liens. Ce comportement est le même que lorsque **/LTCG** n’est pas spécifié sur la ligne de commande.

**PGINSTRUMENT**<br/>
(Facultatif) Cette option est dépréciée à partir de Visual Studio 2015. Au lieu de cela, utilisez **/LTCG** et [/GENPROFILE ou /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) pour produire une génération instrumentée de l’optimisation guidée par profil. Les données recueillies à partir des séries de tests instrumentées sont utilisées pour créer une image optimisée. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG:PGI**.

**PGOPTIMIZE**<br/>
(Facultatif) Cette option est dépréciée à partir de Visual Studio 2015. Au lieu de cela, utilisez **/LTCG** et [/USEPROFILE](useprofile.md) pour générer une image optimisée. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG:PGO**.

**PGUPDATE**<br/>
(Facultatif) Cette option est dépréciée à partir de Visual Studio 2015. Au lieu de cela, utilisez **/LTCG** et **/USEPROFILE** pour regénérer une image optimisée. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG:PGU**.

## <a name="remarks"></a>Notes

L’option **/LTCG** indique à l’éditeur de liens d’appeler le compilateur et d’effectuer une optimisation de l’ensemble du programme. Vous pouvez également effectuer l’optimisation guidée par profil. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md).

Avec les exceptions suivantes, vous ne pouvez pas ajouter des options de l’éditeur de liens à la combinaison de **/LTCG** et d’ **/USEPROFILE** de l’optimisation guidée par profil qui n’ont pas été spécifiées dans la combinaison des options **/LTCG** et **/GENPROFILE** de l’initialisation de l’optimisation guidée par profil précédente :

- [/BASE](base-base-address.md)

- [/FIXED](fixed-fixed-base-address.md)

- **/LTCG**

- [/MAP](map-generate-mapfile.md)

- [/MAPINFO](mapinfo-include-information-in-mapfile.md)

- [/NOLOGO](nologo-suppress-startup-banner-linker.md)

- [/OUT](out-output-file-name.md)

- [/PGD](pgd-specify-database-for-profile-guided-optimizations.md)

- [/PDB](pdb-use-program-database.md)

- [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)

- [/STUB](stub-ms-dos-stub-file-name.md)

- [/VERBOSE](verbose-print-progress-messages.md)

Toutes les options de l’éditeur de liens qui sont spécifiées en même temps que les options **/LTCG** et **/GENPROFILE** pour initialiser l’optimisation guidée par profil n’ont pas besoin d’être spécifiées quand vous générez en utilisant **/LTCG** et **/USEPROFILE** ; elles sont implicites.

Le reste de cet article explique **/LTCG** relativement à la génération de code durant l’édition de liens.

**/LTCG** est implicite avec [/GL](gl-whole-program-optimization.md).

L’éditeur de liens appelle la génération de code durant l’édition de liens si un module compilé avec **/GL** ou un module MSIL lui est passé (consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](netmodule-files-as-linker-input.md)). Si vous ne spécifiez pas explicitement **/LTCG** quand vous passez **/GL** ou des modules MSIL à l’éditeur de liens, ce dernier le détecte et redémarre la liaison en utilisant **/LTCG**. Spécifiez explicitement **/LTCG** lorsque vous passez **/GL** et des modules MSIL à l’éditeur de liens pour accélérer au maximum la génération.

Pour améliorer encore les performances, utilisez **/LTCG:INCREMENTAL**. Cette option indique à l’éditeur de liens de réoptimiser uniquement le jeu de fichiers qui est affecté par la modification d’un fichier source, au lieu de l’ensemble du projet. Ceci peut réduire considérablement le temps nécessaire à l’édition des liens. Cette option est différente de la liaison incrémentielle.

**/LTCG** n’est pas valide pour une utilisation avec [/INCREMENTAL](incremental-link-incrementally.md).

Lorsque **/LTCG** est utilisé pour lier des modules compilés avec [/Og](og-global-optimizations.md), [/O1](o1-o2-minimize-size-maximize-speed.md), [/O2](o1-o2-minimize-size-maximize-speed.md) ou [/Ox](ox-full-optimization.md), les optimisations suivantes sont exécutées :

- Expansion inline entre modules

- Allocation de registre interprocédurale (seulement sur les systèmes d’exploitation 64 bits)

- Convention d’appel personnalisée (x86 uniquement)

- Déplacement TLS réduit (x86 uniquement)

- Alignement de pile double (x86 uniquement)

- Levée d’ambiguïté améliorée de la mémoire (meilleures informations d’interférence pour les variables globales et les paramètres d’entrée)

> [!NOTE]
> L’éditeur de liens détermine les optimisations qui ont été utilisées pour compiler chaque fonction et applique les mêmes optimisations au moment de la liaison.

L’utilisation de **/LTCG** et de **/Ogt** provoque une optimisation à double alignement.

Si **/LTCG** et **/Ogs** sont spécifiés, le double alignement n’est pas effectué. Si la plupart des fonctions d’une application sont compilées pour la rapidité, d’autres l’étant pour la taille (par exemple, à l’aide du pragma [optimize](../../preprocessor/optimize.md)), le compilateur procède à un double alignement des fonctions optimisées pour la taille si celles-ci appellent des fonctions qui en ont besoin.

Si le compilateur peut identifier tous les sites d’appel d’une fonction, le compilateur ignore les modificateurs de convention d’appel explicites sur une fonction et tente d’optimiser la convention d’appel de la fonction :

- passer des paramètres dans les registres

- réorganiser les paramètres pour l’alignement

- supprimer les paramètres inutilisés

Si une fonction est appelée via un pointeur de fonction, ou si une fonction est appelée en dehors d’un module compilé avec **/GL**, le compilateur ne tente pas d’optimiser la convention d’appel de la fonction.

> [!NOTE]
> Si vous utilisez **/LTCG** et redéfinissez `mainCRTStartup`, votre application peut avoir un comportement imprévisible concernant le code utilisateur qui s’exécute avant l’initialisation des objets globaux. Il existe trois façons de régler ce problème : ne pas redéfinir `mainCRTStartup`, ne pas compiler le fichier qui contient `mainCRTStartup` en utilisant **/LTCG** ou initialiser les variables globales et les objets globaux de manière statique.

### <a name="ltcg-and-msil-modules"></a>/LTCG et les modules MSIL

Les modules compilés avec [/GL](gl-whole-program-optimization.md) et [/clr](clr-common-language-runtime-compilation.md) peuvent être utilisés comme entrée dans l'éditeur de liens si **/LTCG** est spécifié.

- **/LTCG** peut accepter des fichiers objets natifs et des fichiers objets natifs/managés mixtes (compilés avec **/clr**). Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017 et ultérieur.

- **/LTCG:PGI** n’accepte pas les modules natifs compilés avec **/GL** et **/clr**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **Général**.

1. Modifiez la propriété **Optimisation de l’ensemble du programme** .

Vous pouvez également appliquer **/LTCG** à des générations spécifiques en choisissant **Générer** > **Optimisation guidée par profil** dans la barre de menus, ou en choisissant l’une des options d’optimisation guidée par profil dans le menu contextuel du projet.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
