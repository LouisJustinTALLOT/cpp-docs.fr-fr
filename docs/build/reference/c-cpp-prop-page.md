---
title: Propriétés de projet C/C++ (Visual Studio)
description: Guide de référence des propriétés des pages de propriétés du projet Microsoft C/C++ de Visual Studio.
ms.date: 07/08/2020
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: d1ade2959351d6e60b1d80554bbfa34074dda725
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229738"
---
# <a name="cc-property-pages"></a>Pages de propriétés C/C++

Les pages de propriétés suivantes se trouvent sous propriétés du **projet**  >  **Properties**  >  **Propriétés de configuration**  >  **C/C++**:

## <a name="cc-general-properties"></a>Propriétés générales de C/C++

### <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter au chemin include. Si vous ajoutez plusieurs répertoires, séparez-les par des points-virgules. Définit [ `/I` (autres répertoires Include)](i-additional-include-directories.md).

### <a name="additional-using-directories"></a>Répertoires de #using supplémentaires

Spécifie un ou plusieurs répertoires (séparez les noms de répertoires par un point-virgule) à rechercher pour résoudre les noms passés à une directive #using. Définit [`/AI`](ai-specify-metadata-directories.md) .

### <a name="debug-information-format"></a>Format des informations de débogage

Indique le type d'informations de débogage générées par le compilateur.  Cette propriété requiert des paramètres de l’éditeur de liens compatibles. Définit [ `/Z7` , `/Zi` , `/ZI` (format des informations de débogage)](z7-zi-zi-debug-information-format.md).

#### <a name="choices"></a>Choices

- **Aucune** : ne génère aucune information de débogage ; la compilation peut donc être plus rapide.
- **Compatible C7** : sélectionnez le type d’informations de débogage créées pour votre programme et indiquez si ces informations sont conservées dans des fichiers objets (. obj) ou dans une base de données de programme (PDB).
- **Base de données du programme** : produit une base de données de programme (PDB) qui contient des informations de type et des informations de débogage symboliques à utiliser avec le débogueur. Les informations de débogage symboliques comprennent les noms et les types de variables et de fonctions, ainsi que les numéros de ligne.
- **Base de données du programme pour modifier & continuer** : produit une base de données de programme, comme décrit ci-dessus, dans un format qui prend en charge la fonctionnalité [Modifier & Continuer](/visualstudio/debugger/edit-and-continue) .

### <a name="support-just-my-code-debugging"></a>Prise en charge du débogage Uniquement mon code

Ajoute le code de prise en charge pour l’activation de l' [uniquement mon code](/visualstudio/debugger/just-my-code) le débogage dans cette unité de compilation. Définit [`/JMC`](jmc.md) .

### <a name="common-language-runtime-support"></a>Prise en charge du Common Language RunTime

Utilisez le service Runtime .NET.  Ce commutateur est incompatible avec d’autres commutateurs ; Pour plus d’informations, consultez la documentation relative à la [`/clr`](clr-common-language-runtime-compilation.md) famille de commutateurs.

#### <a name="choices"></a>Choices

- **Aucune prise en charge du Common Language Runtime** -aucune prise en charge du Common Language Runtime
- **Prise en charge du Common Language Runtime** : crée des métadonnées pour votre application qui peuvent être consommées par d’autres applications CLR. Permet également à votre application d’utiliser des types et des données dans les métadonnées d’autres composants CLR.
- **Prise en charge du Common Language Runtime MSIL pur** : produit un fichier de sortie [MSIL](/dotnet/standard/managed-code)uniquement sans code exécutable natif, bien qu’il puisse contenir des types natifs compilés en MSIL.
- **Prise en charge du Common Language Runtime MSIL sécurisé** : produit un fichier de sortie vérifiable uniquement (sans code exécutable natif).

### <a name="consume-windows-runtime-extension"></a>Utiliser l’extension de Windows Runtime

Utiliser les extensions des langages d’exécution Windows. Définit [`/ZW`](zw-windows-runtime-compilation.md) .

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprime l’affichage de la bannière d’authentification lors du démarrage du compilateur et de l’affichage des messages d’information pendant la compilation.

### <a name="warning-level"></a>Niveau d’avertissement

Sélectionnez la rigueur avec laquelle le compilateur doit traiter les erreurs de code. Définit [`/W0` - `/W4`](compiler-option-warning-level.md) .

#### <a name="choices"></a>Choices

- **Désactiver tous les avertissements** -le niveau 0 désactive tous les avertissements.
- Niveau 1 de **niveau1** affiche les avertissements graves. Le niveau 1 est le niveau d’avertissement par défaut sur la ligne de commande.
- Niveau 2 : affiche tous les avertissements de niveau 1 et les avertissements moins graves **que le niveau** 1.
- **Niveau3** -Level 3 affiche tous les avertissements de niveau 2 et tous les autres avertissements recommandés à des fins de production.
- **Level4** -Level 4 affiche tous les avertissements de niveau 3, ainsi que les avertissements d’information, qui, dans la plupart des cas, peuvent être ignorés en toute sécurité.
- **Activer** : active tous les avertissements, y compris ceux qui sont désactivés par défaut.

### <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Traite les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il peut être préférable de [`/WX`](wx-treat-linker-warnings-as-errors.md) l’utiliser dans chaque compilation. Résolvez tous les avertissements pour réduire les erreurs de code difficiles à trouver.

### <a name="warning-version"></a>Version de l’avertissement

Masquer les avertissements introduits après une version spécifique du compilateur. Définit [`/Wv:xx`\[`.yy`\[`.zzzzz`\]\]](wx-treat-linker-warnings-as-errors.md) .

### <a name="diagnostics-format"></a>Format des diagnostics

Active les diagnostics riches, avec les informations de colonne et le contexte source dans les messages de diagnostic.

#### <a name="choices"></a>Choices

- **Signe insertion** -fournit des informations sur les colonnes dans le message de diagnostic. Et affiche la ligne de code source appropriée avec un signe insertion qui indique la colonne incriminée.
- **Informations sur la colonne** : fournit également le numéro de colonne dans la ligne où le diagnostic est émis, le cas échéant.
- **Classic** : génère uniquement les messages de diagnostic antérieurs et concis avec le numéro de ligne.

### <a name="sdl-checks"></a>Vérifications SDL

Contrôles recommandés SDL (Security Development Lifecycle) supplémentaires ; comprend l’activation de fonctionnalités de génération de code sécurisé supplémentaires et permet d’obtenir des avertissements de sécurité supplémentaires comme des erreurs. Définit [ `/sdl` , `/sdl-` ](sdl-enable-additional-security-checks.md).

### <a name="multi-processor-compilation"></a>Compilation multiprocesseur

Compilation multiprocesseur.

## <a name="cc-optimization-properties"></a>Propriétés d’optimisation C/C++

### <a name="optimization"></a>Optimization

Sélectionnez l’option d’optimisation du code ; Choisissez personnalisé pour utiliser des options d’optimisation spécifiques. Définit [/OD](od-disable-debug.md), [/O1,/O2](o-options-optimize-code.md).

#### <a name="choices"></a>Choices

- **Personnalisé** : optimisation personnalisée.
- **Désactivé** : désactive l’optimisation.
- **Optimisation maximale (privilégier la taille)** -équivalent à**`/Os /Oy /Ob2 /Gs /GF /Gy`**
- **Optimisation maximale (privilégier la vitesse)** -équivalent à**`/Oi /Ot /Oy /Ob2 /Gs /GF /Gy`**
- **Optimisations (favoriser la vitesse)** -équivalent à**`/Oi /Ot /Oy /Ob2`**

### <a name="inline-function-expansion"></a>Expansion des fonctions inline

Sélectionnez le niveau d’expansion des [fonctions inline](../../cpp/inline-functions-cpp.md) pour la Build. Définit [`/Ob`](ob-inline-function-expansion.md) .

#### <a name="choices"></a>Choices

- **Par défaut**
- **Disabled** : désactive l’expansion Inline, qui est activée par défaut.
- **Uniquement __inline** -développe uniquement les fonctions marquées comme **`inline`** , **`__forceinline`** ou **`__inline`** . Ou, dans une fonction membre C++, définie dans une déclaration de classe.
- **Toutes les fonctions appropriées** , qui sont marquées comme **`inline`** ou **`__inline`** et toute autre fonction choisie par le compilateur. (L’expansion se produit à la discrétion du compilateur, souvent appelée *auto-inline*.)

### <a name="enable-intrinsic-functions"></a>Activer les fonctions intrinsèques

Active les fonctions intrinsèques.  L’utilisation de fonctions intrinsèques génère un code plus rapide, mais éventuellement plus volumineux. Définit [`/Oi`](oi-generate-intrinsic-functions.md) .

### <a name="favor-size-or-speed"></a>Privilégier la taille ou la vitesse

S’il faut favoriser la taille du code ou la vitesse du code ; L’optimisation globale doit être activée. Définit [ `/Ot` , `/Os` ](os-ot-favor-small-code-favor-fast-code.md).

#### <a name="choices"></a>Choices

- **Privilégiez le petit** code en privilégiant le code. Réduit la taille des fichiers exe et des dll en demandant au compilateur de privilégier la taille par rapport à la vitesse.
- **Privilégiez** le code rapide en privilégiant le code. Optimise la vitesse des fichiers exe et des dll en demandant au compilateur de privilégier la vitesse par rapport à la taille. (Il s’agit de la valeur par défaut.)
- **Aucune optimisation de taille** et de vitesse.

### <a name="omit-frame-pointers"></a>Omettre les pointeurs de frame

Empêche la création des pointeurs de frame sur la pile des appels.

### <a name="enable-fiber-safe-optimizations"></a>Activer les optimisations à fibres sécurisées

Active l’optimisation de l’espace mémoire lors de l’utilisation des fibres et l’accès au stockage local des threads. Définit [`/GT`](gt-support-fiber-safe-thread-local-storage.md) .

### <a name="whole-program-optimization"></a>Optimisation de l'ensemble du programme

Active les optimisations intermodules en différant la génération du code pour qu'elle se produise au moment de la liaison. Requiert l’option de l’éditeur de liens « génération du code durant l’édition de liens ». Définit [`/GL`](gl-whole-program-optimization.md) .

## <a name="cc-preprocessor-properties"></a>Propriétés du préprocesseur C/C++

### <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Définit les symboles de prétraitement pour votre fichier source.

### <a name="undefine-preprocessor-definitions"></a>Annuler la définition de définitions de préprocesseur

Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur. Définit [`/U`](u-u-undefine-symbols.md) .

### <a name="undefine-all-preprocessor-definitions"></a>Annulation de la définition de toutes les définitions du préprocesseur

Annule la définition de toutes les valeurs de préprocesseur précédemment définies. Définit [`/u`](u-u-undefine-symbols.md) .

### <a name="ignore-standard-include-paths"></a>Ignorer les chemins d’accès Include standard

Empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement INCLUDe.

### <a name="preprocess-to-a-file"></a>Prétraiter dans un fichier

Prétraite les fichiers sources C et C++ et écrit la sortie prétraitée dans un fichier. Cette option supprime la compilation et ne produit pas de *`.obj`* fichier.

### <a name="preprocess-suppress-line-numbers"></a>Prétraiter supprimer les numéros de ligne

Prétraiter sans directives #line.

### <a name="keep-comments"></a>Conserver les commentaires

Supprime la bande de commentaires du code source ; requiert la définition d’une des options’prétraitement'. Définit [`/C`](c-preserve-comments-during-preprocessing.md) .

## <a name="cc-code-generation-properties"></a>Propriétés de génération du code C/C++

### <a name="enable-string-pooling"></a>Activer le regroupement de chaînes

Le compilateur ne crée qu’une seule copie en lecture seule de chaînes identiques dans l’image du programme. Il en résulte des programmes plus petits, une optimisation appelée *regroupement de chaînes*. [ `/O1` , `/O2` ](o-options-optimize-code.md)et [`/ZI`](z7-zi-zi-debug-information-format.md) définit automatiquement l' [`/GF`](gf-eliminate-duplicate-strings.md) option.

### <a name="enable-minimal-rebuild"></a>Activer la régénération minimale

Active la régénération minimale, qui détermine s’il faut recompiler les fichiers sources C++ qui incluent des définitions de classe C++ modifiées, stockées dans des fichiers d’en-tête *`.h`* .

### <a name="enable-c-exceptions"></a>Activer les exceptions C++

Spécifie le modèle de gestion des exceptions à utiliser par le compilateur.

#### <a name="choices"></a>Choices

- **Oui avec les exceptions SEH** : modèle de gestion des exceptions qui intercepte les exceptions asynchrones (structurées) et synchrones (C++). Définit [`/EHa`](eh-exception-handling-model.md) .
- **Oui** : modèle de gestion des exceptions qui intercepte uniquement les exceptions c++ et indique au compilateur de supposer que les fonctions C extern ne lèvent jamais d’exception c++. Définit [`/EHsc`](eh-exception-handling-model.md) .
- **Oui avec les fonctions C extern** : le modèle de gestion des exceptions qui intercepte uniquement les exceptions C++ et indique au compilateur de supposer que les fonctions C extern lèvent une exception. Définit [`/EHs`](eh-exception-handling-model.md) .
- **Sans** aucune gestion des exceptions.

### <a name="smaller-type-check"></a>Contrôle de type plus petit

Activez la vérification de la conversion en types plus petits, incompatibles avec un type d’optimisation autre que Debug. Définit [`/RTCc`](rtc-run-time-error-checks.md) .

### <a name="basic-runtime-checks"></a>Vérifications de base du Runtime

Activez les vérifications des erreurs d’exécution de base, incompatibles avec un type d’optimisation autre que Debug. Définit [ `/RTCs` , `/RTCu` , `/RTC1` ](rtc-run-time-error-checks.md).

#### <a name="choices"></a>Choices

- **Frames de pile** -active la vérification des erreurs au moment de l’exécution du frame de pile.
- **Variables non initialisées** : signale quand une variable est utilisée sans avoir été initialisée.
- **Both (/RTC1, EQUIV. to/RTCsu)** -équivalent de/RTCsu.
- **Default** : vérifications de l’exécution par défaut.

### <a name="runtime-library"></a>Bibliothèque Runtime

Spécifiez la bibliothèque Runtime pour la liaison. Définit [ `/MT` , `/MTd` , `/MD` , `/MDd` ](md-mt-ld-use-run-time-library.md).

#### <a name="choices"></a>Choices

- **Multithread-fait** en sorte que votre application utilise la version statique multithread de la bibliothèque Runtime.
- **Débogage multithread** -Définit _DEBUG et _MT. Cette option indique également au compilateur de placer le nom de bibliothèque *LIBCMTD. lib* dans le *`.obj`* fichier afin que l’éditeur de liens utilise *LIBCMTD. lib* pour résoudre les symboles externes.
- **Dll** multithread-fait en sorte que votre application utilise la version multithread propre à la dll de la bibliothèque Runtime. Définit _MT et _DLL et indique au compilateur de placer le nom de la bibliothèque *Msvcrt. lib* dans le *`.obj`* fichier.
- **Dll de débogage** multithread-Définit _DEBUG, _MT et _DLL et fait en sorte que votre application utilise la version de débogage multithread et la dll de la bibliothèque Runtime. Il indique également au compilateur de placer le nom de la bibliothèque *msvcrtd. lib* dans le *`.obj`* fichier.

### <a name="struct-member-alignment"></a>Alignement des membres de la structure

Spécifie des limites de 1, 2, 4 ou 8 octets pour l’alignement des membres de la structure. Définit [`/Zp`](zp-struct-member-alignment.md) .

#### <a name="choices"></a>Choices

- des structures de paquets de **1 octets** sur des limites de 1 octet. Identique à **`/Zp`** .
- **2 octets** : compresse les structures sur des limites de 2 octets.
- **4 octets** : compresse les structures sur des limites de 4 octets.
- **8 octets** : compresse les structures sur des limites de 8 octets (par défaut).
- **16 octets** : compresse les structures sur des limites de 16 octets.
- Valeurs **par** défaut-paramètres d’alignement par défaut.

### <a name="security-check"></a>Vérification de la sécurité

La vérification de la sécurité permet de détecter les saturations de mémoire tampon de pile, une tentative courante d’attaque contre la sécurité d’un programme.

#### <a name="choices"></a>Choices

- **Désactiver la vérification de la sécurité** : désactivez la vérification de la sécurité. Définit [`/GS-`](gs-buffer-security-check.md) .
- **Activer la vérification de la sécurité** : activez la vérification de la sécurité. Définit [`/GS`](gs-buffer-security-check.md) .

### <a name="control-flow-guard"></a>Control Flow Guard

La vérification de la sécurité de Guard permet de détecter les tentatives de distribution vers un bloc de code illégal.

#### <a name="choices"></a>Choices

- **Oui** -activer la vérification de la sécurité avec les ensembles de garde [`/guard:cf`](guard-enable-control-flow-guard.md) .
- **Non**

### <a name="enable-function-level-linking"></a>Activer la liaison au niveau des fonctions

Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs). Requis avec l’option Modifier et Continuer. Définit [/Gy](gy-enable-function-level-linking.md).

### <a name="enable-parallel-code-generation"></a>Activer la génération de code parallèle

Permet au compilateur de générer du code parallèle pour les boucles identifiées à l’aide de `#pragma loop(hint_parallel[(n)])` lorsque l’optimisation est activée.

### <a name="enable-enhanced-instruction-set"></a>Activer le jeu d’instructions amélioré

Activez l’utilisation des instructions disponibles sur les processeurs qui prennent en charge les jeux d’instructions améliorés. Par exemple, les améliorations de SSE, SSE2, AVX et AVX2 apportées à IA-32. Et, les améliorations AVX et AVX2 pour x64. Actuellement **`/arch:SSE`** et **`/arch:SSE2`** sont disponibles uniquement lors de la création de pour l’architecture x86. Si aucune option n’est spécifiée, le compilateur utilise les instructions trouvées sur les processeurs qui prennent en charge SSE2. L’utilisation d’instructions améliorées peut être désactivée avec **`/arch:IA32`** . Pour plus d’informations, [`/arch (x86)`](arch-x86.md) consultez [`/arch (x64)`](arch-x64.md) et [`/arch (ARM)`](arch-arm.md) .

#### <a name="choices"></a>Choices

- **Extensions streaming SIMD** : extensions streaming SIMD. Paramétr**`/arch:SSE`**
- **Streaming SIMD Extensions 2** -extension streaming SIMD 2. Paramétr**`/arch:SSE2`**
- **Advanced Vector Extensions** : Advanced Vector Extensions. Paramétr**`/arch:AVX`**
- **Advanced Vector Extensions 2** : Advanced Vector Extensions 2. Paramétr**`/arch:AVX2`**
- **Aucune instruction améliorée** -aucune instruction améliorée. Paramétr**`/arch:IA32`**
- **Non défini** -non défini.

### <a name="floating-point-model"></a>Modèle à virgule flottante

Définit le modèle de virgule flottante. Définit [ `/fp:precise` , `/fp:strict` , `/fp:fast` ](fp-specify-floating-point-behavior.md).

#### <a name="choices"></a>Choices

- **Précision** : valeur par défaut. Améliore la cohérence des tests à virgule flottante pour l’égalité et l’inégalité.
- **Strict** : modèle à virgule flottante le plus strict. **`/fp:strict`** provoque l' **`fp_contract`** arrêt et la désactivation **`fenv_access`** . **`/fp:except`** est implicite et peut être désactivée en spécifiant explicitement **`/fp:except-`** . En cas d’utilisation avec **`/fp:except-`** , **`/fp:strict`** applique une sémantique à virgule flottante stricte, mais sans respecter les événements exceptionnels.
- **Fast** -crée le code le plus rapide dans la majorité des cas.

### <a name="enable-floating-point-exceptions"></a>Activer les exceptions à virgule flottante

Modèle de virgule flottante fiable. Les exceptions seront déclenchées immédiatement après leur déclenchement. Définit [/FP : except](fp-specify-floating-point-behavior.md).

### <a name="create-hotpatchable-image"></a>Créer une image corrigeable en mémoire

Lorsque la mise à jour à chaud est activée, le compilateur s’assure que la première instruction de chaque fonction est de deux octets, comme requis pour la mise à jour corrective à chaud. Définit [/hotpatch](hotpatch-create-hotpatchable-image.md).

### <a name="spectre-mitigation"></a>Atténuation de spectre

Spectre les atténuations pour CVE 2017-5753. Définit [`/Qspectre`](qspectre.md) .

#### <a name="choices"></a>Choices

- **Activé** : activer la fonctionnalité d’atténuation de spectre pour CVE 2017-5753
- **Désactivé** : non défini.

## <a name="cc-language-properties"></a>Propriétés du langage C/C++

### <a name="disable-language-extensions"></a>Désactiver les extensions de langage

Supprime ou active les extensions de langage. Définit [`/Za`](za-ze-disable-language-extensions.md) .

### <a name="conformance-mode"></a>Mode de conformité

Active ou supprime le mode de conformité. Définit [`/permissive-`](permissive-standards-conformance.md) .

### <a name="treat-wchar_t-as-built-in-type"></a>Traiter wchar_t comme type intégré

Lorsqu’il est spécifié, le type **`wchar_t`** devient un type natif qui est mappé à **`__wchar_t`** de la même façon que **`short`** **`__int16`** . [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md)est activé par défaut.

### <a name="force-conformance-in-for-loop-scope"></a>Conformité forcée dans la portée de la boucle for

Utilisé pour implémenter le comportement C++ standard pour les boucles for de l’instruction for avec les extensions Microsoft. Définit [ `/Za` `/Ze` (désactive les extensions de langage)](za-ze-disable-language-extensions.md). [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md)est activé par défaut.

### <a name="remove-unreferenced-code-and-data"></a>Supprimer le code et les données non référencés

Lorsqu’il est spécifié, le compilateur ne génère plus d’informations de symbole pour le code et les données non référencés.

### <a name="enforce-type-conversion-rules"></a>Appliquer les règles de conversion de type

Utilisé pour identifier un type de référence rvalue à la suite d’une opération de conversion par la norme C++ 11.

### <a name="enable-run-time-type-information"></a>Activer les informations de type au moment de l’exécution

Ajoute le code permettant de vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution). Définit [ `/GR` , `/GR-` ](gr-enable-run-time-type-information.md).

### <a name="open-mp-support"></a>Prise en charge des PACKs d’ouverture

Active les extensions de langage OpenMP 2,0. Définit [`/openmp`](openmp-enable-openmp-2-0-support.md) .

### <a name="c-language-standard"></a>Norme du langage C++

Détermine la norme du langage C++ que le compilateur active. Utilisez la version la plus récente si possible. Définit [ `/std:c++14` , `/std:c++17` , `/std:c++latest` ](std-specify-language-standard-version.md).

#### <a name="choices"></a>Choices

- **Par défaut**
- **Norme ISO C++ 14**
- **Norme ISO C++ 17**
- **Preview-fonctionnalités de la dernière version de travail C++**

### <a name="enable-c-modules-experimental"></a>Activer les modules C++ (expérimental)

Prise en charge expérimentale des modules TS et des modules de bibliothèque standard C++.

## <a name="cc-precompiled-headers-properties"></a>Propriétés des en-têtes précompilés C/C++

### <a name="createuse-precompiled-header"></a>Créer/utiliser un en-tête précompilé

Active la création ou l’utilisation d’un en-tête précompilé pendant la génération. Définit [`/Yc`](yc-create-precompiled-header-file.md) , [`/Yu`](yu-use-precompiled-header-file.md) .

#### <a name="choices"></a>Choices

- **Créer** : indique au compilateur de créer un fichier d’en-tête précompilé (. pch) qui représente l’état de la compilation à un moment donné.
- **Use** -indique au compilateur d’utiliser un fichier d’en-tête précompilé (. pch) existant dans la compilation actuelle.
- **N’utilise pas les en-têtes précompilés** , sans utiliser les en-têtes précompilés.

### <a name="precompiled-header-file"></a>Fichier d’en-tête précompilé

Spécifie le nom du fichier d’en-tête à utiliser lors de la création ou l’utilisation d’un fichier d’en-tête précompilé. Définit [`/Yc`](yc-create-precompiled-header-file.md) , [`/Yu`](yu-use-precompiled-header-file.md) .

### <a name="precompiled-header-output-file"></a>Fichier d’en-tête précompilé de sortie

Spécifie le chemin d’accès ou le nom du fichier d’en-tête précompilé généré. Définit [`/Fp`](fp-name-dot-pch-file.md) .

## <a name="cc-output-files-properties"></a>Propriétés des fichiers de sortie C/C++

### <a name="expand-attributed-source"></a>Développer la source avec attributs

Crée un fichier listing avec des attributs développés injectés dans le fichier source. Définit [`/Fx`](fx-merge-injected-code.md) .

### <a name="assembler-output"></a>Sortie de l’assembleur

Spécifie le contenu du fichier de sortie linguistique de l’assembly. Définit [ `/FA` , `/FAc` , `/FAs` , `/FAcs` ](fa-fa-listing-file.md).

#### <a name="choices"></a>Choices

- **Aucune liste** -aucune liste.
- **Listing assembleur uniquement** -code assembleur ;*`.asm`*
- **Assembly avec** l’ordinateur de code machine et le code assembleur ;*`.cod`*
- **Assembly avec code source** source et code assembleur ;*`.asm`*
- **Assembly, code machine et** assembly source, code machine et code source ;*`.cod`*

### <a name="use-unicode-for-assembler-listing"></a>Utiliser Unicode pour la liste des assembleurs

Entraîne la création du fichier de sortie au format UTF-8.

### <a name="asm-list-location"></a>Emplacement de la liste ASM

Spécifie le chemin d’accès relatif ou le nom du fichier listing ASM. peut être un nom de fichier ou de répertoire. Définit [`/Fa`](fa-fa-listing-file.md) .

### <a name="object-file-name"></a>Nom de fichier objet

Spécifie un nom de substitution pour le nom de fichier objet par défaut. Il peut s’agir d’un nom de fichier ou de répertoire. Définit [`/Fo`](fo-object-file-name.md) .

### <a name="program-database-file-name"></a>Nom du fichier de base de données du programme

Spécifie un nom pour un fichier PDB généré par le compilateur ; spécifie également le nom de base du fichier IDB requis, généré par le compilateur ; peut être un nom de fichier ou de répertoire. Définit [`/Fd`](fd-program-database-file-name.md) .

### <a name="generate-xml-documentation-files"></a>Générer des fichiers de documentation XML

Spécifie que le compilateur doit générer des fichiers de commentaires de documentation XML (. XDC). Définit [`/doc`](doc-process-documentation-comments-c-cpp.md) .

### <a name="xml-documentation-file-name"></a>Nom du fichier de documentation XML

Spécifie le nom des fichiers de documentation XML générés ; peut être un nom de fichier ou de répertoire. Définit [`/doc:`\<name>](doc-process-documentation-comments-c-cpp.md) .

## <a name="cc-browse-information-properties"></a>Propriétés des informations de navigation C/C++

### <a name="enable-browse-information"></a>Activer les informations de consultation

Spécifie le niveau des informations de consultation dans le *`.bsc`* fichier. Définit [`/FR`](fr-fr-create-dot-sbr-file.md) .

### <a name="browse-information-file"></a>Fichier d’informations de consultation

Spécifie le nom facultatif du fichier d’informations du navigateur. Définit [`/FR`\<name>](fr-fr-create-dot-sbr-file.md) .

## <a name="cc-advanced-properties"></a>Propriétés avancées de C/C++

### <a name="calling-convention"></a>Convention d’appel

Sélectionnez la Convention d’appel par défaut pour votre application (peut être substituée par une fonction). Définit [ `/Gd` , `/Gr` , `/Gz` , `/Gv` ](gd-gr-gv-gz-calling-convention.md).

#### <a name="choices"></a>Choices

- **`__cdecl`**-Spécifie la **`__cdecl`** Convention d’appel pour toutes les fonctions, à l’exception des fonctions membres C++ et des fonctions marquées **`__stdcall`** ou **`__fastcall`** .
- **`__fastcall`**-Spécifie la **`__fastcall`** Convention d’appel pour toutes les fonctions, à l’exception des fonctions membres C++ et des fonctions marquées **`__cdecl`** ou **`__stdcall`** . Toutes les **`__fastcall`** fonctions doivent avoir des prototypes.
- **`__stdcall`**-Spécifie la **`__stdcall`** Convention d’appel pour toutes les fonctions, à l’exception des fonctions membres C++ et des fonctions marquées **`__cdecl`** ou **`__fastcall`** . Toutes les **`__stdcall`** fonctions doivent avoir des prototypes.
- **`__vectorcall`**-Spécifie la **`__vectorcall`** Convention d’appel pour toutes les fonctions, à l’exception des fonctions membres C++ et des fonctions marquées **`__cdecl`** , **`__fastcall`** ou **`__stdcall`** . Toutes les **`__vectorcall`** fonctions doivent avoir des prototypes.

### <a name="compile-as"></a>Compiler en

Sélectionnez l’option langage de compilation pour les *`.c`* *`.cpp`* fichiers et. Définit [ `/TC` , `/TP` ](tc-tp-tc-tp-specify-source-file-type.md).

#### <a name="choices"></a>Choices

- **Par défaut** : option par défaut.
- **Compiler en code C** : compile en code C.
- **Compiler en code c++** -compiler en code c++.

### <a name="disable-specific-warnings"></a>Désactiver des avertissements spécifiques

Désactive les numéros d’avertissement spécifiés. Placez les numéros d’avertissement dans une liste délimitée par des points-virgules. Définit [`/wd`\<number>](compiler-option-warning-level.md) .

### <a name="forced-include-file"></a>Fichier include forcé

un ou plusieurs fichiers Include forcés. Définit [`/FI`\<name>](fi-name-forced-include-file.md) .

### <a name="forced-using-file"></a>Fichier #using forcé

Spécifie un ou plusieurs fichiers #using forcés. Définit [`/FU`\<name>](fu-name-forced-hash-using-file.md) .

### <a name="show-includes"></a>Affichage des fichiers Include

Affiche la liste des fichiers include avec les résultats de la compilation. Définit [`/showIncludes`](showincludes-list-include-files.md) .

### <a name="use-full-paths"></a>Utiliser des chemins d’accès complets

Utilisez des chemins d’accès complets dans les messages de diagnostic. Définit [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) .

### <a name="omit-default-library-name"></a>Omettre le nom de la bibliothèque par défaut

N’inclut pas les noms de bibliothèque par défaut dans les *`.obj`* fichiers. Définit [`/Zl`](zl-omit-default-library-name.md) .

### <a name="internal-compiler-error-reporting"></a>Rapport d’erreurs du compilateur interne

> [!NOTE]
> Cette fonction est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

### <a name="treat-specific-warnings-as-errors"></a>Traiter des avertissements spécifiques comme des erreurs

Traite l’avertissement spécifique du compilateur comme une erreur où n est un avertissement du compilateur.

### <a name="additional-options"></a>Options supplémentaires

Options supplémentaires.
