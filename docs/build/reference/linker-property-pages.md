---
title: pages de propriétés de l'Éditeur de liens
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336588"
---
# <a name="linker-property-pages"></a>pages de propriétés de l'Éditeur de liens

Les propriétés suivantes se trouvent dans **le cadre de Project** > **Properties** > **Configuration Properties** > **Linker**. Pour plus d’informations sur le lien, voir [CL Invokes the Linker](cl-invokes-the-linker.md) et [Linker Options](linker-options.md).

## <a name="general-property-page"></a>Page de propriétés Général

### <a name="output-file"></a>Fichier de sortie

[L’option /OUT](out-output-file-name.md) remplace le nom par défaut et l’emplacement du programme que le lien crée.

### <a name="show-progress"></a>Afficher la progression

Imprime des messages de progrès Linker

**Choix**

- **Pas réglé** - Pas de verbosité.
- **Afficher tous les messages de progrès** - Affiche tous les messages de progression.
- **Pour les bibliothèques recherchées** - Affiche des messages de progression indiquant seulement les bibliothèques recherchées.
- **A propos de comDAT pliage lors d’une liaison optimisée** - Affiche des informations sur le pliage COMDAT lors d’une liaison optimisée.
- **À propos des données supprimées lors d’une liaison optimisée** - Affiche des informations sur les fonctions et les données supprimées lors d’une liaison optimisée.
- **À propos de Modules incompatibles avec SEH** - Affiche des informations sur les modules incompatibles avec la manipulation d’exception sécuritaire.
- **À propos de l’activité linker liée au code géré** - Afficher des informations sur l’activité des liaisons liées au code géré.

### <a name="version"></a>Version

[L’option /VERSION](version-version-information.md) indique au linker de mettre un numéro de version dans l’en-tête du fichier .exe ou .dll. Utilisez DUMPBIN /HEADERS pour voir le champ de version image de l’OPTIONAL HEADER VALUES pour voir l’effet de **/VERSION**.

### <a name="enable-incremental-linking"></a>Activation des liens incrémentiels

Permet une liaison incrémentale. ([/INCRÉMENTAL](incremental-link-incrementally.md), /INCRÉMENTAL:NON)

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

[L’option /NOLOGO](nologo-suppress-startup-banner-linker.md) empêche l’affichage du message et du numéro de version du droit d’auteur.

### <a name="ignore-import-library"></a>Bibliothèque d’importation ignorée

Cette propriété indique à l’éditeur de liens ne pas lier de sortie .lib générée à partir de cette build dans n’importe quel projet dépendant. Il permet au système de projet de traiter les fichiers .dll qui ne produisent pas un fichier .lib lorsqu’il est construit. Si un projet dépend d’un autre projet créant une DLL, le système de projet lie automatiquement le fichier .lib produit par ce projet enfant. Cette propriété peut être inutile dans les projets qui produisent des DLL COM ou des DLL sans ressources, parce que ces DLL n’ont pas d’exportations significatives. Si un DLL n’a pas d’exportations, le lien ne génère pas de fichier .lib. Si aucun fichier export .lib n’est présent, et que le système de projet indique au linker de lier avec le DLL manquant, le lien échoue. Utilisez la propriété **Bibliothèque d’importation ignorée** pour résoudre ce problème. Lorsqu’il est réglé sur **Oui,** le système de projet ignore la présence ou l’absence du fichier .lib, et fait tout projet qui dépend de ce projet de ne pas lien avec le fichier .lib inexistant.

Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Inscription de la sortie

Exécute `regsvr32.exe /s $(TargetPath)` sur la sortie de génération, qui est valide uniquement sur les projets .dll. Pour les projets .exe, cette propriété est ignorée. Pour inscrire un fichier de sortie .exe, définissez un événement post-build dans la configuration afin d’effectuer l’inscription personnalisée obligatoire pour les fichiers .exe inscrits.

Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirection par utilisateur

L’inscription dans Visual Studio s’effectue traditionnellement dans HKEY_CLASSES_ROOT (HKCR). Avec Windows Vista et les systèmes d’exploitation ultérieurs, vous devez exécuter Visual Studio en mode élevé pour accéder à HKCR. Les développeurs ne veulent pas toujours fonctionner en mode élevé, mais doivent toujours travailler avec l’enregistrement. La redirection par utilisateur vous permet de vous inscrire sans avoir à courir en mode élevé.

La redirection par utilisateur force toutes les écritures dans HKCR à être redirigées vers HKEY\_CURRENT\_USER (HKCU). Si la redirection par utilisateur est désactivée, [Erreur de génération de projet PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) peut survenir quand le programme essaie d’écrire dans HKCR.

### <a name="additional-library-directories"></a>Répertoires de bibliothèques supplémentaires

Permet à l’utilisateur de substituer le chemin de la bibliothèque d’environnement. ([/LIBPATH](libpath-additional-libpath.md):dossier)

### <a name="link-library-dependencies"></a>Lier les dépendances de la bibliothèque

Indique s’il convient de lier les fichiers .lib produits par les projets dépendants. Typiquement, vous voulez lier dans les fichiers .lib, mais il peut ne pas être le cas pour certains DLLs.

Vous pouvez également spécifier un fichier .obj en fournissant le nom de fichier et le chemin relatif, par exemple « ..\\..\MyLibProject\MyObjFile.obj ». Si le code source pour le fichier .obj #includes un en-tête précompilé, par exemple pch.h, alors le fichier pch.obj est situé dans le même dossier que MyObjFile.obj. Vous devez également ajouter pch.obj comme une dépendance supplémentaire.

### <a name="use-library-dependency-inputs"></a>Utiliser les entrées de dépendance de la bibliothèque

Précise s’il faut utiliser les intrants à l’outil bibliothécaire, plutôt que le fichier de la bibliothèque lui-même, lorsqu’il établit un lien entre les sorties des bibliothèques des dépendances du projet. Dans un grand projet, quand un projet dépendant produit un fichier .lib, la liaison incrémentielle est désactivée. Si de nombreux projets dépendants génèrent des fichiers .lib, la génération de l’application peut prendre un certain temps. Lorsque cette propriété est définie à **Oui**, le système de projet relie dans les fichiers .obj pour .libs produites par des projets dépendants, permettant la liaison progressive.

Pour plus d’informations sur la façon d’accéder à la page de propriété **General** linker, voir [le compilateur Set CMD et construire des propriétés dans Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>État du lien

Précise si le lien doit afficher un indicateur de progression indiquant quel pourcentage du lien est complet. La valeur par défaut est de ne pas afficher ces informations d’état. ([/LTCG](ltcg-link-time-code-generation.md):STATUS LTCG:NOSTATUS)

### <a name="prevent-dll-binding"></a>Empêcher la liaison DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md):NO met un peu dans l’en-tête d’un DLL qui indique à Bind.exe que l’image n’est pas autorisée à être liée. Vous ne voulez peut-être pas qu’une DLL soit liée si elle a été signée numériquement (la liaison invalide la signature).

### <a name="treat-linker-warning-as-errors"></a>Traiter l’avertissement linker comme des erreurs

[/WX](wx-treat-linker-warnings-as-errors.md) ne provoque aucun fichier de sortie à générer si le lien génère un avertissement.

### <a name="force-file-output"></a>Sortie du fichier de force

[L’option /FORCE](force-force-file-output.md) indique au linker de créer un fichier .exe ou DLL même si un symbole est référencé mais non défini, ou se multiplie défini. Il peut créer un fichier .exe invalide.

**Choix**

- **Activé** - /FORCE sans arguments implique à la fois multiple et non résolu.
- **Multipliez le symbole défini uniquement** - Utilisez /FORCE:MULTIPLE pour créer un fichier de sortie, même si LINK trouve plus d’une définition pour un symbole.
- **Symbole indéfini seulement** - Utiliser /FORCE:UNRESOLVED pour créer un fichier de sortie si LINK trouve ou non un symbole indéfini. /FORCE:UNRESOLVED est ignoré si le symbole du point d’entrée n’est pas résolu.

### <a name="create-hot-patchable-image"></a>Créer Hot Patchable Image

Prépare une image pour hotpatching.

**Choix**

- **Activé** - Prépare une image pour hotpatching.
- **X86 Image seulement** - prépare une image X86 pour hotpatching.
- **X64 Image only** - Prépare une image X64 pour hotpatching.
- **Image d’itanium seulement** - prépare une image d’itanium pour le hotpatching.

### <a name="specify-section-attributes"></a>Spécifier les attributs de la section

[L’option /SECTION](section-specify-section-attributes.md) modifie les attributs d’une section, en l’avant des attributs définis lorsque le fichier .obj pour la section a été compilé.

## <a name="input-property-page"></a>Page de propriété d’entrée

### <a name="additional-dependencies"></a>Dépendances supplémentaires

Spécifie des éléments supplémentaires à ajouter à la ligne de commande de lien, par exemple *kernel32.lib*.

### <a name="ignore-all-default-libraries"></a>Ignorer toutes les bibliothèques par défaut

[L’option /NODEFAULTLIB](nodefaultlib-ignore-libraries.md) indique au linker de supprimer une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’il recherche lors de la résolution de références externes.

### <a name="ignore-specific-default-libraries"></a>Bibliothèques par défaut spécifiques ignorées

Spécifie un ou plusieurs noms de bibliothèques par défaut à ignorer. Séparer plusieurs bibliothèques avec des semi-colons. (/NODEFAULTLIB:[nom, nom, ...])

### <a name="module-definition-file"></a>Fichier de définition du module

[L’option /DEF](def-specify-module-definition-file.md) transmet un fichier de définition de module (.def) au linker. Un seul fichier .def peut être spécifié à LINK.

### <a name="add-module-to-assembly"></a>Ajouter le module à l’assemblage

[L’option /ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) vous permet d’ajouter une référence de module à un assemblage. Les informations de type dans le module ne seront pas disponibles pour le programme d’assemblage qui a ajouté la référence du module. Toutefois, des informations de type dans le module seront disponibles pour tout programme qui fait référence à l’assemblage.

### <a name="embed-managed-resource-file"></a>Fichier de ressources gérées embed

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) intègre un fichier de ressources dans le fichier de sortie.

### <a name="force-symbol-references"></a>Références des symboles forcées

[L’option /INCLUDE](include-force-symbol-references.md) indique au linker d’ajouter un symbole spécifié à la table de symbole.

### <a name="delay-loaded-dlls"></a>Retard des DLL chargés

[L’option /DELAYLOAD](delayload-delay-load-import.md) provoque un retard de chargement des DLL. Le nom dll spécifie un DLL pour retarder la charge.

### <a name="assembly-link-resource"></a>Ressources de lien d’assemblage

[L’option /ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) crée un lien vers une ressource cadre .NET dans le fichier de sortie; le fichier de ressources n’est pas placé dans le fichier de sortie.

## <a name="manifest-file-property-page"></a>Page de propriété de fichier manifeste

### <a name="generate-manifest"></a>Générer Manifeste

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md) précise que le lien doit créer un fichier manifeste côte à côte.

### <a name="manifest-file"></a>Fichier Manifeste

[/MANIFESTFILE](manifestfile-name-manifest-file.md) vous permet de modifier le nom par défaut du fichier manifeste. Le nom par défaut du fichier manifeste est le nom du fichier avec .manifeste appendice.

### <a name="additional-manifest-dependencies"></a>Dépendances manifestes supplémentaires

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) vous permet de spécifier les attributs qui seront placés dans la section dépendance du fichier manifeste.

### <a name="allow-isolation"></a>Permettre l’isolement

Spécifie un comportement pour la recherche de manifeste. ([/AUTORISATION :NON)](allowisolation-manifest-lookup.md)

### <a name="enable-user-account-control-uac"></a>Activez le contrôle des comptes utilisateur (UAC)

Précise si le contrôle des comptes utilisateur est activé ou non.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md), /MANIFESTUAC:NON)

### <a name="uac-execution-level"></a>Niveau d’exécution de l’UAC

Spécifie le niveau d’exécution demandé pour l’application lors de l’exécution avec le contrôle du compte utilisateur.  (/MANIFESTUAC:niveau[valeur])

**Choix**

- **asInvoker** - UAC Execution Level: en tant qu’invocateur.
- **plus élevéDisponible** - UAC Niveau d’exécution: le plus élevé disponible.
- **requireAdministrator** - UAC Niveau d’exécution: exiger l’administrateur.

### <a name="uac-bypass-ui-protection"></a>Protection de l’assurance-chômage de contournement de l’UAC

Précise s’il faut contourner ou non les niveaux de protection de l’interface utilisateur pour d’autres fenêtres du bureau.  Définissez cette propriété au «Oui» uniquement pour les applications d’accessibilité.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md):uiAccessMD[vrai faux])

## <a name="debugging-property-page"></a>Page de propriétés de débogage

### <a name="generate-debug-info"></a>Générer Desbug Info

Cette option permet la création d’informations de débogage pour le fichier .exe ou le DLL.

**Choix**

- **Non** - Ne produit aucune information de débogage.
- **Générer des informations Debug** - Créer une base de données complète de programme (PDB) idéale pour la distribution à Microsoft Symbol Server.
- **Générer Des informations Debug optimisées pour des liens plus rapides** - Produit une base de données de programme (PDB) idéale pour le cycle de modification-lien-debug.
- **Générer Debug Informations optimisées pour le partage et la publication** - Produit une base de données de programme (PDB) idéale pour le cycle de modification-lien-debug.

### <a name="generate-program-database-file"></a>Générer un fichier de base de données de programme

Par défaut, lorsque [/DEBUG](debug-generate-debug-info.md) est spécifié, le lien crée une base de données de programme (PDB) qui contient des informations de débogage. Le nom de fichier par défaut pour le PDB a le nom de base du programme et l’extension .pdb.

### <a name="strip-private-symbols"></a>Bandes privées Symboles

[L’option /PDBSTRIPPED](pdbstripped-strip-private-symbols.md) crée un deuxième fichier de base de données de programme (PDB) lorsque vous construisez votre image de programme avec l’une des options de compilateur ou de liaison qui génèrent un fichier PDB (/DEBUG, /Z7, /Zd, ou /Zi).

### <a name="generate-map-file"></a>Générer un fichier de carte

[L’option /MAP](map-generate-mapfile.md) indique au linker de créer un fichier de cartes.

### <a name="map-file-name"></a>Nom de fichier de mappage

Nom spécifié par l’utilisateur pour le mapfile. Il remplace le nom par défaut.

### <a name="map-exports"></a>Exportations de cartes

[L’option /MAPINFO](mapinfo-include-information-in-mapfile.md) indique au linker d’inclure les informations spécifiées dans un fichier cartographique, qui est créé si vous spécifiez l’option /MAP. EXPORTS indique au linker d’inclure les fonctions exportées.

### <a name="debuggable-assembly"></a>Assemblée débbuggable

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) émet l’attribut DebuggableAttribute avec le suivi des informations de débogé et désactive les optimisations JIT.

## <a name="system-property-page"></a>Page de propriété du système

### <a name="subsystem"></a>Sous-système

[L’option /SUBSYSTEM](subsystem-specify-subsystem.md) indique au système d’exploitation comment exécuter le fichier .exe. Le choix du sous-système affecte le symbole du point d’entrée (ou fonction de point d’entrée) que le lien choisira.

**Choix**

- **Non réglé** - Pas de sous-système défini.
- **Console** - Application en mode caractère Win32. Les applications console sont données sur une console par le système d’exploitation. Si le principal ou le wmain est défini, CONSOLE est la valeur par défaut.
- **Windows** - L’application ne nécessite pas de console, probablement parce qu’elle crée ses propres fenêtres pour l’interaction avec l’utilisateur. Si WinMain ou wWinMain est défini, WINDOWS est la valeur par défaut.
- **Native** - Pilotes d’appareils pour Windows NT. Si /DRIVER:WDM est spécifié, NATIVE est la valeur par défaut.
- **Demande EFI** - Demande EFI.
- **EFI Boot Service Driver** - EFI Boot Service Driver.
- **EFI ROM** - EFI ROM.
- **EFI Runtime** - EFI Runtime.
- **POSIX** - Application qui s’exécute avec le sous-système POSIX dans Windows NT.

### <a name="minimum-required-version"></a>Version minimale requise

Spécifier la version minimale requise du sous-système. Les arguments sont des nombres décimaux dans la gamme 0 à 65 535.

### <a name="heap-reserve-size"></a>Taille de réserve de tas

Spécifie la taille totale de l’allocation de tas dans la mémoire virtuelle. Par défaut est de 1 Mo.    ([/HEAP](heap-set-heap-size.md):réserve)

### <a name="heap-commit-size"></a>Taille d’engagement de tas

Spécifie la taille totale de l’allocation de tas dans la mémoire physique. Par défaut est de 4 KB.    ([/HEAP](heap-set-heap-size.md):réserve,commit)

### <a name="stack-reserve-size"></a>Taille de la réserve de pile

Spécifie la taille totale d’allocation de piles dans la mémoire virtuelle. Par défaut est de 1 Mo.     ([/STACK](stack-stack-allocations.md):réserve)

### <a name="stack-commit-size"></a>Taille de validation de pile

Spécifie la taille totale de l’allocation de pile dans la mémoire physique. Par défaut est de 4 KB.     ([/STACK](stack-stack-allocations.md):réserve,commit)

### <a name="enable-large-addresses"></a>Activer les grandes adresses

[L’option /LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) indique au linker que l’application peut traiter des adresses de plus de 2 gigaoctets. Par défaut, /LARGEADDRESSAWARE:NO est activé si /LARGEADDRESSAWARE n’est pas spécifié autrement sur la ligne de liaison.

### <a name="terminal-server"></a>Terminal Server

[L’option /TSAWARE](tsaware-create-terminal-server-aware-application.md) place un drapeau dans le champ IMAGE_OPTIONAL_HEADER DllCharacteristics dans l’en-tête optionnel de l’image du programme. Si cet indicateur est défini, le serveur Terminal Server n’apportera aucune modification à l’application.

### <a name="swap-run-from-cd"></a>Swap Run From CD

[L’option /SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indique au système d’exploitation de copier d’abord la sortie du linker sur un fichier de swap, puis d’exécuter l’image à partir de là. Cette option est une fonctionnalité Windows NT 4.0 (et plus tard). Lorsque **le CD** est spécifié, le système d’exploitation copie l’image sur un disque amovible à un fichier de page, puis le charge.

### <a name="swap-run-from-network"></a>Swap Run From Network

[L’option /SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indique au système d’exploitation de copier d’abord la sortie du linker sur un fichier de swap, puis d’exécuter l’image à partir de là. Cette option est une fonctionnalité Windows NT 4.0 (et plus tard). Si **NET** est spécifié, le système d’exploitation copiera d’abord l’image binaire du réseau à un fichier d’échange et le chargera à partir de là. Cette option est utile pour l’exécution d’applications sur le réseau.

### <a name="driver"></a>Pilote

Utilisez l’option [/DRIVER](driver-windows-nt-kernel-mode-driver.md) linker pour construire un pilote de mode noyau Windows NT.

**Choix**

- **Non défini** - Réglage du conducteur par défaut.
- **Pilote** - Pilote
- **UP Only** - /DRIVER:UPONLY provoque le lien à ajouter le IMAGE_FILE_UP_SYSTEM_ONLY bit aux caractéristiques de l’en-tête de sortie pour spécifier qu’il s’agit d’un pilote uniprocesseur (UP). Le système d’exploitation refusera de charger un pilote UP sur un système multiprocesseur (MP).
- **WDM** - /DRIVER:WDM provoque le linker pour définir le IMAGE_DLLCHARACTERISTICS_WDM_DRIVER bit dans le champ DllCharacteristics de l’en-tête optionnel.

## <a name="optimization-property-page"></a>Page de propriété d’optimisation

### <a name="references"></a>References

[/OPT](opt-optimizations.md):REF élimine les fonctions et/ou les données qui n’ont jamais fait référence tandis que /OPT:NOREF conserve des fonctions et/ou des données qui n’ont jamais fait référence.

### <a name="enable-comdat-folding"></a>Activer le pliage COMDAT

Utilisez [/OPT](opt-optimizations.md):ICF\[-itérations] pour effectuer le pliage IDENTIQUE COMDAT.

### <a name="function-order"></a>Ordre de fonction

[L’option /ORDER](order-put-functions-in-order.md)permet à LINK d’optimiser votre programme en plaçant certains COMDAT dans l’image dans un ordre prédéterminé. LINK place les fonctions dans l’ordre spécifié dans chaque section de l’image.

### <a name="profile-guided-database"></a>Base de données guidée de profil

Spécifier le fichier .pgd pour les optimisations guidées de profil. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Génération de code durant l’édition de liens

Spécifie la génération du code durant l’édition de liens. ([/LTCG](ltcg-link-time-code-generation.md))

**Choix**

- **Défaut** - Paramètre LTCG par défaut.
- **Utilisez Fast Link Time Code Generation** - Utilisez Link Time Code Generation avec [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Utilisez Link Time Code Generation** - Utilisez Link Time Code [Generation](ltcg-link-time-code-generation.md).
- **Optimisation guidée de profil - Instrument** - Utiliser [l’optimisation guidée de profil](../profile-guided-optimizations.md) avec :PGINSTRUMENT.
- **Optimisation guidée de profil - Optimisation** - Specifie que le linker doit utiliser les données de profil créées après avoir exécuté le binaire instrumenté pour créer une image optimisée.
- **Optimisation guidée de profil - Mise à jour** - Permet et suit la liste des fichiers d’entrée à ajouter ou à modifier à partir de ce qui a été spécifié dans la phase :PGINSTRUMENT.

## <a name="embedded-idl-property-page"></a>Page de propriété IDL intégrée

### <a name="midl-commands"></a>Commandements MIDL

Spécifier les options de ligne de commande MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Ignorer L’IDL intégré

[L’option /IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) spécifie que tout attribut IDL dans le code source ne doit pas être traité dans un fichier .idl.

### <a name="merged-idl-base-file-name"></a>Nom de fichier de base IDL fusionné

[L’option /IDLOUT](idlout-name-midl-output-files.md) spécifie le nom et l’extension du fichier .idl.

### <a name="type-library"></a>Bibliothèque de type

[L’option /TLBOUT](tlbout-name-dot-tlb-file.md) spécifie le nom et l’extension du fichier .tlb.

### <a name="typelib-resource-id"></a>Id de ressource TypeLib

Vous permet de spécifier l’ID de ressources de la bibliothèque de type linker générée. ([/TLBID](tlbid-specify-resource-id-for-typelib.md):id)

## <a name="windows-metadata-property-page"></a>Page de propriété de métadonnées de Windows

### <a name="generate-windows-metadata"></a>Générer des métadonnées Windows

Permet ou désactiver la génération de métadonnées Windows.

**Choix**

- **Oui** - Activez la génération de fichiers Windows Metadata.
- **Non** - Désactiver la génération de fichiers Windows Metadata.

### <a name="windows-metadata-file"></a>Fichier Windows Metadata

Le commutateur d’option [/WINMDFILE.](winmdfile-specify-winmd-file.md)

### <a name="windows-metadata-key-file"></a>Fichier clé windows Metadata

Spécifiez une clé ou une paire clé pour signer une métadonnée Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md):nom de fichier)

### <a name="windows-metadata-key-container"></a>Conteneur de clé windows Metadata

Spécifiez un conteneur clé pour signer une métadonnée Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md):nom)

### <a name="windows-metadata-delay-sign"></a>Signe de retard de métadonnées de Windows

Signez partiellement une métadonnée Windows. Utilisez [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) si vous ne souhaitez placer la clé publique que dans les métadonnées Windows. La valeur par défaut est /WINMDDELAYSIGN:NO.

## <a name="advanced-property-page"></a>Page de propriété avancée

### <a name="entry-point"></a>Point d'entrée

[L’option /ENTRY](entry-entry-point-symbol.md) spécifie une fonction de point d’entrée comme adresse de départ pour un fichier .exe ou DLL.

### <a name="no-entry-point"></a>Aucun point d’entrée

[L’option /NOENTRY](noentry-no-entry-point.md)est nécessaire pour créer un DLL sans ressources seulement. Utilisez cette option pour empêcher LINK `_main` de lier une référence à la DLL.

### <a name="set-checksum"></a>Définir Checksum

[L’option /RELEASE](release-set-the-checksum.md) définit le Checksum dans l’en-tête d’un fichier .exe.

### <a name="base-address"></a>Adresse de base

Définit une adresse de base pour le programme. ([/BASE](base-base-address.md):\[adresse,size] @filename,clé)

### <a name="randomized-base-address"></a>Adresse de base randomisée

Adresse de base randomisée. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[:NON))

### <a name="fixed-base-address"></a>Adresse de base fixe

Crée un programme qui peut être chargé uniquement à son adresse de base préférée. ([/FIXE](fixed-fixed-base-address.md)\[:NON))

### <a name="data-execution-prevention-dep"></a>Prévention de l’exécution des données (DEP)

Marque un exécutable comme ayant été testé pour être compatible avec Windows Data Execution Prevention fonctionnalité. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[:NON))

### <a name="turn-off-assembly-generation"></a>Désactiver la génération d’assemblage

[L’option /NOASSEMBLY](noassembly-create-a-msil-module.md) indique au linker de créer une image pour le fichier de sortie actuel sans assemblage cadre .NET.

### <a name="unload-delay-loaded-dll"></a>Déchargement de retard chargé DLL

Le qualificatif **UNLOAD** indique la fonction d’aide à la charge de retard pour soutenir le déchargement explicite de la DLL. ([/RETARD](delay-delay-load-import-settings.md):DÉCHARGEMENT)

### <a name="nobind-delay-loaded-dll"></a>Nobind retard chargé DLL

Le qualificatif **NOBIND** indique au linker de ne pas inclure un IAT liant dans l’image finale. L'option par défaut consiste à créer la table IAT pouvant être liée pour les DLL chargées en différé. ([/RETARD](delay-delay-load-import-settings.md):NOBIND)

### <a name="import-library"></a>Bibliothèque d'importation

Remplace le nom par défaut de la bibliothèque d’importation. ([/IMPLIB](implib-name-import-library.md):nom de fichier)

### <a name="merge-sections"></a>Sections de fusion

[L’option /MERGE](merge-combine-sections.md) combine la première section (à partir de) avec la deuxième section (à), nommant la section résultante à. Par exemple, /merge:.rdata.texte.

### <a name="target-machine"></a>Machine cible

[L’option /MACHINE](machine-specify-target-platform.md) spécifie la plate-forme cible du programme.

**Choix**

- **Non réglé**
- **MachineARM**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Profil

Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances. Nécessite que l’information de généré (/[/DEBUG](debug-generate-debug-info.md)) soit réglée. ([/ PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Attribut de fil CLR

Spécifier explicitement l’attribut de threading pour le point d’entrée de votre programme CLR.

**Choix**

- **Attribut de threading MTA** - Applique l’attribut MTAThreadAttribute au point d’entrée de votre programme.
- **ATTRIBUT de threading STA** - Applique l’attribut STAThreadAttribute au point d’entrée de votre programme.
- **Attribut de threading par défaut** - Même que ne pas spécifier [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Permet au temps d’exécution de langue commune (CLR) de définir l’attribut de threading par défaut.

### <a name="clr-image-type"></a>Type d’image CLR

Définit le type (IJW, pure ou sécurisée) d’une image CLR.

**Choix**

- **Image de Force IJW**
- **Force Pure IL Image**
- **Force Safe IL Image**
- **Type d’image par défaut**

### <a name="key-file"></a>Fichier de clé

Spécifier la clé ou la paire clé pour signer un assemblage. ([/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md):nom de fichier)

### <a name="key-container"></a>Conteneur clé

Spécifier un conteneur clé pour signer un assemblage. ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md):nom)

### <a name="delay-sign"></a>Signe de retard

Signez partiellement une assemblée. Utilisez [/DELAYSIGN](delaysign-partially-sign-an-assembly.md) si vous ne voulez placer la clé publique dans l’assemblée. La valeur par défaut est /DELAYSIGN:NO.

### <a name="clr-unmanaged-code-check"></a>Vérification de code non mentée CLR

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) précise si le linker appliquera SuppressUnmanagedCodeSecurityAttribute pour relier les appels PInvoke générés par les liaisons à partir du code géré en DLL indigènes.

### <a name="error-reporting"></a>Rapport d'erreurs

Vous permet de signaler les erreurs internes du compilateur (ICE) directement à l'équipe Visual C++.

**Choix**

- **PromptImmediately** - Prompt immédiatement.
- **File d’attente pour la prochaine connexion** - File d’attente pour la connexion suivante.
- **Envoyer un rapport d’erreur** - Envoyer un rapport d’erreur.
- **Aucun rapport d’erreur** - Pas de rapport d’erreur.

### <a name="sectionalignment"></a>SectionAlignment

[L’option /ALIGN](align-section-alignment.md) spécifie l’alignement de chaque section dans l’espace d’adresse linéaire du programme. L’argument du nombre est dans les octets et doit être un pouvoir de deux.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Préserver le code d’erreur du dernier cas pour les appels PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), qui est activé par défaut, préserve le dernier code d’erreur des fonctions appelées via le mécanisme P/Invoke, qui vous permet d’appeler des fonctions indigènes dans DLLS, à partir du code compilé avec /clr.

**Choix**

- **Activé** - Activer CLRSupportLastError.
- **Désactivé** - Désactiver CLRSupportLastError.
- **Système Dlls Only** - Activer CLRSupportLastError pour les dlls système seulement.

### <a name="image-has-safe-exception-handlers"></a>Image a sûr des gestionnaires d’exception

Lorsque [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) est spécifié, le lien ne produira une image que s’il peut également produire une table des gestionnaires d’exception sûrs de l’image. Ce tableau spécifie pour le système d’exploitation qui, selon les gestionnaires d’exception, est valable pour l’image.
