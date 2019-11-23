---
title: Options de l’éditeur de liens MSVC
description: Liste des options prises en charge par l’éditeur de liens Microsoft LINK.
ms.date: 09/24/2019
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: c7a44be5bb21bf83d621bd57c45713bd01e22cb6
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712700"
---
# <a name="linker-options"></a>Options de l’éditeur de liens

LINK.exe lie des bibliothèques et des fichiers objets COFF (Common Object File Format) pour créer un fichier exécutable (.exe) ou une bibliothèque de liens dynamiques (DLL).

Le tableau ci-dessous répertorie les options pour LINK.exe. Pour plus d’informations sur LINK, consultez :

- [Compiler-Controlled LINK Options](compiler-controlled-link-options.md)

- [Fichiers d’entrée LINK](link-input-files.md)

- [Sortie LINK](link-output.md)

- [Mots réservés](reserved-words.md)

Sur la ligne de commande, les options de l’éditeur de liens ne respectent pas la casse ; par exemple,/base et/BASE signifient la même chose. Pour plus d'informations sur la façon de spécifier une option quelconque sur la ligne de commande ou dans Visual Studio, consultez la documentation relative à cette option.

Vous pouvez utiliser le pragma [comment](../../preprocessor/comment-c-cpp.md) pour spécifier des options de l'éditeur de liens.

## <a name="linker-options-listed-alphabetically"></a>Options de l’éditeur de liens classées par ordre alphabétique

|Option|Objectif|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Spécifie un fichier réponse.|
|[/ALIGN](align-section-alignment.md)|Spécifie l’alignement de chaque section.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Spécifie qu’une DLL ne peut pas être liée.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Spécifie un comportement pour la recherche de manifeste.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Spécifie si l’application doit s’exécuter au sein d’un environnement de processus appcontainer.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Ajoute l’attribut <xref:System.Diagnostics.DebuggableAttribute> à une image managée.|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Crée un lien à une ressource managée.|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Spécifie qu’un module MSIL (Microsoft Intermediate Language) doit être importé dans l’assembly.|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Incorpore un fichier de ressources managé dans un assembly.|
|[/BASE](base-base-address.md)|Définit une adresse de base pour le programme.|
|[/CGTHREADS](cgthreads-compiler-threads.md)|Définit le nombre de threads de cl.exe à utiliser pour l’optimisation et la génération de code quand la génération de code durant l’édition de liens est spécifiée.|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Définit le type (IJW, pure ou sécurisée) d’une image CLR.|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Préserve le dernier code d’erreur des fonctions qui sont appelées via le mécanisme P/Invoke.|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Spécifie l’attribut de thread à appliquer au point d’entrée de votre programme CLR.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Spécifie si l’éditeur de liens doit appliquer l’attribut SuppressUnmanagedCodeSecurity aux stubs PInvoke générés par l’éditeur de liens qui appellent à partir du code managé dans des DLL natives.|
|[/DEBUG](debug-generate-debug-info.md)|Crée des informations de débogage.|
|[/DEBUGTYPE](debugtype-debug-info-options.md)|Spécifie les données à inclure dans les informations de débogage.|
|[/DEF](def-specify-module-definition-file.md)|Passe un fichier de définition de module (.def) à l’éditeur de liens.|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Effectue une recherche dans la bibliothèque spécifiée quand des références externes sont résolues.|
|[/DELAY](delay-delay-load-import-settings.md)|Contrôle le chargement différé des DLL.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Entraîne le chargement différé de la DLL spécifiée.|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Signe partiellement un assembly.|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|Définit des indicateurs par défaut sur les charges de DLL dépendantes.|
|[/DLL](dll-build-a-dll.md)|Génère une DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Crée un pilote en mode noyau.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Spécifie s’il convient de générer une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement en utilisant la fonctionnalité de randomisation du format d’espace d’adresse (ASLR).|
|[/ENTRY](entry-entry-point-symbol.md)|Définit l’adresse de départ.|
|[/errorReport](errorreport-report-internal-linker-errors.md)|Signale les erreurs internes de l’éditeur de liens à Microsoft.|
|[/EXPORT](export-exports-a-function.md)|Exporte une fonction.|
|[/FILEALIGN](filealign.md)|Aligne les sections dans le fichier de sortie sur les multiples d’une valeur spécifiée.|
|[/FIXED](fixed-fixed-base-address.md)|Crée un programme qui peut être chargé uniquement à son adresse de base préférée.|
|[/FORCE](force-force-file-output.md)|Force un lien à se terminer même avec des symboles non résolus ou des symboles définis plusieurs fois.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Crée une image qui peut être corrigée en mémoire.|
|[/ GENPROFILE, /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Ces deux options spécifient la génération d’un fichier .pgd par l’éditeur de liens pour prendre en charge l’optimisation guidée par profil. /GENPROFILE et /FASTGENPROFILE utilisent des paramètres par défaut différents.|
|[/GUARD](guard-enable-guard-checks.md)|Active la protection du flux de contrôle.|
|[/HEAP](heap-set-heap-size.md)|Définit la taille du tas, en octets.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Spécifie la prise en charge de la fonctionnalité de randomisation du format d’espace d’adresse (ASLR) 64 bits de forte entropie.|
|[/IDLOUT](idlout-name-midl-output-files.md)|Spécifie le nom du fichier .idl et d’autres fichiers de sortie MIDL.|
|[/IGNORE](ignore-ignore-specific-warnings.md)|Supprime la sortie des avertissements spécifiés de l’éditeur de liens.|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Empêche le traitement des informations d’attribut en un fichier .idl.|
|[/IMPLIB](implib-name-import-library.md)|Remplace le nom par défaut de la bibliothèque d’importation.|
|[/INCLUDE](include-force-symbol-references.md)|Force les références de symboles.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Contrôle l’édition de liens incrémentiels.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Spécifie que le module requiert une vérification de signature au moment du chargement.|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Spécifie un conteneur de clé pour signer un assembly.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Spécifie une clé ou une paire de clés pour signer un assembly.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Indique au compilateur que l’application prend en charge les adresses supérieures à deux giga-octets|
|[/LIBPATH](libpath-additional-libpath.md)|Spécifie un chemin d’accès pour effectuer la recherche avant le chemin d’accès de la bibliothèque d’environnement.|
|[/LINKREPRO](linkrepro.md)|Spécifie un chemin d’accès pour générer des artefacts de reproduction de lien dans.|
|[/LINKREPROTARGET](linkreprotarget.md)|Génère une reproduction de lien uniquement lors de la génération de la cible spécifiée. <sup>16,1</sup>|
|[/LTCG](ltcg-link-time-code-generation.md)|Spécifie la génération du code durant l’édition de liens.|
|[/MACHINE](machine-specify-target-platform.md)|Spécifie la plateforme cible.|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Crée un fichier manifeste côte à côte et l’incorpore éventuellement dans le fichier binaire.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Spécifie une section de > \<dependentAssembly dans le fichier manifeste.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Modifie le nom par défaut du fichier manifeste.|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Spécifie un fichier d’entrée de manifeste pour que l’éditeur de liens le traite et l’incorpore dans le fichier binaire. Vous pouvez utiliser cette option plusieurs fois pour spécifier plusieurs fichiers d’entrée de manifeste.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Spécifie si les informations de contrôle de compte d’utilisateur sont incorporées dans le manifeste du programme.|
|[/MAP](map-generate-mapfile.md)|Crée un fichier de mappage.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Inclut les informations spécifiées dans le fichier de mappage.|
|[/MERGE](merge-combine-sections.md)|Combine des sections.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Spécifie les options de ligne de commande MIDL.|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|Ajoute des visualiseurs de débogueur à partir d’un fichier Natvis dans le fichier PDB.|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|Supprime la création d’un assembly .NET Framework.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Ignore toutes les bibliothèques par défaut (ou celles spécifiées) quand des références externes sont résolues.|
|[/NOENTRY](noentry-no-entry-point.md)|Crée une DLL de ressource uniquement.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Supprime la bannière de démarrage.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Marque un exécutable comme étant vérifié comme compatible avec la fonctionnalité de prévention de l’exécution des données Windows.|
|[/OPT](opt-optimizations.md)|Contrôle les optimisations LINK.|
|[/ORDER](order-put-functions-in-order.md)|Place les COMDAT dans l’image dans un ordre prédéterminé.|
|[/OUT](out-output-file-name.md)|Spécifie le nom du fichier de sortie.|
|[/PDB](pdb-use-program-database.md)|Crée un fichier de base de données de programme (PDB).|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Utilise un autre emplacement pour enregistrer un fichier PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Crée un fichier de base de données de programme (PDB) dépourvu de symboles privés.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Spécifie un fichier .pgd pour les optimisations guidées par profil.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Obsolète** Crée une build instrumentée PGO thread-safe.|
|[/PROFILE](profile-performance-tools-profiler.md)|Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances.|
|[/RELEASE](release-set-the-checksum.md)|Définit la somme de contrôle dans l’en-tête du fichier .exe.|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Spécifie que l’image contiendra une table de gestionnaires d’exceptions sécurisés.|
|[/SECTION](section-specify-section-attributes.md)|Remplace les attributs d’une section.|
|[/SOURCELINK](sourcelink.md)|Spécifie un fichier SourceLink à ajouter au fichier PDB.|
|[/STACK](stack-stack-allocations.md)|Définit la taille de la pile, en octets.|
|[/STUB](stub-ms-dos-stub-file-name.md)|Attache un programme stub MS-DOS à un programme Win32.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Indique au système d’exploitation comment exécuter le fichier .exe.|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Indique au système d’exploitation de copier la sortie de l’éditeur de liens dans un fichier d’échange avant de l’exécuter.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Spécifie l’ID de ressource de la bibliothèque de types générée par l’éditeur de liens.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Spécifie le nom du fichier .tlb et d’autres fichiers de sortie MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Crée une application conçue spécifiquement pour s’exécuter sous Terminal Server.|
|[/USEPROFILE](useprofile.md)|Utilise les données d’apprentissage de l’optimisation guidée par profil pour créer une image optimisée.|
|[/VERBOSE](verbose-print-progress-messages.md)|Imprime les messages de progression de l’éditeur de liens.|
|[/VERSION](version-version-information.md)|Affecte un numéro de version.|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Comprend tous les fichiers objets des bibliothèques statiques spécifiées.|
|[/WINMD](winmd-generate-windows-metadata.md)|Active la génération d’un fichier de métadonnées Windows Runtime.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Spécifie le nom du fichier de sortie des métadonnées Windows Runtime (winmd) qui est généré par l’option [/WINMD](winmd-generate-windows-metadata.md) de l’éditeur de liens.|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Spécifie une clé ou une paire de clés pour signer un fichier de métadonnées Windows Runtime.|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Spécifie un conteneur de clé pour signer un fichier de métadonnées Windows.|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Signe partiellement un fichier de métadonnées Windows Runtime (.winmd) en plaçant la clé publique dans le fichier winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Traite les avertissements de l’éditeur de liens en tant qu’erreurs.|

<sup>16,1</sup> cette option est disponible à partir de Visual Studio 2019 version 16,1.

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)\
[Informations de référence sur l’éditeur de liens MSVC](linking.md)
