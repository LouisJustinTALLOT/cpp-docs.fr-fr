---
title: Options de l'éditeur de liens
ms.date: 08/20/2018
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 22ac88ede7cc015efd12f1a996ffdf361b43f041
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510110"
---
# <a name="linker-options"></a>Options de l'éditeur de liens

LINK.exe lie des bibliothèques et des fichiers objets COFF (Common Object File Format) pour créer un fichier exécutable (.exe) ou une bibliothèque de liens dynamiques (DLL).

Le tableau ci-dessous répertorie les options pour LINK.exe. Pour plus d’informations sur LINK, consultez :

- [Options LINK contrôlées par le compilateur](../../build/reference/compiler-controlled-link-options.md)

- [Fichiers d’entrée LINK](../../build/reference/link-input-files.md)

- [Sortie LINK](../../build/reference/link-output.md)

- [Mots réservés](../../build/reference/reserved-words.md)

Sur la ligne de commande, les options de l’éditeur de liens ne sont pas la casse ; par exemple, /base et /BASE ont la même signification. Pour plus d'informations sur la façon de spécifier une option quelconque sur la ligne de commande ou dans Visual Studio, consultez la documentation relative à cette option.

Vous pouvez utiliser le pragma [comment](../../preprocessor/comment-c-cpp.md) pour spécifier des options de l'éditeur de liens.

|Option|Objectif|
|------------|-------------|
|[@](../../build/reference/at-specify-a-linker-response-file.md)|Spécifie un fichier réponse.|
|[/ALIGN](../../build/reference/align-section-alignment.md)|Spécifie l’alignement de chaque section.|
|[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|Spécifie qu’une DLL ne peut pas être liée.|
|[/ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|Spécifie un comportement pour la recherche de manifeste.|
|[/APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|Spécifie si l’application doit s’exécuter au sein d’un environnement de processus appcontainer.|
|[/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|Ajoute l’attribut <xref:System.Diagnostics.DebuggableAttribute> à une image managée.|
|[/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|Crée un lien à une ressource managée.|
|[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|Spécifie qu’un module MSIL (Microsoft Intermediate Language) doit être importé dans l’assembly.|
|[/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|Incorpore un fichier de ressources managé dans un assembly.|
|[/BASE](../../build/reference/base-base-address.md)|Définit une adresse de base pour le programme.|
|[/CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|Définit le nombre de threads de cl.exe à utiliser pour l’optimisation et la génération de code quand la génération de code durant l’édition de liens est spécifiée.|
|[/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|Définit le type (IJW, pure ou sécurisée) d’une image CLR.|
|[/CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Préserve le dernier code d’erreur des fonctions qui sont appelées via le mécanisme P/Invoke.|
|[/CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|Spécifie l’attribut de thread à appliquer au point d’entrée de votre programme CLR.|
|[/CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Spécifie si l’éditeur de liens doit appliquer l’attribut SuppressUnmanagedCodeSecurity aux stubs PInvoke générés par l’éditeur de liens qui appellent à partir du code managé dans des DLL natives.|
|[/DEBUG](../../build/reference/debug-generate-debug-info.md)|Crée des informations de débogage.|
|[/DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|Spécifie les données à inclure dans les informations de débogage.|
|[/DEF](../../build/reference/def-specify-module-definition-file.md)|Passe un fichier de définition de module (.def) à l’éditeur de liens.|
|[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|Effectue une recherche dans la bibliothèque spécifiée quand des références externes sont résolues.|
|[/DELAY](../../build/reference/delay-delay-load-import-settings.md)|Contrôle le chargement différé des DLL.|
|[/DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|Entraîne le chargement différé de la DLL spécifiée.|
|[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|Signe partiellement un assembly.|
|[/ DEPENDENTLOADFLAG](dependentloadflag.md)|Définit les indicateurs par défaut sur les chargements DLL dépendantes.|
|[/DLL](../../build/reference/dll-build-a-dll.md)|Génère une DLL.|
|[/DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|Crée un pilote en mode noyau.|
|[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|Spécifie s’il convient de générer une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement en utilisant la fonctionnalité de randomisation du format d’espace d’adresse (ASLR).|
|[/ENTRY](../../build/reference/entry-entry-point-symbol.md)|Définit l’adresse de départ.|
|[/errorReport](../../build/reference/errorreport-report-internal-linker-errors.md)|Signale les erreurs internes de l’éditeur de liens à Microsoft.|
|[/EXPORT](../../build/reference/export-exports-a-function.md)|Exporte une fonction.|
|[/ /FILEALIGN](../../build/reference/filealign.md)|Alignement des sections dans le fichier de sortie multiples d’une valeur spécifiée.|
|[/FIXED](../../build/reference/fixed-fixed-base-address.md)|Crée un programme qui peut être chargé uniquement à son adresse de base préférée.|
|[/FORCE](../../build/reference/force-force-file-output.md)|Force un lien à se terminer même avec des symboles non résolus ou des symboles définis plusieurs fois.|
|[/FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|Crée une image qui peut être corrigée en mémoire.|
|[/ GENPROFILE, /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Ces deux options spécifient la génération d’un fichier .pgd par l’éditeur de liens pour prendre en charge l’optimisation guidée par profil. /GENPROFILE et /FASTGENPROFILE utilisent des paramètres par défaut différents.|
|[/GUARD](../../build/reference/guard-enable-guard-checks.md)|Active la protection du flux de contrôle.|
|[/HEAP](../../build/reference/heap-set-heap-size.md)|Définit la taille du tas, en octets.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|Spécifie la prise en charge de la fonctionnalité de randomisation du format d’espace d’adresse (ASLR) 64 bits de forte entropie.|
|[/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|Spécifie le nom du fichier .idl et d’autres fichiers de sortie MIDL.|
|[/IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|Supprime la sortie des avertissements spécifiés de l’éditeur de liens.|
|[/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|Empêche le traitement des informations d’attribut en un fichier .idl.|
|[/IMPLIB](../../build/reference/implib-name-import-library.md)|Remplace le nom par défaut de la bibliothèque d’importation.|
|[/INCLUDE](../../build/reference/include-force-symbol-references.md)|Force les références de symboles.|
|[/INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|Contrôle l’édition de liens incrémentiels.|
|[/INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|Spécifie que le module requiert une vérification de signature au moment du chargement.|
|[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Spécifie un conteneur de clé pour signer un assembly.|
|[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Spécifie une clé ou une paire de clés pour signer un assembly.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|Indique au compilateur que l’application prend en charge les adresses supérieures à deux giga-octets|
|[/LIBPATH](../../build/reference/libpath-additional-libpath.md)|Spécifie un chemin d’accès pour effectuer la recherche avant le chemin d’accès de la bibliothèque d’environnement.|
|[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)|Spécifie la génération du code durant l’édition de liens.|
|[/MACHINE](../../build/reference/machine-specify-target-platform.md)|Spécifie la plateforme cible.|
|[/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|Crée un fichier manifeste côte à côte et l’incorpore éventuellement dans le fichier binaire.|
|[/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|Spécifie un \<dependentAssembly > section dans le fichier manifeste.|
|[/MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|Modifie le nom par défaut du fichier manifeste.|
|[/MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|Spécifie un fichier d’entrée de manifeste pour que l’éditeur de liens le traite et l’incorpore dans le fichier binaire. Vous pouvez utiliser cette option plusieurs fois pour spécifier plusieurs fichiers d’entrée de manifeste.|
|[/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|Spécifie si les informations de contrôle de compte d’utilisateur sont incorporées dans le manifeste du programme.|
|[/MAP](../../build/reference/map-generate-mapfile.md)|Crée un fichier de mappage.|
|[/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|Inclut les informations spécifiées dans le fichier de mappage.|
|[/MERGE](../../build/reference/merge-combine-sections.md)|Combine des sections.|
|[/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|Spécifie les options de ligne de commande MIDL.|
|[/ NATVIS](../../build/reference/natvis-add-natvis-to-pdb.md)|Ajoute des visualiseurs de débogueur à partir d’un fichier Natvis au fichier PDB.|
|[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|Supprime la création d’un assembly .NET Framework.|
|[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|Ignore toutes les bibliothèques par défaut (ou celles spécifiées) quand des références externes sont résolues.|
|[/NOENTRY](../../build/reference/noentry-no-entry-point.md)|Crée une DLL de ressource uniquement.|
|[/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|Supprime la bannière de démarrage.|
|[/NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|Marque un exécutable comme étant vérifié comme compatible avec la fonctionnalité de prévention de l’exécution des données Windows.|
|[/OPT](../../build/reference/opt-optimizations.md)|Contrôle les optimisations LINK.|
|[/ORDER](../../build/reference/order-put-functions-in-order.md)|Place les COMDAT dans l’image dans un ordre prédéterminé.|
|[/OUT](../../build/reference/out-output-file-name.md)|Spécifie le nom du fichier de sortie.|
|[/PDB](../../build/reference/pdb-use-program-database.md)|Crée un fichier de base de données de programme (PDB).|
|[/PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|Utilise un autre emplacement pour enregistrer un fichier PDB.|
|[/PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|Crée un fichier de base de données de programme (PDB) dépourvu de symboles privés.|
|[/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|Spécifie un fichier .pgd pour les optimisations guidées par profil.|
|[/POGOSAFEMODE](../../build/reference/pogosafemode-linker-option.md)|**Obsolète** crée une build instrumentée PGO de thread-safe.|
|[/PROFILE](../../build/reference/profile-performance-tools-profiler.md)|Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances.|
|[/RELEASE](../../build/reference/release-set-the-checksum.md)|Définit la somme de contrôle dans l’en-tête du fichier .exe.|
|[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|Spécifie que l’image contiendra une table de gestionnaires d’exceptions sécurisés.|
|[/SECTION](../../build/reference/section-specify-section-attributes.md)|Remplace les attributs d’une section.|
|[/ SOURCELINK](../../build/reference/sourcelink.md)|Spécifie un fichier SourceLink à ajouter au fichier PDB.|
|[/STACK](../../build/reference/stack-stack-allocations.md)|Définit la taille de la pile, en octets.|
|[/STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|Attache un programme stub MS-DOS à un programme Win32.|
|[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|Indique au système d’exploitation comment exécuter le fichier .exe.|
|[/SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|Indique au système d’exploitation de copier la sortie de l’éditeur de liens dans un fichier d’échange avant de l’exécuter.|
|[/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|Spécifie l’ID de ressource de la bibliothèque de types générée par l’éditeur de liens.|
|[/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|Spécifie le nom du fichier .tlb et d’autres fichiers de sortie MIDL.|
|[/TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|Crée une application conçue spécifiquement pour s’exécuter sous Terminal Server.|
|[/USEPROFILE](../../build/reference/useprofile.md)|Données d’apprentissage utilise guidée par profil optimisation pour créer une image optimisée.|
|[/VERBOSE](../../build/reference/verbose-print-progress-messages.md)|Imprime les messages de progression de l’éditeur de liens.|
|[/VERSION](../../build/reference/version-version-information.md)|Affecte un numéro de version.|
|[/ WHOLEARCHIVE](../../build/reference/wholearchive-include-all-library-object-files.md)|Inclut tous les fichiers objet à partir de bibliothèques statiques spécifiés.|
|[/WINMD](../../build/reference/winmd-generate-windows-metadata.md)|Active la génération d’un fichier de métadonnées Windows Runtime.|
|[/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|Spécifie le nom du fichier de sortie des métadonnées Windows Runtime (winmd) qui est généré par l’option [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) de l’éditeur de liens.|
|[/WINMDKEYFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|Spécifie une clé ou une paire de clés pour signer un fichier de métadonnées Windows Runtime.|
|[/WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|Spécifie un conteneur de clé pour signer un fichier de métadonnées Windows.|
|[/WINMDDELAYSIGN](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|Signe partiellement un fichier de métadonnées Windows Runtime (.winmd) en plaçant la clé publique dans le fichier winmd.|
|[/WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|Traite les avertissements de l’éditeur de liens en tant qu’erreurs.|

Pour plus d’informations, consultez [Compiler-Controlled LINK Options](../../build/reference/compiler-controlled-link-options.md).

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)