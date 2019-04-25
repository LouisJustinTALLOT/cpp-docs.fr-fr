---
title: /LTCG (Génération de code durant l'édition de liens)
ms.date: 03/14/2018
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
ms.openlocfilehash: 40fb591952180735de3a2c226a3953a303c7d90f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62162355"
---
# <a name="ltcg-link-time-code-generation"></a>/LTCG (Génération de code durant l'édition de liens)

Utilisez **/LTCG** pour effectuer l’optimisation de la totalité du programme, ou pour créer l’instrumentation de l’optimisation guidée par profil (PGO), effectuer l’apprentissage et créer guidée par profil optimisé builds.

## <a name="syntax"></a>Syntaxe

> **/LTCG**[**:**{**INCREMENTAL**|**NOSTATUS**|**STATUS**|**OFF**}]<br/>

Ces options sont déconseillées à compter de Visual Studio 2015 :

> **/ LTCG :**{**PGINSTRUMENT**|**PGOPTIMIZE**|**PGUPDATE**}<br/>

### <a name="arguments"></a>Arguments

**INCRÉMENTIELLE**<br/>
(Facultatif) Spécifie que l’éditeur de liens s’applique uniquement ensemble du programme optimisation ou le moment de la liaison génération de code (LTCG) à l’ensemble des fichiers affectés par une modification, au lieu de l’ensemble du projet. Par défaut, cet indicateur n'est pas défini quand **/LTCG** est spécifié, et l’ensemble du projet est lié à l’aide d’optimisation de l’ensemble du programme.

**NOSTATUS** &#124; **STATUS**<br/>
(Facultatif) Spécifie si l’éditeur de liens affiche un indicateur de progression qui indique quel pourcentage de la liaison est terminée. Par défaut, ces informations d'état ne sont pas affichées.

**OFF**<br/>
(Facultatif) Désactive la génération de code du moment de la liaison. Ce comportement est le même que lorsque **/LTCG** n’est pas spécifié sur la ligne de commande.

**PGINSTRUMENT**<br/>
(Facultatif) Cette option est déconseillée à compter de Visual Studio 2015. Au lieu de cela, utilisez **/LTCG** et [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) pour générer une version instrumentée de l’optimisation guidée par profil. Les données recueillies à partir des séries de tests instrumentées sont utilisées pour créer une image optimisée. Pour plus d’informations, consultez [optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG : PGI**.

**PGOPTIMIZE**<br/>
(Facultatif) Cette option est déconseillée à compter de Visual Studio 2015. Au lieu de cela, utilisez **/LTCG** et [/USEPROFILE](useprofile.md) pour générer une image optimisée. Pour plus d’informations, consultez [optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG : PGO**.

**PGUPDATE**<br/>
(Facultatif) Cette option est déconseillée à compter de Visual Studio 2015. Au lieu de cela, utilisez **/LTCG** et **/USEPROFILE** pour reconstruire une image optimisée. Pour plus d’informations, consultez [optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **/LTCG : pgu**.

## <a name="remarks"></a>Notes

Le **/LTCG** option indique à l’éditeur de liens d’appeler le compilateur et effectuer une optimisation de la totalité du programme. Vous pouvez également effectuer l’optimisation guidée par profil. Pour plus d’informations, consultez [optimisations guidées par profil](../profile-guided-optimizations.md).

Avec les exceptions suivantes, vous ne pouvez pas ajouter des options de l’éditeur de liens à la combinaison de **/LTCG** et **/USEPROFILE** qui n’ont pas été spécifiées dans la combinaison d’initialisation précédente de  **/ LTCG** et **/genprofile** options :

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

Toutes les options de l’éditeur de liens qui sont spécifiées avec le **/LTCG** et **/genprofile** options pour initialiser la PGO n’ont pas à être spécifié lorsque vous générez à l’aide de **/LTCG** et **/USEPROFILE**; elles sont implicites.

Le reste de cet article explique **/LTCG** en termes de génération de code du moment de la liaison.

**/ LTCG** est implicite avec [/GL](gl-whole-program-optimization.md).

L’éditeur de liens appelle la génération de code du moment de la liaison si elle est passée à un module qui a été compilé à l’aide de **/GL** ou un module MSIL (consultez [fichiers .netmodule en tant qu’entrée de l’éditeur de liens](netmodule-files-as-linker-input.md)). Si vous ne spécifiez pas explicitement **/LTCG** lorsque vous passez **/GL** ou des modules MSIL à l’éditeur de liens, l’éditeur de liens finalement détecte et redémarre la liaison à l’aide de **/LTCG**. Spécifiez explicitement **/LTCG** lorsque vous passez **/GL** et performances de modules MSIL à l’éditeur de liens pour accélérer au maximum la génération.

Pour encore améliorer les performances, utilisez **/LTCG : incrémentielle**. Cette option indique à l’éditeur de liens d’optimiser uniquement le jeu de fichiers qui est affecté par la modification d’un fichier source, au lieu de l’ensemble du projet. Ceci peut réduire considérablement le temps nécessaire à l’édition des liens. Cela n’est pas la même option comme la liaison incrémentielle.

**/LTCG** n’est pas valide pour une utilisation avec [/INCREMENTAL](incremental-link-incrementally.md).

Lorsque **/LTCG** est utilisé pour lier les modules compilés à l’aide de [/Og](og-global-optimizations.md), [/O1](o1-o2-minimize-size-maximize-speed.md), [/O2](o1-o2-minimize-size-maximize-speed.md), ou [/Ox](ox-full-optimization.md), le optimisations suivantes sont effectuées :

- Expansion inline entre modules

- Allocation de registre interprocédurale (seulement sur les systèmes d’exploitation 64 bits)

- Convention d’appel personnalisée (x86 uniquement)

- Déplacement TLS réduit (x86 uniquement)

- Alignement de pile double (x86 uniquement)

- Levée d’ambiguïté améliorée de la mémoire (meilleures informations d’interférence pour les variables globales et les paramètres d’entrée)

> [!NOTE]
> L’éditeur de liens détermine les optimisations qui ont été utilisées pour compiler chaque fonction et applique les mêmes optimisations au moment de la liaison.

À l’aide de **/LTCG** et **/Ogt** provoque une optimisation à double alignement.

Si **/LTCG** et **/Ogs** sont spécifiés, double alignement n’est pas effectuée. Si la plupart des fonctions dans une application est compilée pour la rapidité, avec quelques fonctions compilées pour la taille (par exemple, en utilisant le [optimiser](../../preprocessor/optimize.md) pragma), le compilateur aligne double les fonctions qui sont optimisées pour la taille si celles-ci appellent fonctions nécessitant un double alignement.

Si le compilateur peut identifier tous les sites d’appel d’une fonction, le compilateur ignore les modificateurs de convention d’appel explicites sur une fonction et tente d’optimiser la convention d’appel de la fonction :

- passer des paramètres dans les registres

- réorganiser les paramètres pour l’alignement

- supprimer les paramètres inutilisés

Si une fonction est appelée via un pointeur de fonction, ou si une fonction est appelée en dehors d’un module qui est compilé à l’aide de **/GL**, le compilateur ne tente pas d’optimiser la convention d’appel de la fonction.

> [!NOTE]
> Si vous utilisez **/LTCG** et redéfinir `mainCRTStartup`, votre application peut avoir un comportement imprévisible qui est lié au code utilisateur qui s’exécute avant l’initialisation des objets globaux. Il existe trois façons de régler ce problème : ne pas redéfinir `mainCRTStartup`, ne pas compiler le fichier qui contient `mainCRTStartup` à l’aide de **/LTCG**, ou initialiser les variables globales et les objets de manière statique.

### <a name="ltcg-and-msil-modules"></a>/LTCG et les modules MSIL

Les modules compilés avec [/GL](gl-whole-program-optimization.md) et [/clr](clr-common-language-runtime-compilation.md) peuvent être utilisés comme entrée dans l'éditeur de liens si **/LTCG** est spécifié.

- **/ LTCG** peut accepter des fichiers objets natifs et fichiers d’objets natifs/managés mixtes (compilés avec **/CLR**). Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

- **/ LTCG : PGI** n’accepte pas de modules natifs compilés avec **/GL** et   **/CLR**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **général** page de propriétés.

1. Modifiez la propriété **Optimisation de l’ensemble du programme** .

Vous pouvez également appliquer **/LTCG** à des builds spécifiques en choisissant **Build** > **optimisation guidée par profil** sur la barre de menus, ou en choisissant une du profil Options d’optimisation guidées dans le menu contextuel du projet.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
