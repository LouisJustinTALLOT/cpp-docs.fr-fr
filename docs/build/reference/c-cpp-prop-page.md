---
title: C/C++ propriétés du projet (Visual Studio)
ms.date: 07/18/2019
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: 2f7fe025eb69fc1977713c638eef0742074bd9fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927750"
---
# <a name="cc-property-pages"></a>C/C++ pages de propriétés

Les pages de propriétés suivantes se trouvent sous propriétés du **projet** >  > **Propriétés** > de configuration**C/C++** :

## <a name="cc-general-properties"></a>Propriétés CC++ /General

### <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter au chemin include. Si vous ajoutez plusieurs répertoires, séparez-les par des points-virgules. Définit [/i (autres répertoires Include)](i-additional-include-directories.md).

### <a name="additional-using-directories"></a>Répertoires de #using supplémentaires

Spécifie un ou plusieurs répertoires (séparez les noms de répertoires par un point-virgule) à rechercher pour résoudre les noms passés à une directive #using. Définit [/ai](ai-specify-metadata-directories.md).

### <a name="debug-information-format"></a>Format des informations de débogage

Indique le type d'informations de débogage générées par le compilateur.  Cela requiert des paramètres de l’éditeur de liens compatibles. Définit [/Z7,/Zi,/ZI (format des informations de débogage)](z7-zi-zi-debug-information-format.md).

**Choix**

- **Aucune** : ne génère aucune information de débogage ; la compilation peut donc être plus rapide.
- **Compatible C7** : sélectionnez le type d’informations de débogage créées pour votre programme et indiquez si ces informations sont conservées dans des fichiers objets (. obj) ou dans une base de données de programme (PDB).
- **Base de données du programme** : produit une base de données de programme (PDB) qui contient des informations de type et des informations de débogage symboliques à utiliser avec le débogueur. Les informations de débogage symboliques comprennent les noms et types des variables, ainsi que les fonctions et les numéros de ligne.
- **Base de données du programme pour modifier & continuer** : produit une base de données de programme, comme décrit ci-dessus, dans un format qui prend en charge la fonctionnalité [Modifier & Continuer](/visualstudio/debugger/edit-and-continue) .

### <a name="support-just-my-code-debugging"></a>Prise en charge du débogage Uniquement mon code

Ajoute le code de prise en charge pour l’activation de l' [uniquement mon code](/visualstudio/debugger/just-my-code) le débogage dans cette unité de compilation. Définit [/JMC](jmc.md).

### <a name="common-language-runtime-support"></a>Prise en charge du Common Language RunTime

Utilisez le service Runtime .NET.  Ce commutateur est incompatible avec d’autres commutateurs; Pour plus d’informations, consultez la documentation sur la famille de commutateurs [/CLR](clr-common-language-runtime-compilation.md) .

**Choix**

- **Aucune prise en charge du Common Language Runtime** -aucune prise en charge du Common Language Runtime
- **Prise en charge du Common Language Runtime** : crée des métadonnées pour votre application qui peuvent être consommées par d’autres applications CLR, et permet à votre application d’utiliser des types et des données dans les métadonnées d’autres composants CLR.
- **Prise en charge du Common Language Runtime MSIL pur** : produit un fichier de sortie [MSIL](/dotnet/standard/managed-code)uniquement sans code exécutable natif, bien qu’il puisse contenir des types natifs compilés en MSIL.
- **Prise en charge du Common Language Runtime MSIL sécurisé** : produit un fichier de sortie vérifiable uniquement (sans code exécutable natif).

### <a name="consume-windows-runtime-extension"></a>Utiliser l’extension de Windows Runtime

Utiliser les extensions des langages d’exécution Windows. Définit [/ZW](zw-windows-runtime-compilation.md).

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprime l’affichage de la bannière d’authentification lors du démarrage du compilateur et de l’affichage des messages d’information pendant la compilation.

### <a name="warning-level"></a>Niveau d’avertissement

Sélectionnez la rigueur avec laquelle le compilateur doit traiter les erreurs de code. Définit [/W0-/W4](compiler-option-warning-level.md).

**Choix**

- **Désactiver tous les avertissements** -le niveau 0 désactive tous les avertissements.
- Niveau 1 de **niveau1** affiche les avertissements graves. Le niveau 1 est le niveau d’avertissement par défaut sur la ligne de commande.
- Niveau 2: affiche tous les avertissements de niveau 1 et les avertissements moins graves **que le niveau** 1.
- **Niveau3** -Level 3 affiche tous les avertissements de niveau 2 et tous les autres avertissements recommandés à des fins de production.
- **Level4** -Level 4 affiche tous les avertissements de niveau 3, ainsi que les avertissements d’information, qui, dans la plupart des cas, peuvent être ignorés en toute sécurité.
- **Activer tous les avertissements** : active tous les avertissements, dont ceux qui sont désactivés par défaut.

### <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il peut être préférable d’utiliser [/WX](wx-treat-linker-warnings-as-errors.md) dans toutes les compilations. la résolution de tous les avertissements permet de garantir le moins possible d’erreurs de code difficiles à trouver.

### <a name="warning-version"></a>Version de l’avertissement

Masquer les avertissements introduits après une version spécifique du compilateur. Définit [/WV: XX\[. yy\[. zzzzz\]\]](wx-treat-linker-warnings-as-errors.md).

### <a name="diagnostics-format"></a>Format des diagnostics

Active les diagnostics riches, avec les informations de colonne et le contexte source dans les messages de diagnostic.

**Choix**

- **Signe insertion** -fournit des informations sur les colonnes dans le message de diagnostic, ainsi que la ligne appropriée du code source avec un signe insertion indiquant la colonne incriminée.
- **Informations sur la colonne** : fournit également le numéro de colonne dans la ligne où le diagnostic est émis, le cas échéant.
- **Classique** : conserve les messages de diagnostic antérieurs et concis avec le numéro de ligne.

### <a name="sdl-checks"></a>Vérifications SDL

Contrôles recommandés SDL (Security Development Lifecycle) supplémentaires; comprend l’activation de fonctionnalités de génération de code sécurisé supplémentaires et permet d’obtenir des avertissements de sécurité supplémentaires comme des erreurs. Définit [/SDL,/SDL-](sdl-enable-additional-security-checks.md).

### <a name="multi-processor-compilation"></a>Compilation multiprocesseur

Compilation multiprocesseur.

## <a name="cc-optimization-properties"></a>Propriétés deC++ C/Optimization

### <a name="optimization"></a>Optimisation

Sélectionnez l’option d’optimisation du code; Choisissez personnalisé pour utiliser des options d’optimisation spécifiques. Définit [/OD](od-disable-debug.md), [/O1,/O2](o-options-optimize-code.md).

**Choix**

- **Personnalisé** : optimisation personnalisée.
- **Désactivé** : désactive l’optimisation.
- **Optimisation maximale (privilégier la taille)** -équivalent à/og/OS/Oy/OB2/GS/GF/GY
- **Optimisation maximale (privilégier la vitesse)** -équivalent à/og/OI/OT/Oy/OB2/GS/GF/GY
- **Optimisations (favoriser la vitesse)** -équivalent à/og/OI/OT/Oy/OB2

### <a name="inline-function-expansion"></a>Expansion des fonctions inline

Sélectionnez le niveau d’expansion des [fonctions inline](../../cpp/inline-functions-cpp.md) pour la Build. Définit [/Ob1,/OB2](ob-inline-function-expansion.md).

**Choix**

- **Par défaut**
- Disabled: désactive l’expansion Inline, qui est activée par défaut.
- **Uniquement** _ _ Inline-étend uniquement les fonctions marquées comme Inline, _ _ Inline, C++ _ _ forceinline ou _ _ inline ou, dans une fonction membre, définie dans une déclaration de classe.
- **Toutes les fonctions appropriées** qui sont marquées comme inline ou _ _ inline et toute autre fonction choisie par le compilateur (l’expansion se produit à la discrétion du compilateur, souvent appelée auto-inline).

### <a name="enable-intrinsic-functions"></a>Activer les fonctions intrinsèques

Active les fonctions intrinsèques.  L’utilisation de fonctions intrinsèques génère un code plus rapide, mais éventuellement plus volumineux. Définit [/OI](oi-generate-intrinsic-functions.md).

### <a name="favor-size-or-speed"></a>Privilégier la taille ou la vitesse

S’il faut favoriser la taille du code ou la vitesse du code; L’optimisation globale doit être activée. Définit [/OT,/OS](os-ot-favor-small-code-favor-fast-code.md).

**Choix**

- **Privilégiez le petit** code en privilégiant le code. Réduit la taille des fichiers exe et des dll en demandant au compilateur de privilégier la taille par rapport à la vitesse.
- Privilégiez le code rapide en privilégiant le **code** . Optimise la vitesse des fichiers exe et des dll en demandant au compilateur de privilégier la vitesse par rapport à la taille. (Il s’agit de la valeur par défaut.)
- **Ni** aucune taille, ni optimisation de la vitesse.

### <a name="omit-frame-pointers"></a>Omettre les pointeurs de frame

Empêche la création des pointeurs de frame sur la pile des appels.

### <a name="enable-fiber-safe-optimizations"></a>Activer les optimisations à fibres sécurisées

Active l’optimisation de l’espace mémoire lors de l’utilisation des fibres et l’accès au stockage local des threads. Définit [/gt](gt-support-fiber-safe-thread-local-storage.md).

### <a name="whole-program-optimization"></a>Optimisation de l'ensemble du programme

Active les optimisations entre modules en retardant la génération du code au moment de la liaison. requiert que l’option de l’éditeur de liens «génération du code durant l’édition de liens» soit activée. Définit [/GL](gl-whole-program-optimization.md).

## <a name="cc-preprocessor-properties"></a>Propriétés deC++ préprocesseur C/

### <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Définit des symboles de prétraitement pour votre fichier source.

### <a name="undefine-preprocessor-definitions"></a>Annuler la définition de définitions de préprocesseur

Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur. Définit [/u](u-u-undefine-symbols.md).

### <a name="undefine-all-preprocessor-definitions"></a>Annulation de la définition de toutes les définitions du préprocesseur

Annule la définition de toutes les valeurs de préprocesseur précédemment définies. Définit [/u](u-u-undefine-symbols.md).

### <a name="ignore-standard-include-paths"></a>Ignorer les chemins d’accès Include standard

Empêche le compilateur de rechercher des fichiers include dans les répertoires spécifiés dans les variables d’environnement INCLUDe.

### <a name="preprocess-to-a-file"></a>Prétraiter dans un fichier

Prétraite les fichiers C++ sources et C et écrit la sortie prétraitée dans un fichier. Cette option supprime la compilation, donc elle ne produit pas de fichier. obj.

### <a name="preprocess-suppress-line-numbers"></a>Prétraiter supprimer les numéros de ligne

Prétraiter sans directives #line.

### <a name="keep-comments"></a>Conserver les commentaires

Supprime la bande de commentaires du code source; requiert la définition d’une des options’prétraitement'. Définit [/c](c-preserve-comments-during-preprocessing.md).

## <a name="cc-code-generation-properties"></a>C/C++ propriétés de génération de code

### <a name="enable-string-pooling"></a>Activer le regroupement de chaînes

Permet au compilateur de créer une seule copie en lecture seule de chaînes identiques dans l’image de programme et en mémoire pendant l’exécution, ce qui entraîne des programmes plus petits, une optimisation appelée regroupement de chaînes. [/O1,/O2](o-options-optimize-code.md)et [/Zi](z7-zi-zi-debug-information-format.md) définissent automatiquement l’option [/GF](gf-eliminate-duplicate-strings.md) .

### <a name="enable-minimal-rebuild"></a>Activer la régénération minimale

Permet une régénération minimale, qui détermine si les fichiers sources C++ qui incluent des définitions de classe C++ modifiées (stockées dans des fichiers d'en-tête (.h)) doivent être recompilés.

### <a name="enable-c-exceptions"></a>Activer les exceptions C++

Spécifie le modèle de gestion des exceptions à utiliser par le compilateur.

**Choix**

- **Oui avec les exceptions SEH** : modèle de gestion des exceptions qui intercepte les exceptions asynchrones (C++structurées) et synchrones (). Définit [/EHa](eh-exception-handling-model.md).
- **Oui** : modèle de gestion des exceptions qui intercepte C++ uniquement les exceptions et indique au compilateur de supposer que les fonctions C extern C++ ne lèvent jamais d’exception. Définit [/EHsc](eh-exception-handling-model.md).
- **Oui avec les fonctions C extern** : le modèle de gestion des exceptions C++ qui intercepte uniquement les exceptions et indique au compilateur de supposer que les fonctions C extern lèvent une exception. Définit [/EHS](eh-exception-handling-model.md).
- **Sans** aucune gestion des exceptions.

### <a name="smaller-type-check"></a>Contrôle de type plus petit

Activez la vérification de la conversion en types plus petits, incompatibles avec un type d’optimisation autre que Debug. Définit [/RTCc](rtc-run-time-error-checks.md).

### <a name="basic-runtime-checks"></a>Vérifications de base du Runtime

Effectuez des vérifications des erreurs d’exécution de base, incompatibles avec un type d’optimisation autre que Debug. Définit [/RTCs,/RTCu,/RTC1](rtc-run-time-error-checks.md).

**Choix**

- **Frames de pile** -active la vérification des erreurs au moment de l’exécution du frame de pile.
- **Variables** non initialisées: signale quand une variable est utilisée sans avoir été initialisée.
- **Both (/RTC1, EQUIV. to/RTCsu)** -équivalent de/RTCsu.
- **Default** : vérifications de l’exécution par défaut.

### <a name="runtime-library"></a>Bibliothèque Runtime

Spécifiez la bibliothèque Runtime pour la liaison. Définit [/MT,/MTD,/MD,/MDD](md-mt-ld-use-run-time-library.md).

**Choix**

- Multithread **-fait** en sorte que votre application utilise la version statique multithread de la bibliothèque Runtime.
- **Débogage multithread** -définit _ Debug et _ Mt. Cette option indique également au compilateur d'ajouter le nom de bibliothèque LIBCMTD.lib dans le fichier .obj afin que l'Éditeur de liens utilise LIBCMTD.lib pour résoudre les symboles externes.
- **Dll** multithread-fait en sorte que votre application utilise la version multithread propre à la dll de la bibliothèque Runtime. Définit _MT et _DLL, puis indique au compilateur de placer le nom de la bibliothèque MSVCRT.lib dans le fichier .obj.
- **Dll de débogage** multithread-définit _ DEBUG, _ MT et _DLL et fait en sorte que votre application utilise la version de débogage multithread et spécifique à la dll de la bibliothèque Runtime. Le compilateur place également le nom de la bibliothèque MSVCRTD.lib dans le fichier .obj.

### <a name="struct-member-alignment"></a>Alignement des membres de la structure

Spécifie des limites de 1, 2, 4 ou 8 octets pour l’alignement des membres de la structure. Définit [/ZP](zp-struct-member-alignment.md).

**Choix**

- des structures de paquets de **1 octets** sur des limites de 1 octet. Identique à/ZP.
- **2 octets** : compresse les structures sur des limites de 2 octets.
- **quatre** structures de paquets d’octets sur des limites de 4 octets.
- **8 octets** : compresse les structures sur des limites de 8 octets (par défaut).
- **16 octets** : compresse les structures sur des limites de 16 octets.
- Valeurs **par** défaut-paramètres d’alignement par défaut.

### <a name="security-check"></a>Vérification de la sécurité

La vérification de la sécurité permet de détecter les saturations de mémoire tampon de pile, une tentative courante d’attaque contre la sécurité d’un programme. 

**Choix**

- **Désactiver la vérification de la sécurité** : désactivez la vérification de la sécurité. Définit [/GS-](gs-buffer-security-check.md).
- **Activer la vérification de la sécurité** : activez la vérification de la sécurité. Définit [/GS](gs-buffer-security-check.md).

### <a name="control-flow-guard"></a>Protection du workflow de contrôle

La vérification de la sécurité de Guard permet de détecter les tentatives de distribution vers un bloc de code illégal. 

**Choix**

- **Oui** -activer la vérification de la sécurité avec les jeux de protection [/Guard: cf](guard-enable-control-flow-guard.md).
- **Non**

### <a name="enable-function-level-linking"></a>Activer la liaison au niveau des fonctions

Permet au compilateur d’empaqueter des fonctions individuelles sous la forme de fonctions empaquetées (COMDATs). Requis avec l’option Modifier et Continuer. Définit [/Gy](gy-enable-function-level-linking.md).

### <a name="enable-parallel-code-generation"></a>Activer la génération de code parallèle

Permet au compilateur de générer du code parallèle pour les boucles identifiées à l'\[aide de #pragma Loop (hint_parallel (n)]) lorsque l’optimisation est activée.

### <a name="enable-enhanced-instruction-set"></a>Activer le jeu d’instructions amélioré

Activez l’utilisation des instructions disponibles sur les processeurs qui prennent en charge les jeux d’instructions améliorés, par exemple, les améliorations SSE, SSE2, AVX et AVX2 pour IA-32; AVX et AVX2 à x64. Actuellement, **/arch: SSE** et **/arch: SSE2** sont uniquement disponibles lors de la génération pour l’architecture x86. Si aucune option n’est spécifiée, le compilateur utilise les instructions trouvées sur les processeurs qui prennent en charge SSE2. L’utilisation d’instructions améliorées peut être désactivée avec/arch: IA32. Pour plus d’informations, consultez [/Arch (x86)](arch-x86.md), [/Arch (x64)](arch-x64.md) et [/Arch (ARM)](arch-arm.md) .

**Choix**

- **Extensions streaming SIMD** : extensions streaming SIMD. Définit **/arch: SSE**
- **Streaming SIMD Extensions 2** -extension streaming SIMD 2. Définit **/arch: SSE2**
- **Advanced Vector Extensions** : Advanced Vector Extensions. Définit **/arch: AVX**
- **Advanced Vector Extensions 2** : Advanced Vector Extensions 2. Définit **/arch: AVX2**
- **Aucune instruction améliorée** -aucune instruction améliorée. Définit **/arch: ia32**
- **Non défini** -non défini.

### <a name="floating-point-model"></a>Modèle à virgule flottante

Définit le modèle de virgule flottante. Définit [/FP: precise,/FP: strict,/FP: Fast](fp-specify-floating-point-behavior.md).

**Choix**

- **Précision** : valeur par défaut. Améliore la cohérence des tests à virgule flottante pour l’égalité et l’inégalité.
- **Strict** : modèle à virgule flottante le plus strict. /FP : strict fait en sorte que fp_contract soit désactivé et que fenv_access soit activé. /FP: except est implicite et peut être désactivé en spécifiant de manière explicite/FP: except-. En cas d’utilisation avec/FP: Except-,/FP: strict applique une sémantique à virgule flottante stricte, mais sans respect des événements exceptionnels.
- **Fast** -crée le code le plus rapide dans la majorité des cas.

### <a name="enable-floating-point-exceptions"></a>Activer les exceptions à virgule flottante

Modèle de virgule flottante fiable. Des exceptions sont levées dès leur déclenchement.  Définit [/FP: except](fp-specify-floating-point-behavior.md).

### <a name="create-hotpatchable-image"></a>Créer une image corrigeable en mémoire

Lorsque la mise à jour à chaud est activée, le compilateur s’assure que la première instruction de chaque fonction est de deux octets, ce qui est nécessaire pour la mise à jour corrective.  Définit [/hotpatch](hotpatch-create-hotpatchable-image.md).

### <a name="spectre-mitigation"></a>Atténuation de spectre

Spectre les atténuations pour CVE 2017-5753. Définit [/Qspectre](qspectre.md).

**Choix**

- **Activé** : activer la fonctionnalité d’atténuation de spectre pour CVE 2017-5753
- **Désactivé** : non défini.

## <a name="cc-language-properties"></a>Propriétés CC++ /Language

### <a name="disable-language-extensions"></a>Désactiver les extensions de langage

Supprime ou active les extensions de langage. Définit [/za](za-ze-disable-language-extensions.md).

### <a name="conformance-mode"></a>Mode de conformité

Active ou supprime le mode de conformité. Définit [/permissive-](permissive-standards-conformance.md).

### <a name="treat-wchar_t-as-built-in-type"></a>Traitement de WChar_t en tant que type intégré

Lorsqu’il est spécifié, le type wchar_t devient un type natif qui correspond à __wchar_t de la même façon que Short est mappé à __int16. [/Zc : wchar_t](zc-wchar-t-wchar-t-is-native-type.md) est activé par défaut.

### <a name="force-conformance-in-for-loop-scope"></a>Conformité forcée dans la portée de la boucle for

Utilisé pour implémenter C++ le comportement standard pour l’instruction for, les boucles avec les extensions Microsoft. Définit [/za,/Ze (désactiver les extensions de langage](za-ze-disable-language-extensions.md). [/Zc:forScope](zc-forscope-force-conformance-in-for-loop-scope.md) est activé par défaut.

### <a name="remove-unreferenced-code-and-data"></a>Supprimer le code et les données non référencés

Lorsqu’il est spécifié, le compilateur ne génère plus d’informations de symbole pour le code et les données non référencés.

### <a name="enforce-type-conversion-rules"></a>Appliquer les règles de conversion de type

Utilisé pour identifier un type de référence rvalue à la suite d’une opération de conversion conforme à la norme C++ 11.

### <a name="enable-run-time-type-information"></a>Activer les informations de type au moment de l’exécution

Ajoute le code permettant de vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution). Définit [/gr,/GR-](gr-enable-run-time-type-information.md).

### <a name="open-mp-support"></a>Prise en charge des PACKs d’ouverture

Activez les extensions de langage OpenMP 2,0. Définit [/OpenMP](openmp-enable-openmp-2-0-support.md).

### <a name="c-language-standard"></a>Norme du langage C++

Détermine la C++ norme du langage que le compilateur appliquera. Il est recommandé d’utiliser la dernière version si possible. Définit [/std: c++ 14,/std: c++ 17,/std: c + + latest](std-specify-language-standard-version.md).

**Choix**

- **Par défaut**
- **Norme ISO C++ 14**
- **Norme ISO C++ 17**
- **Aperçu-fonctionnalités du dernier C++ brouillon de travail**

### <a name="enable-c-modules-experimental"></a>Activer C++ les modules (expérimental)

Prise en charge expérimentale C++ des modules TS et des modules de bibliothèque standard.

## <a name="cc-precompiled-headers-properties"></a>Propriétés desC++ en-têtes C/précompilés

### <a name="precompiled-header"></a>En-tête précompilé

Créer/utiliser un en-tête précompilé: Active la création ou l’utilisation d’un en-tête précompilé pendant la génération. Définit [/Yc](yc-create-precompiled-header-file.md), [/Yu](yu-use-precompiled-header-file.md).

**Choix**

- **Créer** : indique au compilateur de créer un fichier d’en-tête précompilé (. pch) qui représente l’état de la compilation à un moment donné.
- **Use** -indique au compilateur d’utiliser un fichier d’en-tête précompilé (. pch) existant dans la compilation actuelle.
- **N’utilise pas les en-têtes** précompilés, sans utiliser les en-têtes précompilés.

### <a name="precompiled-header-file"></a>Fichier d’en-tête précompilé

Spécifie le nom du fichier d’en-tête à utiliser lors de la création ou l’utilisation d’un fichier d’en-tête précompilé. Définit [/Yc](yc-create-precompiled-header-file.md), [/Yu]] (Yu-use-Precompiled-Header-File.MD).

### <a name="precompiled-header-output-file"></a>Fichier d’en-tête précompilé de sortie

Spécifie le chemin d’accès et/ou le nom du fichier d’en-tête précompilé généré. Définit [/FP](fp-name-dot-pch-file.md).

## <a name="cc-output-files-properties"></a>Propriétés desC++ fichiers de sortie/C

### <a name="expand-attributed-source"></a>Développer la source avec attributs

Crée un fichier listing avec des attributs développés injectés dans le fichier source. Définit [/FX](fx-merge-injected-code.md).

### <a name="assembler-output"></a>Sortie de l’assembleur

Spécifie le contenu du fichier de sortie linguistique de l’assembly. Définit [/FA,/FAC,/FAS,/FACS](fa-fa-listing-file.md).

**Choix**

- **Aucune liste** -aucune liste.
- **Listing assembleur uniquement** -code assembleur;. asm
- **Assembly avec machine de code machine** et code assembleur;. COD
- **Assembly avec code source** -source et code assembleur;. asm
- **Assembly, code machine et** assembly source, code machine et code source;. COD

### <a name="use-unicode-for-assembler-listing"></a>Utiliser Unicode pour la liste des assembleurs

Entraîne la création du fichier de sortie au format UTF-8.

### <a name="asm-list-location"></a>Emplacement de la liste ASM

Spécifie le chemin d’accès relatif et/ou le nom du fichier listing ASM. peut être un nom de fichier ou de répertoire. Définit [/FA](fa-fa-listing-file.md).

### <a name="object-file-name"></a>Nom de fichier objet

Spécifie un nom de substitution pour le nom de fichier objet par défaut. Il peut s’agir d’un nom de fichier ou de répertoire. Définit [/FO](fo-object-file-name.md).

### <a name="program-database-file-name"></a>Nom du fichier de base de données du programme

Spécifie un nom pour un fichier PDB généré par le compilateur; spécifie également le nom de base du fichier IDB requis, généré par le compilateur; peut être un nom de fichier ou de répertoire. Définit [/FD](fd-program-database-file-name.md).

### <a name="generate-xml-documentation-files"></a>Générer des fichiers de documentation XML

Spécifie que le compilateur doit générer des fichiers de commentaires de documentation XML (. XDC). Définit [/doc](doc-process-documentation-comments-c-cpp.md).

### <a name="xml-documentation-file-name"></a>Nom du fichier de documentation XML

Spécifie le nom des fichiers de documentation XML générés; peut être un nom de fichier ou de répertoire. Définit [/doc:\<name >](doc-process-documentation-comments-c-cpp.md).

## <a name="cc-browse-information-properties"></a>C/C++ parcourir les propriétés des informations

### <a name="enable-browse-information"></a>Activer les informations de consultation

Activer les informations de consultation: Spécifie le niveau des informations de consultation dans le fichier. bsc. Définit [/fr](fr-fr-create-dot-sbr-file.md).

### <a name="browse-information-file"></a>Fichier d’informations de consultation

Parcourir le fichier: Spécifie le nom facultatif du fichier d’informations du navigateur. Définit [le\<nom/fr >](fr-fr-create-dot-sbr-file.md).

## <a name="cc-advanced-properties"></a>Propriétés deC++ C/Advanced

### <a name="calling-convention"></a>Convention d’appel

Sélectionnez la Convention d’appel par défaut pour votre application (peut être substituée par une fonction). Définit [/GD,/GR,/gz,/GV](gd-gr-gv-gz-calling-convention.md).

**Choix**

- **_ _ cdecl** -spécifie la Convention d’appel _ C++ _ cdecl pour toutes les fonctions, sauf les fonctions membres et les fonctions marquées _ _ stdcall ou _ _ fastcall
- **_ _ fastcall** -spécifie la Convention d’appel _ C++ _ fastcall pour toutes les fonctions, sauf les fonctions membres et les fonctions marquées _ _ cdecl ou _ _ StdCall Toutes les fonctions _ _ fastcall doivent avoir des prototypes.
- **_ _ stdcall** : spécifie la Convention d’appel _ C++ _ STDCALL pour toutes les fonctions, sauf les fonctions membres et les fonctions marquées _ _ cdecl ou _ _ fastcall Toutes les fonctions _ _ stdcall doivent avoir des prototypes.
- **__vectorcall** : spécifie la Convention d’appel __vectorcall pour toutes C++ les fonctions, à l’exception des fonctions membres et des fonctions marquées _ _ cdecl, _ _ fastcall ou _ _ StdCall. Toutes les fonctions __vectorcall doivent avoir des prototypes.

### <a name="compile-as"></a>Compiler en

Permet de sélectionner l’option de langage de compilation pour les fichiers .c et .cpp. Définit [/TC,/TP](tc-tp-tc-tp-specify-source-file-type.md).

**Choix**

- **Par défaut** : option par défaut.
- **Compiler en code C** : compile en code C.
- **Compiler en code C++**  : compile en code C++.

### <a name="disable-specific-warnings"></a>Désactiver des avertissements spécifiques

Désactivez les numéros d’avertissement souhaités; Placez les nombres dans une liste délimitée par des points-virgules. Définit [/WD\<num >](compiler-option-warning-level.md).

### <a name="forced-include-file"></a>Fichier include forcé

un ou plusieurs fichiers Include forcés. Définit [/fi\<name >](fi-name-forced-include-file.md).

### <a name="forced-using-file"></a>Fichier #using forcé

Spécifie un ou plusieurs fichiers #using forcés. Définit [l'\<> du nom/Fu](fu-name-forced-hash-using-file.md).

### <a name="show-includes"></a>Affichage des fichiers Include

Affiche la liste des fichiers include avec les résultats de la compilation. Définit [/showIncludes](showincludes-list-include-files.md).

### <a name="use-full-paths"></a>Utiliser des chemins d’accès complets

Utilisez des chemins d’accès complets dans les messages de diagnostic. Définit [/FC](fc-full-path-of-source-code-file-in-diagnostics.md).

### <a name="omit-default-library-name"></a>Omettre le nom de la bibliothèque par défaut

N’incluez pas les noms de bibliothèque par défaut dans les fichiers. obj. Définit [/zl](zl-omit-default-library-name.md).

### <a name="internal-compiler-error-reporting"></a>Rapport d’erreurs du compilateur interne

Spécifie comment les erreurs internes de l’outil doivent être signalées à Microsoft.  La valeur par défaut dans l’IDE est prompt.  La valeur par défaut de la ligne de commande builds est queue. Définit [/errorreport :\[Method]] (errorreport-Report-Internal-Compiler-Errors.MD).

**Choix**

- **Ne pas envoyer** de rapports: les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.
- **Invite immédiatement** : vous invite à envoyer un rapport lorsque vous recevez une erreur interne du compilateur.
- **File d’attente pour la prochaine connexion** : met en file d’attente le rapport d’erreurs. Lorsque vous vous connectez avec des privilèges d’administrateur, une fenêtre contextuelle s’affiche et vous permet de signaler les échecs depuis la dernière connexion (vous n’êtes pas invité à envoyer des rapports pour les défaillances plus d’une fois tous les trois jours). la file d’attente est la valeur par défaut lors de la compilation d’une application sur la ligne de commande.
- **Envoyer automatiquement** : envoie automatiquement les rapports d’erreurs internes du compilateur à Microsoft. Pour activer cette option, vous devez d’abord accepter la stratégie de collecte de données Microsoft% 27s. La première fois que vous spécifiez/errorReport : send sur un ordinateur, un message du compilateur vous renverra vers un site Web qui contient la stratégie de collecte de données Microsoft% 27s.

### <a name="treat-specific-warnings-as-errors"></a>Traiter des avertissements spécifiques comme des erreurs

Traite l’avertissement spécifique du compilateur comme une erreur où n est un avertissement du compilateur.

### <a name="additional-options"></a>Options supplémentaires

Options supplémentaires.
