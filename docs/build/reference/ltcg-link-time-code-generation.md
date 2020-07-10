---
title: /LTCG (Génération de code durant l’édition de liens)
description: L’option de l’éditeur de liens MSVC/LTCG active la génération de code durant l’édition de liens pour l’optimisation de l’ensemble du programme.
ms.date: 07/08/2020
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
ms.openlocfilehash: c954794d6d0fd087eee74ebb7e86d77b89a9a8fc
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180797"
---
# <a name="ltcg-link-time-code-generation"></a>`/LTCG`(Génération de code durant l’édition de liens)

Utilisez **`/LTCG`** pour effectuer l’optimisation de l’ensemble du programme, ou pour créer l’instrumentation de l’optimisation guidée par profil (PGO), effectuer une formation et créer des builds optimisées par profil.

## <a name="syntax"></a>Syntaxe

> **`/LTCG`**[**`:`**{**`INCREMENTAL`**|**`NOSTATUS`**|**`STATUS`**|**`OFF`**}]

Ces options sont dépréciées à partir de Visual Studio 2015 :

> **`/LTCG:`**{**`PGINSTRUMENT`**|**`PGOPTIMIZE`**|**`PGUPDATE`**}

### <a name="arguments"></a>Arguments

**`INCREMENTAL`**<br/>
Facultatif Spécifie que l’éditeur de liens applique uniquement l’optimisation de l’ensemble du programme ou la génération du code durant l’édition de liens (LTCG) aux fichiers affectés par une modification, au lieu du projet entier. Par défaut, cet indicateur n’est pas défini lorsque **`/LTCG`** est spécifié, et l’ensemble du projet est lié à l’aide de l’optimisation de l’ensemble du programme.

**`NOSTATUS`**&#124;**`STATUS`**<br/>
(Facultatif) Spécifie si l’éditeur de liens affiche un indicateur de progression qui montre le pourcentage d’exécution du lien. Par défaut, ces informations d’État ne sont pas affichées.

**`OFF`**<br/>
(Facultatif) Désactive la génération de code durant l’édition de liens. Ce comportement est le même que lorsque **`/LTCG`** n’est pas spécifié sur la ligne de commande.

**`PGINSTRUMENT`**<br/>
(Facultatif) Cette option est dépréciée à partir de Visual Studio 2015. Utilisez plutôt **`/LTCG`** and `[/GENPROFILE` ou `/FASTGENPROFILE` ] (genprofile-fastgenprofile-Generate-Profiling-Instrumented-Build.MD) pour générer une build instrumentée pour l’optimisation guidée par profil. Les données recueillies à partir des séries de tests instrumentées sont utilisées pour créer une image optimisée. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **`/LTCG:PGI`** .

**`PGOPTIMIZE`**<br/>
(Facultatif) Cette option est dépréciée à partir de Visual Studio 2015. Au lieu de cela, utilisez **`/LTCG`** et [`/USEPROFILE`](useprofile.md) pour générer une image optimisée. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **`/LTCG:PGO`** .

**`PGUPDATE`**<br/>
(Facultatif) Cette option est dépréciée à partir de Visual Studio 2015. Au lieu de cela, utilisez **`/LTCG`** et **`/USEPROFILE`** pour reconstruire une image optimisée. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md). La forme abrégée de cette option est **`/LTCG:PGU`** .

## <a name="remarks"></a>Notes

L' **`/LTCG`** option indique à l’éditeur de liens d’appeler le compilateur et d’effectuer l’optimisation de l’ensemble du programme. Vous pouvez également effectuer l’optimisation guidée par profil. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md).

Avec les exceptions suivantes, vous ne pouvez pas ajouter d’options de l’éditeur de liens à la combinaison PGO de **`/LTCG`** et qui n’ont pas été **`/USEPROFILE`** spécifiées dans la combinaison d’initialisation PGO précédente des **`/LTCG`** **`/GENPROFILE`** options et :

- [`/BASE`](base-base-address.md)

- [`/FIXED`](fixed-fixed-base-address.md)

- **`/LTCG`**

- [`/MAP`](map-generate-mapfile.md)

- [`/MAPINFO`](mapinfo-include-information-in-mapfile.md)

- [`/NOLOGO`](nologo-suppress-startup-banner-linker.md)

- [`/OUT`](out-output-file-name.md)

- [`/PGD`](pgd-specify-database-for-profile-guided-optimizations.md)

- [`/PDB`](pdb-use-program-database.md)

- [`/PDBSTRIPPED`](pdbstripped-strip-private-symbols.md)

- [`/STUB`](stub-ms-dos-stub-file-name.md)

- [`/VERBOSE`](verbose-print-progress-messages.md)

Toutes les options de l’éditeur de liens spécifiées avec les **`/LTCG`** **`/GENPROFILE`** options et pour initialiser PGO n’ont pas besoin d’être spécifiées lors de la génération à l’aide **`/LTCG`** de et **`/USEPROFILE`** ; elles sont implicites.

Le reste de cet article décrit la génération de code durant l’édition de liens effectuée par **`/LTCG`** .

**`/LTCG`** est implicite avec [`/GL`](gl-whole-program-optimization.md) .

L’éditeur de liens appelle la génération de code durant l’édition de liens s’il reçoit un module qui a été compilé à l’aide de **`/GL`** ou d’un module MSIL (consultez [ `.netmodule` fichiers en tant qu’entrée](netmodule-files-as-linker-input.md)de l’éditeur de liens). Si vous ne spécifiez pas explicitement **`/LTCG`** quand vous transmettez des **`/GL`** modules MSIL à l’éditeur de liens, l’éditeur de liens détecte finalement cette situation et redémarre le lien à l’aide de **`/LTCG`** . Spécifiez explicitement **`/LTCG`** quand vous transmettez **`/GL`** des modules MSIL à l’éditeur de liens pour obtenir des performances de génération plus rapides.

Pour des performances encore plus rapides, utilisez **`/LTCG:INCREMENTAL`** . Cette option indique à l’éditeur de liens de réoptimiser uniquement les fichiers affectés par la modification d’un fichier source, et non le projet entier. Cette option peut réduire considérablement le temps nécessaire à la liaison. Cette option n’est pas la même option que les [liens incrémentiels](incremental-link-incrementally.md).

**`/LTCG`** n’est pas valide pour une utilisation avec [`/INCREMENTAL`](incremental-link-incrementally.md) .

Lorsque **`/LTCG`** est utilisé pour lier des modules compilés à l’aide de [`/Og`](og-global-optimizations.md) , [`/O1`](o1-o2-minimize-size-maximize-speed.md) , [`/O2`](o1-o2-minimize-size-maximize-speed.md) ou [`/Ox`](ox-full-optimization.md) , les optimisations suivantes sont effectuées :

- Expansion inline entre modules

- Allocation de registre interprocédurale (seulement sur les systèmes d’exploitation 64 bits)

- Convention d’appel personnalisée (x86 uniquement)

- Déplacement TLS réduit (x86 uniquement)

- Alignement de pile double (x86 uniquement)

- Levée d’ambiguïté améliorée de la mémoire (meilleures informations d’interférence pour les variables globales et les paramètres d’entrée)

> [!NOTE]
> L’éditeur de liens détermine les optimisations qui ont été utilisées pour compiler chaque fonction et applique les mêmes optimisations au moment de la liaison.

L’utilisation **`/LTCG`** de et de **`/O2`** provoque une optimisation à double alignement.

Si **`/LTCG`** et **`/O1`** sont spécifiés, le double alignement n’est pas effectué. Si la plupart des fonctions d’une application sont compilées pour la vitesse, avec quelques fonctions compilées pour la taille (par exemple, à l’aide du [`optimize`](../../preprocessor/optimize.md) pragma), le compilateur double-aligne les fonctions optimisées pour la taille si elles appellent des fonctions qui requièrent un double alignement.

Si le compilateur peut identifier tous les sites d’appel d’une fonction, le compilateur ignore les modificateurs de convention d’appel explicites sur une fonction et tente d’optimiser la convention d’appel de la fonction :

- passer des paramètres dans les registres

- réorganiser les paramètres pour l’alignement

- supprimer les paramètres inutilisés

Si une fonction est appelée via un pointeur de fonction, ou si une fonction est appelée en dehors d’un module qui est compilé à l’aide de **`/GL`** , le compilateur ne tente pas d’optimiser la Convention d’appel de la fonction.

> [!NOTE]
> Si vous utilisez **`/LTCG`** et redéfinissez `mainCRTStartup` , votre application peut avoir un comportement imprévisible qui se réfère au code utilisateur qui s’exécute avant l’initialisation des objets globaux. Il existe trois façons de résoudre ce problème : ne pas redéfinir `mainCRTStartup` , ne pas compiler le fichier qui contient `mainCRTStartup` à l’aide de **`/LTCG`** , ni initialiser des variables globales et des objets statiquement.

### <a name="ltcg-and-msil-modules"></a>`/LTCG`et modules MSIL

Les modules compilés à l’aide [`/GL`](gl-whole-program-optimization.md) de et [`/clr`](clr-common-language-runtime-compilation.md) peuvent être utilisés comme entrée de l’éditeur de liens lorsque **`/LTCG`** est spécifié.

- **`/LTCG`** peut accepter des fichiers objets natifs et des fichiers objets natifs/managés mixtes (compilés à l’aide de **`/clr`** ). Les **`/clr:pure`** **`/clr:safe`** Options du compilateur et sont dépréciées dans visual studio 2015 et ne sont pas prises en charge dans visual studio 2017 et versions ultérieures.

- **`/LTCG:PGI`** n’accepte pas les modules natifs compilés à l’aide **`/GL`** de et**`/clr`**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés général **Propriétés de configuration**  >  **General** .

1. Modifiez la propriété **Optimisation de l’ensemble du programme** .

Vous pouvez également appliquer **`/LTCG`** à des builds spécifiques **Build**en choisissant l'  >  **optimisation guidée par profil** de build dans la barre de menus, ou en choisissant l’une des options d’optimisation guidée par profil dans le menu contextuel du projet.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)\
[Options de l’éditeur de liens MSVC](linker-options.md)
