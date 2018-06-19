---
title: Options du compilateur classées par catégorie | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fff661bf573ca30a5b0e7550c2e53b00a7ff3d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379326"
---
# <a name="compiler-options-listed-by-category"></a>Options du compilateur classées par catégorie

Cet article contient une liste par catégorie d'options du compilateur. Pour obtenir une liste alphabétique, consultez [Options du compilateur classées par ordre alphabétique](compiler-options-listed-alphabetically.md).

### <a name="optimization"></a>Optimisation

|Option|Objectif|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Crée un code compact.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Crée un code rapide.|
|[/OB](ob-inline-function-expansion.md)|Contrôle l'expansion inline.|
|[/Od](od-disable-debug.md)|Désactive l'optimisation.|
|[/Og](og-global-optimizations.md)|Obsolète. Utilise des optimisations globales.|
|[/Oi](oi-generate-intrinsic-functions.md)|Génère des fonctions intrinsèques.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Favorise la taille du code.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Favorise la vitesse du code.|
|[/Ox](ox-full-optimization.md)|Utilise l'optimisation maximale (/Ob2gity /Gs).|
|[/Oy](oy-frame-pointer-omission.md)|Omet le pointeur de frame. (x86 uniquement)|
|[/favor](favor-optimize-for-architecture-specifics.md)|Produit du code optimisé pour une architecture spécifiée ou pour une plage d'architectures.|

### <a name="code-generation"></a>Génération de code

|Option|Objectif|
|------------|-------------|
|[/arch](arch-x86.md)|Utiliser des instructions SSE ou SSE2 dans la génération du code. (x86 uniquement)|
|[/clr](clr-common-language-runtime-compilation.md)|Produit un fichier de sortie à exécuter sur le CLR (Common Language Runtime).|
|[/EH](eh-exception-handling-model.md)|Spécifie le modèle de gestion des exceptions.|
|[/ FP](fp-specify-floating-point-behavior.md)|Spécifie le comportement de virgule flottante.|
|[/GA](ga-optimize-for-windows-application.md)|Optimise pour les applications Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Utilise la convention d'appel `__cdecl` . (x86 uniquement)|
|[/GE](ge-enable-stack-probes.md)|Obsolète. Active les tests de pile.|
|[/GF](gf-eliminate-duplicate-strings.md)|Active le regroupement des chaînes.|
|[/GH](gh-enable-penter-hook-function.md)|Appelle la fonction de raccordement `_penter`.|
|[/GH](gh-enable-pexit-hook-function.md)|Appelle la fonction de raccordement `_pexit`.|
|[/GL](gl-whole-program-optimization.md)|Active l'optimisation de l'ensemble du programme.|
|[/Gm](gm-enable-minimal-rebuild.md)|Active la régénération minimale.|
|[/GR](gr-enable-run-time-type-information.md)|Active les informations de type au moment de l'exécution (RTTI, Run-Time Type Information).|
|[GR](gd-gr-gv-gz-calling-convention.md)|Utilise la convention d'appel `__fastcall` . (x86 uniquement)|
|[/GS](gs-buffer-security-check.md)|Vérifie la sécurité des mémoires tampons.|
|[/ GS](gs-control-stack-checking-calls.md)|Gère les tests de pile.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Prend en charge la sécurité des fibres pour les données allouées en utilisant un stockage local des threads de type statique.|
|[/ Guard : CF](guard-enable-control-flow-guard.md)|Ajoute des vérifications de sécurité de protection du flux de contrôle.|
|[GV](gd-gr-gv-gz-calling-convention.md)|Utilise la convention d'appel `__vectorcall` . (x86 et x64 uniquement)|
|[/GW](gw-optimize-global-data.md)|Active l'optimisation globale des données de la totalité du programme.|
|[/GX](gx-enable-exception-handling.md)|Obsolète. Active la gestion synchrone des exceptions. Utilisez [/EH](eh-exception-handling-model.md) à la place.|
|[/Gy](gy-enable-function-level-linking.md)|Active la liaison au niveau des fonctions.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Obsolète. Active les vérifications rapides. (Identique à [/RTC1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Utilise la convention d'appel `__stdcall` . (x86 uniquement)|
|[/Homeparams](homeparams-copy-register-parameters-to-stack.md)|Force l'écriture des paramètres passés dans les registres à leurs emplacements sur la pile lors de l'entrée de la fonction. Cette option du compilateur est uniquement destinée aux compilateurs [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] (compilation native et croisée).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Crée une image corrigeable en mémoire.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Génère des fonctions transcendantes rapides.|
|[QIfist](qifist-suppress-ftol.md)|Obsolète. Supprime l'appel de la fonction d'assistance `_ftol` quand la conversion d'un type à virgule flottante vers un type intégral est requise. (x86 uniquement)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Supprime les commandes `fwait` dans les blocs `try` .|
|[/Qpar](qpar-auto-parallelizer.md)|Active la parallélisation automatique des boucles.|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|Active les niveaux de création de rapports pour la parallélisation automatique.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Utilise des instructions de déplacement d'entiers pour les valeurs à virgule flottante et désactive certaines optimisations de charge de virgule flottante.|
|[/Qspectre](qspectre.md)|Activer l’atténuation pour CVE 2017-5753, pour une classe d’attaques du Spectre.|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Active les niveaux de création de rapports pour le vectorisation automatique.|
|[/RTC](rtc-run-time-error-checks.md)|Active les vérifications des erreurs au moment de l'exécution.|
|[/ volatile](volatile-volatile-keyword-interpretation.md)|Sélectionne comment le mot clé volatile est interprété.|

### <a name="output-files"></a>Fichiers de sortie

|Option|Objectif|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Traite les commentaires de documentation pour les diriger vers un fichier XML.|
|[/FA](fa-fa-listing-file.md)|Configure un fichier de listes d'assemblys.|
|[/FA](fa-fa-listing-file.md)|Crée un fichier de listes d'assemblys.|
|[/Fd](fd-program-database-file-name.md)|Renomme le fichier de base de données du programme.|
|[/FE](fe-name-exe-file.md)|Renomme le fichier exécutable.|
|[/Fi](fi-preprocess-output-file-name.md)|Spécifie le nom du fichier de sortie prétraité.|
|[/Fm](fm-name-mapfile.md)|Crée un fichier de mappage.|
|[/FO](fo-object-file-name.md)|Crée un fichier objet.|
|[/ FP](fp-name-dot-pch-file.md)|Spécifie un nom de fichier d'en-tête précompilé.|
|[/ FR, /Fr](fr-fr-create-dot-sbr-file.md)|Nom généré des fichiers .sbr navigateur.|

### <a name="preprocessor"></a>Préprocesseur

|Option|Objectif|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Spécifie un répertoire à explorer afin de résoudre les références de fichiers passées à la directive [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/C](c-preserve-comments-during-preprocessing.md)|Conserve les commentaires pendant le prétraitement.|
|[/D](d-preprocessor-definitions.md)|Définit des constantes et des macros.|
|[/E](e-preprocess-to-stdout.md)|Copie la sortie du préprocesseur vers une sortie standard.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Copie la sortie du préprocesseur vers une sortie standard.|
|[/FI](fi-name-forced-include-file.md)|Prétraite le fichier Include spécifié.|
|[/FU](fu-name-forced-hash-using-file.md)|Force l'utilisation d'un nom de fichier, comme s'il avait été passé à la directive [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/Fx](fx-merge-injected-code.md)|Fusionne le code injecté avec le fichier source.|
|[/I](i-additional-include-directories.md)|Recherche des fichiers Include dans un répertoire.|
|[/P](p-preprocess-to-a-file.md)|Écrit la sortie du préprocesseur dans un fichier.|
|[/U](u-u-undefine-symbols.md)|Supprime une macro prédéfinie.|
|[/u](u-u-undefine-symbols.md)|Supprime toutes les macros prédéfinies.|
|[/X](x-ignore-standard-include-paths.md)|Ignore le répertoire Include standard.|

### <a name="language"></a>Langage

|Option|Objectif|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Évaluation de constexpr contrôle au moment de la compilation.|
|[/OpenMP](openmp-enable-openmp-2-0-support.md)|Active [#pragma omp](../../preprocessor/omp.md) dans le code source.|
|[/VD](vd-disable-construction-displacements.md)|Supprime ou active les membres masqués de la classe `vtordisp` .|
|[/vmb](vmb-vmg-representation-method.md)|Utilise la meilleure base pour les pointeurs vers des membres.|
|[/vmg](vmb-vmg-representation-method.md)|Utilise la généralité complète pour les pointeurs vers des membres.|
|[/ VMM](vmm-vms-vmv-general-purpose-representation.md)|Déclare un héritage multiple.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Déclare un héritage simple.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Déclare un héritage virtuel.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Génère compatible C 7.0 informations de débogage.|
|[/Za](za-ze-disable-language-extensions.md)|Désactive les extensions de langage.|
|[/Zc](zc-conformance.md)|Spécifie le comportement standard sous [/Ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Obsolète. Active les extensions de langage.|
|[/Zf](zf.md)|Améliore les temps de génération dans des builds parallèles PDB.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Inclut des informations de débogage dans une base de données du programme compatible avec Modifier & Continuer. (x86 uniquement)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Génère des informations de débogage complètes.|
|[/Zl](zl-omit-default-library-name.md)|Supprime le nom de la bibliothèque par défaut du fichier .obj.|
|[/Zp](zp-struct-member-alignment.md) *n*|Compresse les membres de la structure.|
|[/Zs](zs-syntax-check-only.md)|Vérifie la syntaxe uniquement.|
|[/ZW](zw-windows-runtime-compilation.md)|Génère un fichier de sortie à exécuter sur le Windows Runtime.|

### <a name="linking"></a>Liaison

|Option|Objectif|
|------------|-------------|
|[/F](f-set-stack-size.md)|Définit la taille de la pile.|
|[/LD](md-mt-ld-use-run-time-library.md)|Crée une bibliothèque de liens dynamiques.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Crée une bibliothèque de liens dynamiques de débogage.|
|[/link](link-pass-options-to-linker.md)|Passe l'option spécifiée à LINK.|
|[/LN](ln-create-msil-module.md)|Crée un module MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Compile pour créer une DLL multithread, à l'aide de MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Compile pour créer une DLL multithread de débogage, à l'aide de MSVCRTD.lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Compile pour créer un fichier exécutable multithread, à l'aide de LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Compile pour créer un fichier exécutable multithread de débogage, à l'aide de LIBCMTD.lib.|

### <a name="miscellaneous"></a>Divers

|Option|Objectif|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Affiche la liste des options du compilateur.|
|[@](at-specify-a-compiler-response-file.md)|Spécifie un fichier réponse.|
|[/ analyze](analyze-code-analysis.md)|Active l'analyse du code.|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Augmente le nombre de sections adressables dans un fichier .obj.|
|[/c](c-compile-without-linking.md)|Compile sans liaison.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Spécifie le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Vous permet de signaler les erreurs internes du compilateur (ICE) directement à l'équipe Visual C++.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Affiche le chemin d'accès complet des fichiers de code source passés à cl.exe dans un texte de diagnostic.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Force la sérialisation des écritures dans le fichier de base de données de programme (PDB) via MSPDBSRV.EXE.|
|[/H](h-restrict-length-of-external-names.md)|Obsolète. Limite la longueur des noms externes (publics).|
|[/ HELP](help-compiler-command-line-help.md)|Affiche la liste des options du compilateur.|
|[/J](j-default-char-type-is-unsigned.md)|Change le type `char` par défaut.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Le compilateur et l'éditeur de liens créeront un binaire qui peut être exécuté dans le noyau Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Génère plusieurs fichiers sources simultanément.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Supprime l'affichage de la bannière d'ouverture de session.|
|[/sdl](sdl-enable-additional-security-checks.md)|Active des fonctionnalités de sécurité et ses avertissements supplémentaires.|
|[/showIncludes](showincludes-list-include-files.md)|Affiche la liste de tous les fichiers Include pendant la compilation.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Spécifie un fichier source C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Spécifie tous les fichiers sources C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Spécifie un fichier source C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Spécifie tous les fichiers sources C++.|
|[/V](v-version-number.md)|Obsolète. Définit la chaîne version.|
|[/w](compiler-option-warning-level.md)|Désactive tous les avertissements.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Définit le niveau d’avertissement de sortie.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Définit le niveau de l’avertissement spécifié.|
|[/Wall](compiler-option-warning-level.md)|Active tous les avertissements, y compris les avertissements qui sont désactivés par défaut.|
|[/wd](compiler-option-warning-level.md)|Désactive l’avertissement spécifié.|
|[/we](compiler-option-warning-level.md)|Traite l’avertissement spécifié comme une erreur.|
|[/WL](wl-enable-one-line-diagnostics.md)|Active un diagnostic de ligne pour les messages d'erreur et d'avertissement lors de la compilation du code source C++ à partir de la ligne de commande.|
|[/WO](compiler-option-warning-level.md)|Affiche l’avertissement spécifié une seule fois.|
|[/Wv](compiler-option-warning-level.md)|Désactive les avertissements introduits par les versions ultérieures du compilateur.|
|[/WX](compiler-option-warning-level.md)|Traite les avertissements comme des erreurs.|
|[/Yc](yc-create-precompiled-header-file.md)|Créer. Aucun fichier PCH.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Obsolète. Place des informations de débogage complètes dans tous les fichiers objets. Utilisez [/Zi](z7-zi-zi-debug-information-format.md) à la place.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Injecte une référence PCH lors de la création d'une bibliothèque de débogage.|
|[/Yu](yu-use-precompiled-header-file.md)|Utilise un fichier d'en-tête précompilé pendant la génération.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignore toutes les autres options d'en-tête précompilé pour la génération en cours.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Spécifie la limite d'allocation de mémoire de l'en-tête précompilé.|
|[/ await](await-enable-coroutine-support.md)|Activer les coroutines (fonctions peut être reprises) des extensions.|
|[/source-charset](source-charset-set-source-character-set.md)|Ensemble de jeu de caractères source.|
|[/execution-charset](execution-charset-set-execution-character-set.md)|Jeu de caractères de l’exécution de jeu.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Jeux de caractères de source et de l’exécution de jeu UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Valider les fichiers UTF-8 pour que les caractères compatibles.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Contrôle le format des messages de diagnostic.|
|[/ permissive-](permissive-standards-conformance.md)|Définir le mode standard de la conformité.|
|[/std](std-specify-language-standard-version.md)|Sélecteur de compatibilité de version de la norme C++.|

### <a name="deprecated-and-removed-compiler-options"></a>Options du compilateur déconseillées et supprimées

|Option|Objectif|
|------------|-------------|
|[/ CLR : noAssembly](clr-common-language-runtime-compilation.md)|Obsolète. Utilisez [/LN (créer un Module MSIL)](ln-create-msil-module.md) à la place.|
|[/Fr](fr-fr-create-dot-sbr-file.md)|Obsolète. Crée un fichier d’informations de consultation sans variables locales.|
|[/GE](ge-enable-stack-probes.md)|Obsolète. Active les tests de pile. Activé par défaut.|
|[/GX](gx-enable-exception-handling.md)|Obsolète. Active la gestion synchrone des exceptions. Utilisez [/EH](eh-exception-handling-model.md) à la place.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Obsolète. Active les vérifications rapides. Utilisez [/RTC1](rtc-run-time-error-checks.md) à la place.|
|[/H](h-restrict-length-of-external-names.md)|Obsolète. Limite la longueur des noms externes (publics).|
|[/Og](og-global-optimizations.md)|Obsolète. Utilise des optimisations globales.|
|[QIfist](qifist-suppress-ftol.md)|Obsolète. Était utilisé pour spécifier le mode de conversion d’un type à virgule flottante en type intégral.|
|[/V](v-version-number.md)|Obsolète. Définit la chaîne de version du fichier .obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Obsolète. Détecte les problèmes de portabilité 64 bits.|
|[/Yd](yd-place-debug-information-in-object-file.md)|Obsolète. Place des informations de débogage complètes dans tous les fichiers objets. Utilisez [/Zi](z7-zi-zi-debug-information-format.md) à la place.|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|Obsolète. Désactive la conformité dans la portée d’une boucle for.|
|[/Ze](za-ze-disable-language-extensions.md)|Obsolète. Active les extensions de langage.|
|[/Zg](zg-generate-function-prototypes.md)|Supprimé dans Visual C++ 2015. Génère des prototypes de fonction.|

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](c-cpp-building-reference.md)<br/>
[Options du compilateur](compiler-options.md)<br/>
[Définition des options du compilateur](setting-compiler-options.md)<br/>
