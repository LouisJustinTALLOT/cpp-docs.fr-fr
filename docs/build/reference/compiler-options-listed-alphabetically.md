---
title: Options du compilateur classées par ordre alphabétique
description: Liste de références dans l’ordre alphabétique des options de ligne de commande du compilateur Microsoft C/C++.
ms.date: 07/29/2020
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 81f2fbfe385e8655193c5862455e6ffca3719c96
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520860"
---
# <a name="compiler-options-listed-alphabetically"></a>Options du compilateur classées par ordre alphabétique

Ce tableau contient une liste alphabétique des options du compilateur. Pour obtenir la liste des options du compilateur par catégorie, consultez l’article [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md) .

## <a name="compiler-options"></a>Options du compilateur

| Option | Objectif |
|--|--|
| [`@`](at-specify-a-compiler-response-file.md) | Spécifie un fichier réponse. |
| [`/?`](help-compiler-command-line-help.md) | Affiche la liste des options du compilateur. |
| [`/AI`](ai-specify-metadata-directories.md) | Spécifie un répertoire à explorer afin de résoudre les références de fichiers passées à la [`#using`](../../preprocessor/hash-using-directive-cpp.md) directive. |
| [`/analyze`](analyze-code-analysis.md) | Active l'analyse du code. |
| [`/arch`](arch-minimum-cpu-architecture.md) | Spécifie l'architecture pour la génération de code. |
| [`/await`](await-enable-coroutine-support.md) | Activez les extensions (fonctions pouvant être reprises). |
| [`/bigobj`](bigobj-increase-number-of-sections-in-dot-obj-file.md) | Augmente le nombre de sections adressables dans un fichier .obj. |
| [`/C`](c-preserve-comments-during-preprocessing.md) | Conserve les commentaires pendant le prétraitement. |
| [`/c`](c-compile-without-linking.md) | Compile sans liaison. |
| [`/cgthreads`](cgthreads-code-generation-threads.md) | Spécifie le nombre de threads de cl.exe à utiliser pour l'optimisation et la génération de code. |
| [`/clr`](clr-common-language-runtime-compilation.md) | Produit un fichier de sortie à exécuter sur le CLR (Common Language Runtime). |
| [`/constexpr`](constexpr-control-constexpr-evaluation.md) | Contrôler l' **`constexpr`** évaluation au moment de la compilation. |
| [`/D`](d-preprocessor-definitions.md) | Définit des constantes et des macros. |
| [`/diagnostics`](diagnostics-compiler-diagnostic-options.md) | Contrôle le format des messages de diagnostic. |
| [`/doc`](doc-process-documentation-comments-c-cpp.md) | Traite les commentaires de documentation pour les diriger vers un fichier XML. |
| [`/E`](e-preprocess-to-stdout.md) | Copie la sortie du préprocesseur vers une sortie standard. |
| [`/EH`](eh-exception-handling-model.md) | Spécifie le modèle de gestion des exceptions. |
| [`/EP`](ep-preprocess-to-stdout-without-hash-line-directives.md) | Copie la sortie du préprocesseur vers une sortie standard. |
| [`/errorReport`](errorreport-report-internal-compiler-errors.md) | Action déconseillée. Le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
| [`/execution-charset`](execution-charset-set-execution-character-set.md) | Définir le jeu de caractères d’exécution. |
| [`/experimental:module`](experimental-module.md) | Active la prise en charge des modules expérimentaux. |
| [`/experimental:preprocessor`](experimental-preprocessor.md) | Active la prise en charge de préprocesseur conforme aux expérimentations. |
| [`/F`](f-set-stack-size.md) | Définit la taille de la pile. |
| [`/favor`](favor-optimize-for-architecture-specifics.md) | Produit du code optimisé pour une architecture x64 spécifique. Ou, pour les micro-architectures spécifiques dans les architectures AMD64 et EM64T. |
| [`/FA`](fa-fa-listing-file.md) | Crée un fichier listing. |
| [`/Fa`](fa-fa-listing-file.md) | Définit le nom du fichier listing. |
| [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) | Affiche le chemin d'accès complet des fichiers de code source passés à cl.exe dans un texte de diagnostic. |
| [`/Fd`](fd-program-database-file-name.md) | Renomme le fichier de base de données du programme. |
| [`/Fe`](fe-name-exe-file.md) | Renomme le fichier exécutable. |
| [`/FI`](fi-name-forced-include-file.md) | Prétraite le fichier Include spécifié. |
| [`/Fi`](fi-preprocess-output-file-name.md) | Définit le nom de fichier de sortie prétraité. |
| [`/Fm`](fm-name-mapfile.md) | Crée un fichier de mappage. |
| [`/Fo`](fo-object-file-name.md) | Crée un fichier objet. |
| [`/fp`](fp-specify-floating-point-behavior.md) | Spécifie le comportement de virgule flottante. |
| [`/Fp`](fp-name-dot-pch-file.md) | Spécifie un nom de fichier d'en-tête précompilé. |
| [`/FR`](fr-fr-create-dot-sbr-file.md)<br /><br /> [`/Fr`](fr-fr-create-dot-sbr-file.md) | Génère des fichiers browser. **`/Fr`** est déconseillé. |
| [`/FS`](fs-force-synchronous-pdb-writes.md) | Force la sérialisation de toutes les écritures dans le fichier de base de données du programme (PDB) via MSPDBSRV.EXE. |
| [`/FU`](fu-name-forced-hash-using-file.md) | Force l’utilisation d’un nom de fichier comme s’il avait été passé à la [`#using`](../../preprocessor/hash-using-directive-cpp.md) directive. |
| [`/Fx`](fx-merge-injected-code.md) | Fusionne le code injecté avec le fichier source. |
| [`/GA`](ga-optimize-for-windows-application.md) | Optimise le code pour une application Windows. |
| [`/Gd`](gd-gr-gv-gz-calling-convention.md) | Utilise la **`__cdecl`** Convention d’appel (x86 uniquement). |
| [`/Ge`](ge-enable-stack-probes.md) | Action déconseillée. Active les tests de pile. |
| [`/GF`](gf-eliminate-duplicate-strings.md) | Active le regroupement des chaînes. |
| [`/GH`](gh-enable-pexit-hook-function.md) | Appelle la fonction de raccordement `_pexit`. |
| [`/Gh`](gh-enable-penter-hook-function.md) | Appelle la fonction de raccordement `_penter`. |
| [`/GL`](gl-whole-program-optimization.md) | Active l'optimisation de l'ensemble du programme. |
| [`/Gm`](gm-enable-minimal-rebuild.md) | Action déconseillée. Active la régénération minimale. |
| [`/GR`](gr-enable-run-time-type-information.md) | Active les informations de type au moment de l'exécution (RTTI, Run-Time Type Information). |
| [`/Gr`](gd-gr-gv-gz-calling-convention.md) | Utilise la **`__fastcall`** Convention d’appel (x86 uniquement). |
| [`/GS`](gs-buffer-security-check.md) | Active les contrôles de sécurité des mémoires tampons. |
| [`/Gs`](gs-control-stack-checking-calls.md) | Gère les tests de pile. |
| [`/GT`](gt-support-fiber-safe-thread-local-storage.md) | Prend en charge la sécurité des fibres pour les données allouées en utilisant un stockage local des threads de type statique. |
| [`/guard:cf`](guard-enable-control-flow-guard.md) | Ajoute des vérifications de sécurité de protection du flux de contrôle. |
| [`/guard:ehcont`](guard-enable-eh-continuation-metadata.md) | Active les métadonnées de continuation EH. |
| [`/Gv`](gd-gr-gv-gz-calling-convention.md) | Utilise la **`__vectorcall`** Convention d’appel. (x86 et x64 uniquement) |
| [`/Gw`](gw-optimize-global-data.md) | Active l'optimisation globale des données de la totalité du programme. |
| [`/GX`](gx-enable-exception-handling.md) | Action déconseillée. Active la gestion synchrone des exceptions. Utilisez à la [`/EH`](eh-exception-handling-model.md) place. |
| [`/Gy`](gy-enable-function-level-linking.md) | Active la liaison au niveau des fonctions. |
| [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) | Action déconseillée. Identique à [`/RTC1`](rtc-run-time-error-checks.md) . |
| [`/Gz`](gd-gr-gv-gz-calling-convention.md) | Utilise la **`__stdcall`** Convention d’appel (x86 uniquement). |
| [`/H`](h-restrict-length-of-external-names.md) | Action déconseillée. Limite la longueur des noms externes (publics). |
| [`/HELP`](help-compiler-command-line-help.md) | Affiche la liste des options du compilateur. |
| [`/homeparams`](homeparams-copy-register-parameters-to-stack.md) | Force l'écriture des paramètres passés dans les registres à leurs emplacements sur la pile lors de l'entrée de la fonction. Cette option du compilateur concerne uniquement les compilateurs x64 (Native et Cross compile). |
| [`/hotpatch`](hotpatch-create-hotpatchable-image.md) | Crée une image corrigeable à chaud. |
| [`/I`](i-additional-include-directories.md) | Recherche des fichiers Include dans un répertoire. |
| [`/J`](j-default-char-type-is-unsigned.md) | Modifie le type par défaut **`char`** . |
| [`/JMC`](jmc.md) | Prend en charge le débogage Uniquement mon code en C++ natif. |
| [`/kernel`](kernel-create-kernel-mode-binary.md) | Le compilateur et l'éditeur de liens créeront un binaire qui peut être exécuté dans le noyau Windows. |
| [`/LD`](md-mt-ld-use-run-time-library.md) | Crée une bibliothèque de liens dynamiques. |
| [`/LDd`](md-mt-ld-use-run-time-library.md) | Crée une bibliothèque de liens dynamiques de débogage. |
| [`/link`](link-pass-options-to-linker.md) | Passe l'option spécifiée à LINK. |
| [`/LN`](ln-create-msil-module.md) | Crée un module MSIL. |
| [`/MD`](md-mt-ld-use-run-time-library.md) | Crée une DLL multithread avec MSVCRT.lib. |
| [`/MDd`](md-mt-ld-use-run-time-library.md) | Crée une DLL multithread de débogage avec MSVCRTD.lib. |
| [`/MP`](mp-build-with-multiple-processes.md) | Compile plusieurs fichiers sources à l'aide de plusieurs processus. |
| [`/MT`](md-mt-ld-use-run-time-library.md) | Crée un fichier exécutable multithread avec LIBCMT.lib. |
| [`/MTd`](md-mt-ld-use-run-time-library.md) | Crée un fichier exécutable de débogage avec LIBCMTD.lib. |
| [`/nologo`](nologo-suppress-startup-banner-c-cpp.md) | Supprime l'affichage de la bannière d'ouverture de session. |
| [`/O1`](o1-o2-minimize-size-maximize-speed.md) | Crée un code compact. |
| [`/O2`](o1-o2-minimize-size-maximize-speed.md) | Crée un code rapide. |
| [`/Ob`](ob-inline-function-expansion.md) | Contrôle l'expansion inline. |
| [`/Od`](od-disable-debug.md) | Désactive l'optimisation. |
| [`/Og`](og-global-optimizations.md) | Action déconseillée. Utilise des optimisations globales. |
| [`/Oi`](oi-generate-intrinsic-functions.md) | Génère des fonctions intrinsèques. |
| [`/openmp`](openmp-enable-openmp-2-0-support.md) | Active la [`#pragma omp`](../../preprocessor/omp.md) directive dans le code source. |
| [`/Os`](os-ot-favor-small-code-favor-fast-code.md) | Favorise la taille du code. |
| [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) | Favorise la vitesse du code. |
| [`/Ox`](ox-full-optimization.md) | Un sous-ensemble de/O2 qui n’inclut pas/GF ou/GY. |
| [`/Oy`](oy-frame-pointer-omission.md) | Omet le pointeur de frame (x86 uniquement). |
| [`/P`](p-preprocess-to-a-file.md) | Écrit la sortie du préprocesseur dans un fichier. |
| [`/permissive-`](permissive-standards-conformance.md) | Définissez le mode de conformité standard. |
| [`/Qfast_transcendentals`](qfast-transcendentals-force-fast-transcendentals.md) | Génère des fonctions transcendantes rapides. |
| [`/QIfist`](qifist-suppress-ftol.md) | Action déconseillée. Supprime `_ftol` lorsque la conversion d'un type à virgule flottante vers un type intégral est requise (x86 uniquement). |
| [`/Qimprecise_fwaits`](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md) | Supprime les `fwait` commandes à l’intérieur des **`try`** blocs. |
| [`/QIntel-jcc-erratum`](qintel-jcc-erratum.md) | Atténue l’impact sur les performances de la mise à jour du microcode Intel CMC vérification du défaut. |
| [/QPAR (auto-paralléliseur)](qpar-auto-parallelizer.md) | Active la parallélisation automatique des boucles marquées avec la directive [#pragma loop()](../../preprocessor/loop.md) . |
| [`/Qsafe_fp_loads`](qsafe-fp-loads.md) | Utilise des instructions de déplacement d'entiers pour les valeurs à virgule flottante et désactive certaines optimisations de charge de virgule flottante. |
| [`/Qspectre`](qspectre.md) | Spécifie la génération par le compilateur d’instructions pour atténuer certaines failles de sécurité Spectre Variant 1. |
| [`/Qspectre-load`](qspectre-load.md) | Spécifie la génération par le compilateur des instructions de sérialisation pour atténuer les vulnérabilités de sécurité spectre en fonction des instructions de chargement. |
| [`/Qspectre-load-cf`](qspectre-load-cf.md) | Spécifie la génération par le compilateur des instructions de sérialisation pour atténuer les vulnérabilités de sécurité spectre en fonction des instructions de workflow de contrôle qui chargent la mémoire. |
| [`/Qvec-report`(Niveau de rapport de vectoriseur automatique)](qvec-report-auto-vectorizer-reporting-level.md) | Active les niveaux de création de rapports pour le vectorisation automatique. |
| [`/RTC`](rtc-run-time-error-checks.md) | Active les vérifications des erreurs au moment de l'exécution. |
| [`/sdl`](sdl-enable-additional-security-checks.md) | Active des fonctionnalités de sécurité et ses avertissements supplémentaires. |
| [`/showIncludes`](showincludes-list-include-files.md) | Affiche une liste des fichiers Include pendant la compilation. |
| [`/source-charset`](source-charset-set-source-character-set.md) | Définir le jeu de caractères source. |
| [`/sourceDependencies`](sourcedependencies.md) | En-têtes de liste, modules et autres dépendances sources. |
| [`/std`](std-specify-language-standard-version.md) | Sélecteur de compatibilité de version standard C++. |
| [`/Tc`](tc-tp-tc-tp-specify-source-file-type.md) | Spécifie un fichier source C. |
| [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) | Spécifie que tous les fichiers sources sont C. |
| [`/Tp`](tc-tp-tc-tp-specify-source-file-type.md) | Spécifie un fichier source C++. |
| [`/TP`](tc-tp-tc-tp-specify-source-file-type.md) | Spécifie que tous les fichiers sources sont en C++. |
| [`/U`](u-u-undefine-symbols.md) | Supprime une macro prédéfinie. |
| [`/u`](u-u-undefine-symbols.md) | Supprime toutes les macros prédéfinies. |
| [`/utf-8`](utf-8-set-source-and-executable-character-sets-to-utf-8.md) | Définissez les jeux de caractères source et d’exécution sur UTF-8. |
| [`/V`](v-version-number.md) | Action déconseillée. Définit la chaîne de version du fichier .obj. |
| [`/validate-charset`](validate-charset-validate-for-compatible-characters.md) | Validez les fichiers UTF-8 uniquement pour les caractères compatibles. |
| [`/vd`](vd-disable-construction-displacements.md) | Supprime ou active les membres masqués de la classe vtordisp. |
| [`/vmb`](vmb-vmg-representation-method.md) | Utilise la meilleure base pour les pointeurs vers des membres. |
| [`/vmg`](vmb-vmg-representation-method.md) | Utilise la généralité complète pour les pointeurs vers des membres. |
| [`/vmm`](vmm-vms-vmv-general-purpose-representation.md) | Déclare un héritage multiple. |
| [`/vms`](vmm-vms-vmv-general-purpose-representation.md) | Déclare un héritage simple. |
| [`/vmv`](vmm-vms-vmv-general-purpose-representation.md) | Déclare un héritage virtuel. |
| [`/volatile`](volatile-volatile-keyword-interpretation.md) | Sélectionne comment le mot clé volatile est interprété. |
| [`/w`](compiler-option-warning-level.md) | Désactive tous les avertissements. |
| [`/W0`, `/W1`, `/W2`, `/W3`, `/W4`](compiler-option-warning-level.md) | Définit le niveau d’avertissement de sortie. |
| [`/w1`, `/w2`, `/w3`, `/w4`](compiler-option-warning-level.md) | Définit le niveau de l’avertissement spécifié. |
| [`/Wall`](compiler-option-warning-level.md) | Active tous les avertissements, y compris les avertissements qui sont désactivés par défaut. |
| [`/wd`](compiler-option-warning-level.md) | Désactive l’avertissement spécifié. |
| [`/we`](compiler-option-warning-level.md) | Traite l’avertissement spécifié comme une erreur. |
| [`/WL`](wl-enable-one-line-diagnostics.md) | Active un diagnostic de ligne pour les messages d'erreur et d'avertissement lors de la compilation du code source C++ à partir de la ligne de commande. |
| [`/wo`](compiler-option-warning-level.md) | Affiche l’avertissement spécifié une seule fois. |
| [`/Wp64`](wp64-detect-64-bit-portability-issues.md) | Obsolète. Détecte les problèmes de portabilité 64 bits. |
| [`/Wv`](compiler-option-warning-level.md) | N’affiche aucun avertissement introduit après la version spécifiée du compilateur. |
| [`/WX`](compiler-option-warning-level.md) | Traite tous les avertissements comme des erreurs. |
| [`/X`](x-ignore-standard-include-paths.md) | Ignore le répertoire Include standard. |
| [`/Y-`](y-ignore-precompiled-header-options.md) | Ignore toutes les autres options d'en-tête précompilé pour la génération en cours. |
| [`/Yc`](yc-create-precompiled-header-file.md) | Crée un fichier d'en-tête précompilé. |
| [`/Yd`](yd-place-debug-information-in-object-file.md) | Action déconseillée. Place des informations de débogage complètes dans tous les fichiers objets. Utilisez à la [`/Zi`](z7-zi-zi-debug-information-format.md) place. |
| [`/Yl`](yl-inject-pch-reference-for-debug-library.md) | Injecte une référence PCH lors de la création d'une bibliothèque de débogage. |
| [`/Yu`](yu-use-precompiled-header-file.md) | Utilise un fichier d'en-tête précompilé pendant la génération. |
| [`/Z7`](z7-zi-zi-debug-information-format.md) | Génère des informations de débogage compatibles C 7,0. |
| [`/Za`](za-ze-disable-language-extensions.md) | Désactive les extensions de langage. |
| [`/Zc`](zc-conformance.md) | Spécifie les comportements standard. |
| [`/Ze`](za-ze-disable-language-extensions.md) | Action déconseillée. Active les extensions de langage. |
| [`/Zf`](zf.md) | Améliore la génération PDB dans les builds parallèles. |
| [`/Zg`](zg-generate-function-prototypes.md) | Supprimé dans Visual Studio 2015. Génère des prototypes de fonction. |
| [`/ZH`](zh.md) | Spécifie MD5, SHA-1 ou SHA-256 pour les sommes de contrôle dans les informations de débogage. |
| [`/ZI`](z7-zi-zi-debug-information-format.md) | Inclut des informations de débogage dans une base de données du programme compatible avec Modifier & Continuer. |
| [`/Zi`](z7-zi-zi-debug-information-format.md) | Génère des informations de débogage complètes. |
| [`/Zl`](zl-omit-default-library-name.md) | Supprime le nom de la bibliothèque par défaut dans le fichier .obj (x86 uniquement). |
| [`/Zm`](zm-specify-precompiled-header-memory-allocation-limit.md) | Spécifie la limite d'allocation de mémoire de l'en-tête précompilé. |
| [`/Zo`](zo-enhance-optimized-debugging.md) | Génère des informations de débogage avancées pour le code optimisé. |
| [`/Zp`](zp-struct-member-alignment.md) | Compresse les membres de la structure. |
| [`/Zs`](zs-syntax-check-only.md) | Vérifie la syntaxe uniquement. |
| [`/ZW`](zw-windows-runtime-compilation.md) | Produit un fichier de sortie à exécuter sur le Windows Runtime. |

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
