---
description: 'En savoir plus sur : pages de propriétés de l’éditeur de liens'
title: pages de propriétés de l'Éditeur de liens
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 308b5d27eda497f196479b063388c33d1c4eddc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199426"
---
# <a name="linker-property-pages"></a>pages de propriétés de l'Éditeur de liens

Les propriétés suivantes se trouvent sous propriétés du **projet**  >    >  éditeur de liens **Propriétés de configuration**  >  . Pour plus d’informations sur l’éditeur de liens, consultez [CL appelle l’éditeur](cl-invokes-the-linker.md) de liens et les options de l' [éditeur de liens](linker-options.md).

## <a name="general-property-page"></a>Général, page de propriétés

### <a name="output-file"></a>Fichier de sortie

L’option [/out](out-output-file-name.md) substitue le nom et l’emplacement par défaut du programme créé par l’éditeur de liens.

### <a name="show-progress"></a>Afficher la progression

Affiche les messages de progression de l’éditeur de liens

**Choices**

- **Non défini** -pas de commentaires.
- **Afficher tous les messages de progression** -affiche tous les messages d’avancement.
- **Pour les bibliothèques recherchées** , affiche les messages de progression indiquant uniquement les bibliothèques recherchées.
- **À propos du repli COMDAT lors de la liaison optimisée** : affiche des informations sur le repli COMDAT pendant la liaison optimisée.
- **À propos des données supprimées pendant la liaison optimisée** : affiche des informations sur les fonctions et les données supprimées pendant la liaison optimisée.
- **À propos des modules incompatibles avec SEH** -affiche des informations sur les modules incompatibles avec la gestion sécurisée des exceptions.
- **À propos de l’activité de l’éditeur de liens liée au code managé-permet** d’afficher des informations sur l’activité de l’éditeur de liens liée au code managé.

### <a name="version"></a>Version

L’option [/version](version-version-information.md) indique à l’éditeur de liens de placer un numéro de version dans l’en-tête du fichier. exe ou. dll. Utilisez DUMPBIN/HEADERS pour voir le champ version de l’image des valeurs d’en-tête FACULTATIVEs pour voir l’effet de **/version**.

### <a name="enable-incremental-linking"></a>Activation des liens incrémentiels

Active les liens incrémentiels. ([/INCREMENTAL](incremental-link-incrementally.md),/Incremental : no)

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

L’option [/nologo](nologo-suppress-startup-banner-linker.md) empêche l’affichage du message de copyright et du numéro de version.

### <a name="ignore-import-library"></a>Bibliothèque d’importation ignorée

Cette propriété indique à l’éditeur de liens ne pas lier de sortie .lib générée à partir de cette build dans n’importe quel projet dépendant. Elle permet au système de projet de gérer les fichiers. dll qui ne produisent pas de fichier. lib lors de la génération. Si un projet dépend d’un autre projet créant une DLL, le système de projet lie automatiquement le fichier .lib produit par ce projet enfant. Cette propriété peut ne pas être nécessaire dans les projets qui produisent des DLL COM ou des dll de ressources uniquement, car ces dll n’ont aucune exportation significative. Si une DLL n’a pas d’exportation, l’éditeur de liens ne génère pas de fichier. lib. Si aucun fichier. lib d’exportation n’est présent et que le système de projet indique à l’éditeur de liens de créer un lien avec la DLL manquante, le lien échoue. Utilisez la propriété **Bibliothèque d’importation ignorée** pour résoudre ce problème. Lorsque la valeur est **Oui**, le système de projet ignore la présence ou l’absence du fichier. lib, et entraîne l’absence de liaison entre tout projet qui dépend de ce projet et le fichier. lib inexistant.

Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Inscription de la sortie

Exécute `regsvr32.exe /s $(TargetPath)` sur la sortie de génération, qui est valide uniquement sur les projets .dll. Pour les projets .exe, cette propriété est ignorée. Pour inscrire un fichier de sortie .exe, définissez un événement post-build dans la configuration afin d’effectuer l’inscription personnalisée obligatoire pour les fichiers .exe inscrits.

Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirection par utilisateur

L’inscription dans Visual Studio s’effectue traditionnellement dans HKEY_CLASSES_ROOT (HKCR). Avec Windows Vista et les systèmes d’exploitation ultérieurs, vous devez exécuter Visual Studio en mode élevé pour accéder à HKCR. Les développeurs ne veulent pas toujours s’exécuter en mode élevé, mais doivent toujours travailler avec l’inscription. La redirection par utilisateur vous permet de vous inscrire sans avoir à s’exécuter en mode élevé.

La redirection par utilisateur force toutes les écritures dans HKCR à être redirigées vers HKEY\_CURRENT\_USER (HKCU). Si la redirection par utilisateur est désactivée, [Erreur de génération de projet PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) peut survenir quand le programme essaie d’écrire dans HKCR.

### <a name="additional-library-directories"></a>Répertoires de bibliothèques supplémentaires

Permet à l’utilisateur de substituer le chemin de la bibliothèque d’environnement. ([/LIBPATH](libpath-additional-libpath.md): Folder)

### <a name="link-library-dependencies"></a>Lier les dépendances de la bibliothèque

Indique s’il convient de lier les fichiers .lib produits par les projets dépendants. En général, vous souhaitez créer un lien dans les fichiers. lib, mais ce n’est peut-être pas le cas pour certaines dll.

Vous pouvez également spécifier un fichier .obj en fournissant le nom de fichier et le chemin relatif, par exemple « ..\\..\MyLibProject\MyObjFile.obj ». Si le code source du fichier. obj #includes un en-tête précompilé, par exemple pch. h, le fichier PCH. obj se trouve dans le même dossier que MyObjFile. obj. Vous devez également ajouter pch. obj comme dépendance supplémentaire.

### <a name="use-library-dependency-inputs"></a>Utiliser les entrées de dépendance de la bibliothèque

Spécifie s’il faut utiliser les entrées de l’outil bibliothécaire, plutôt que le fichier bibliothèque lui-même, lors de la liaison des sorties de bibliothèque des dépendances du projet. Dans un grand projet, quand un projet dépendant produit un fichier .lib, la liaison incrémentielle est désactivée. Si de nombreux projets dépendants génèrent des fichiers .lib, la génération de l’application peut prendre un certain temps. Quand cette propriété a la valeur **Oui**, le système de projet lie les fichiers. obj des fichiers. libs produits par des projets dépendants, ce qui permet d’effectuer des liens incrémentiels.

Pour plus d’informations sur l’accès à la page de propriétés **général** de l’éditeur de liens, consultez [définir le compilateur C++ et les propriétés de génération dans Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>État du lien

Spécifie si l’éditeur de liens doit afficher un indicateur de progression indiquant quel pourcentage du lien est terminé. La valeur par défaut est de ne pas afficher ces informations d’État. ([/LTCG](ltcg-link-time-code-generation.md): état | LTCG : NOSTATUS)

### <a name="prevent-dll-binding"></a>Empêcher la liaison de DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md): no définit un bit dans l’en-tête d’une dll qui indique à Bind.exe que l’image n’est pas autorisée à être liée. Vous ne voulez peut-être pas qu’une DLL soit liée si elle a été signée numériquement (la liaison invalide la signature).

### <a name="treat-linker-warning-as-errors"></a>Considérer l’avertissement de l’éditeur de liens comme des erreurs

[/WX](wx-treat-linker-warnings-as-errors.md) n’entraîne la génération d’aucun fichier de sortie si l’éditeur de liens génère un avertissement.

### <a name="force-file-output"></a>Forcer la sortie du fichier

L’option [/force](force-force-file-output.md) indique à l’éditeur de liens de créer un fichier. exe ou une dll même si un symbole est référencé mais pas défini, ou s’il est défini sur multiplier. Il peut créer un fichier. exe non valide.

**Choices**

- **Activé** -/force sans argument implique à la fois plusieurs et non résolus.
- **Symbole défini par multiplication uniquement** -utilisez/force : multiple pour créer un fichier de sortie, même si Link trouve plusieurs définitions pour un symbole.
- **Symbole non défini uniquement** -utilisez/force : Unresolved pour créer un fichier de sortie si Link trouve un symbole non défini. /FORCE : Unresolved est ignoré si le symbole de point d’entrée n’est pas résolu.

### <a name="create-hot-patchable-image"></a>Créer une image corrigeable à chaud

Prépare une image pour la mise à jour à chaud.

**Choices**

- **Activé** : prépare une image pour la mise à jour à chaud.
- **Image x86 uniquement** -prépare une image x86 pour la mise à jour à chaud.
- **Image x64 uniquement** -prépare une image x64 pour la mise à jour à chaud.
- **Image Itanium uniquement** -prépare une image Itanium pour la mise à jour à chaud.

### <a name="specify-section-attributes"></a>Spécifier les attributs de section

L’option [/section](section-specify-section-attributes.md) modifie les attributs d’une section, en substituant les attributs définis lors de la compilation du fichier. obj de la section.

## <a name="input-property-page"></a>Page de propriétés d’entrée

### <a name="additional-dependencies"></a>Dépendances supplémentaires

Spécifie des éléments supplémentaires à ajouter à la ligne de commande de lien, par exemple, *Kernel32. lib*.

### <a name="ignore-all-default-libraries"></a>Ignorer toutes les bibliothèques par défaut

L’option [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) indique à l’éditeur de liens de supprimer une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’il recherche lors de la résolution des références externes.

### <a name="ignore-specific-default-libraries"></a>Bibliothèques par défaut spécifiques ignorées

Spécifie un ou plusieurs noms de bibliothèques par défaut à ignorer. Séparez plusieurs bibliothèques par des points-virgules. (/NODEFAULTLIB : [nom, nom,...])

### <a name="module-definition-file"></a>Fichier de définition de module

L’option [/def](def-specify-module-definition-file.md) passe un fichier de définition de module (. def) à l’éditeur de liens. Un seul fichier. def peut être spécifié pour la liaison.

### <a name="add-module-to-assembly"></a>Ajouter un module à l’assembly

L’option [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) vous permet d’ajouter une référence de module à un assembly. Les informations de type dans le module ne sont pas disponibles pour le programme d’assembly qui a ajouté la référence de module. Toutefois, les informations de type dans le module sont disponibles pour tout programme qui fait référence à l’assembly.

### <a name="embed-managed-resource-file"></a>Incorporer un fichier de ressources managé

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) incorpore un fichier de ressources dans le fichier de sortie.

### <a name="force-symbol-references"></a>Références des symboles forcées

L’option [/include](include-force-symbol-references.md) indique à l’éditeur de liens d’ajouter un symbole spécifié à la table de symboles.

### <a name="delay-loaded-dlls"></a>Dll à chargement différé

L’option [/delayload](delayload-delay-load-import.md) entraîne le chargement différé des dll. Le nom de la dll spécifie une DLL pour différer le chargement.

### <a name="assembly-link-resource"></a>Ressource de lien d’assembly

L’option [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) crée un lien vers une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie.

## <a name="manifest-file-property-page"></a>Page de propriétés du fichier manifeste

### <a name="generate-manifest"></a>Générer le manifeste

[/Manifest](manifest-create-side-by-side-assembly-manifest.md) spécifie que l’éditeur de liens doit créer un fichier manifeste côte à côte.

### <a name="manifest-file"></a>Fichier manifeste

[/MANIFESTFILE](manifestfile-name-manifest-file.md) vous permet de modifier le nom par défaut du fichier manifeste. Le nom par défaut du fichier manifeste est le nom de fichier avec. manifest ajouté.

### <a name="additional-manifest-dependencies"></a>Dépendances de manifeste supplémentaires

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) vous permet de spécifier des attributs qui seront placés dans la section des dépendances du fichier manifeste.

### <a name="allow-isolation"></a>Autoriser l’isolation

Spécifie un comportement pour la recherche de manifeste. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): non)

### <a name="enable-user-account-control-uac"></a>Activer le contrôle de compte d’utilisateur (UAC)

Spécifie si le contrôle de compte d’utilisateur est activé ou non.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC : no)

### <a name="uac-execution-level"></a>Niveau d’exécution du contrôle de compte d’utilisateur

Spécifie le niveau d’exécution demandé pour l’application lors de l’exécution avec le contrôle de compte d’utilisateur.  (/MANIFESTUAC : Level = [valeur])

**Choices**

- **asInvoker** -niveau d’exécution UAC : en tant que demandeur.
- **highestAvailable** -niveau d’exécution du contrôle de compte d’utilisateur : disponible le plus élevé.
- **requireAdministrator** -niveau d’exécution du contrôle de compte d’utilisateur : exiger un administrateur.

### <a name="uac-bypass-ui-protection"></a>Contourner le contrôle de compte d’utilisateur protection

Spécifie s’il faut ignorer les niveaux de protection de l’interface utilisateur pour les autres fenêtres sur le bureau.  Définissez cette propriété sur « Oui » uniquement pour les applications d’accessibilité.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): UIAccess = [true | false])

## <a name="debugging-property-page"></a>Page de propriétés de débogage

### <a name="generate-debug-info"></a>Générer des informations de débogage

Cette option permet de créer des informations de débogage pour le fichier. exe ou la DLL.

**Choices**

- **Non** : ne produit aucune information de débogage.
- **Générer des informations de débogage** -créer une base de données de programme (PDB) complète idéale pour la distribution vers le serveur de symboles Microsoft.
- **Générer des informations de débogage optimisées pour des liens plus rapides** : produit une base de données de programme (PDB) idéale pour le cycle de modification-lien-débogage.
- **Générer des informations de débogage optimisées pour le partage et la publication** : produit une base de données de programme (PDB) idéale pour le cycle de modification-lien-débogage.

### <a name="generate-program-database-file"></a>Générer le fichier de base de données du programme

Par défaut, quand [/Debug](debug-generate-debug-info.md) est spécifié, l’éditeur de liens crée une base de données de programme (PDB) qui contient des informations de débogage. Le nom de fichier par défaut pour le fichier PDB porte le nom de base du programme et l’extension. pdb.

### <a name="strip-private-symbols"></a>Supprimer les symboles privés

L’option [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) crée un deuxième fichier de base de données du programme (PDB) lorsque vous générez votre image de programme avec l’une des options du compilateur ou de l’éditeur de liens qui génèrent un fichier PDB (/Debug,/Z7,/Zd ou/Zi).

### <a name="generate-map-file"></a>Générer un fichier de mappage

L’option [/Map](map-generate-mapfile.md) indique à l’éditeur de liens de créer un mappage.

### <a name="map-file-name"></a>Nom de fichier de mappage

Nom spécifié par l’utilisateur pour le mappage. Il remplace le nom par défaut.

### <a name="map-exports"></a>Mappage des exportations

L’option [/MapInfo](mapinfo-include-information-in-mapfile.md) indique à l’éditeur de liens d’inclure les informations spécifiées dans un mappage, qui est créé si vous spécifiez l’option/map. Les exportations indiquent à l’éditeur de liens d’inclure les fonctions exportées.

### <a name="debuggable-assembly"></a>Assembly pouvant être débogué

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) émet l’attribut DebuggableAttribute avec le suivi des informations de débogage et désactive les optimisations JIT.

## <a name="system-property-page"></a>Page de propriétés système

### <a name="subsystem"></a>Sous-système

L’option [/Subsystem](subsystem-specify-subsystem.md) indique au système d’exploitation comment exécuter le fichier. exe. Le choix du sous-système affecte le symbole de point d’entrée (ou la fonction de point d’entrée) choisi par l’éditeur de liens.

**Choices**

- **Non défini** -aucun sous-système défini.
- **Console** : application en mode caractères Win32. Les applications console reçoivent une console par le système d’exploitation. Si main ou wmain est défini, CONSOLE est la valeur par défaut.
- **Windows** -l’application ne nécessite pas de console, probablement parce qu’elle crée ses propres fenêtres pour l’interaction avec l’utilisateur. Si WinMain ou wWinMain est défini, WINDOWS est la valeur par défaut.
- **Native** -pilotes de périphérique pour Windows NT. Si/DRIVER : WDM est spécifié, NATIVE est la valeur par défaut.
- Application **EFI** -application EFI.
- **Pilote de service de démarrage EFI** -pilote de service de démarrage EFI.
- ROM **EFI** -ROM EFI.
- Runtime **EFI** -Runtime EFI.
- **POSIX** -application qui s’exécute avec le sous-système POSIX dans Windows NT.

### <a name="minimum-required-version"></a>Version minimale requise

Spécifiez la version minimale requise du sous-système. Les arguments sont des nombres décimaux compris entre 0 et 65 535.

### <a name="heap-reserve-size"></a>Taille de la réserve de tas

Spécifie la taille totale d’allocation des tas dans la mémoire virtuelle. La valeur par défaut est 1 Mo.    ([/Heap](heap-set-heap-size.md): Reserve)

### <a name="heap-commit-size"></a>Taille de la validation du tas

Spécifie la taille totale d’allocation des tas dans la mémoire physique. La valeur par défaut est 4 Ko.    ([/Heap](heap-set-heap-size.md): Reserve, Commit)

### <a name="stack-reserve-size"></a>Taille de réserve de pile

Spécifie la taille totale d’allocation de piles dans la mémoire virtuelle. La valeur par défaut est 1 Mo.     ([/Stack](stack-stack-allocations.md): Reserve)

### <a name="stack-commit-size"></a>Taille de la validation de pile

Spécifie la taille totale d’allocation de piles dans la mémoire physique. La valeur par défaut est 4 Ko.     ([/Stack](stack-stack-allocations.md): Reserve, Commit)

### <a name="enable-large-addresses"></a>Activer les adresses volumineuses

L’option [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) indique à l’éditeur de liens que l’application peut gérer des adresses supérieures à 2 gigaoctets. Par défaut,/LARGEADDRESSAWARE : NO est activé si/LARGEADDRESSAWARE n’est pas spécifié sur la ligne de l’éditeur de liens.

### <a name="terminal-server"></a>Terminal Server

L’option [/TSAWARE](tsaware-create-terminal-server-aware-application.md) définit un indicateur dans le champ IMAGE_OPTIONAL_HEADER DllCharacteristics dans l’en-tête facultatif de l’image du programme. Si cet indicateur est défini, le serveur Terminal Server n’apportera aucune modification à l’application.

### <a name="swap-run-from-cd"></a>Échange d’exécution à partir du CD

L’option [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indique au système d’exploitation de copier la sortie de l’éditeur de liens dans un fichier d’échange, puis d’exécuter l’image à partir de là. Cette option est une fonctionnalité de Windows NT 4,0 (et versions ultérieures). Si vous spécifiez **CD** , le système d’exploitation copie l’image sur un disque amovible dans un fichier d’échange, puis la charge.

### <a name="swap-run-from-network"></a>Échange d’exécution à partir du réseau

L’option [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) indique au système d’exploitation de copier la sortie de l’éditeur de liens dans un fichier d’échange, puis d’exécuter l’image à partir de là. Cette option est une fonctionnalité de Windows NT 4,0 (et versions ultérieures). Si **net** est spécifié, le système d’exploitation copie tout d’abord l’image binaire du réseau dans un fichier d’échange et la charge à partir de là. Cette option est utile pour exécuter des applications sur le réseau.

### <a name="driver"></a>Pilote

Utilisez l’option [/Driver](driver-windows-nt-kernel-mode-driver.md) de l’éditeur de liens pour générer un pilote en mode noyau Windows NT.

**Choices**

- **Non défini** -paramètre de pilote par défaut.
- **Pilote-pilote**
- **Up** -/Driver : en fait, l’éditeur de liens ajoute le bit IMAGE_FILE_UP_SYSTEM_ONLY aux caractéristiques de l’en-tête de sortie pour spécifier qu’il s’agit d’un pilote monoprocesseur (up). Le système d’exploitation refuse de charger un pilote UP sur un système multiprocesseur (MP).
- **WDM** -/Driver : WDM force l’éditeur de liens à définir le bit IMAGE_DLLCHARACTERISTICS_WDM_DRIVER dans le champ DLLCHARACTERISTICS de l’en-tête facultatif.

## <a name="optimization-property-page"></a>Page de propriétés optimisation

### <a name="references"></a>References

[/OPT](opt-optimizations.md): Ref élimine les fonctions et/ou les données qui ne sont jamais référencées alors que/opt : NOREF conserve les fonctions et/ou les données qui ne sont jamais référencées.

### <a name="enable-comdat-folding"></a>Activer le pliage COMDAT

Utilisez [/OPT](opt-optimizations.md): ICF \[ = iterations] pour effectuer un repli COMDAT identique.

### <a name="function-order"></a>Ordre des fonctions

L’option [/Order](order-put-functions-in-order.md)indique à Link d’optimiser votre programme en plaçant certains COMDAT dans l’image dans un ordre prédéterminé. LINK place les fonctions dans l’ordre spécifié au sein de chaque section de l’image.

### <a name="profile-guided-database"></a>Base de données guidée par profil

Spécifiez le fichier. PGD pour les optimisations guidées par profil. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Génération de code durant l’édition de liens

Spécifie la génération du code durant l’édition de liens. ([/LTCG](ltcg-link-time-code-generation.md))

**Choices**

- **Default** -paramètre LTCG par défaut.
- Utiliser la génération de **code durant l’édition de liens rapide** : utilisez la génération de code durant l’édition de liens avec [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Utilisez la génération de code durant l’édition de liens** -utilisez la [génération de code durant l’édition de liens](ltcg-link-time-code-generation.md).
- **Optimisation guidée par profil-instrumenter** -utiliser l' [optimisation guidée par profil](../profile-guided-optimizations.md) avec :P ginstrument.
- **Optimisation guidée par profil-optimisation** : spécifie que l’éditeur de liens doit utiliser les données de profil créées après l’exécution du fichier binaire instrumenté pour créer une image optimisée.
- **Optimisation guidée par profil-mettre à jour** : permet et effectue le suivi de la liste des fichiers d’entrée à ajouter ou à modifier à partir de ce qui a été spécifié dans la phase :P ginstrument.

## <a name="embedded-idl-property-page"></a>Page de propriétés IDL incorporé

### <a name="midl-commands"></a>Commandes MIDL

Spécifiez les options de ligne de commande MIDL. ([/MIDL](midl-specify-midl-command-line-options.md) :@responsefile )

### <a name="ignore-embedded-idl"></a>IDL incorporé ignoré

L’option [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) spécifie que les attributs IDL du code source ne doivent pas être traités dans un fichier. idl.

### <a name="merged-idl-base-file-name"></a>Nom de fichier de base IDL fusionné

L’option [/Idlout](idlout-name-midl-output-files.md) spécifie le nom et l’extension du fichier. idl.

### <a name="type-library"></a>Bibliothèque de types

L’option [/TLBOUT](tlbout-name-dot-tlb-file.md) spécifie le nom et l’extension du fichier. tlb.

### <a name="typelib-resource-id"></a>ID de ressource TypeLib

Vous permet de spécifier l’ID de ressource de la bibliothèque de types générée par l’éditeur de liens. ([/TLBID](tlbid-specify-resource-id-for-typelib.md): ID)

## <a name="windows-metadata-property-page"></a>Page de propriétés de métadonnées Windows

### <a name="generate-windows-metadata"></a>Générer des métadonnées Windows

Active ou désactive la génération de métadonnées Windows.

**Choices**

- **Oui** : active la génération des fichiers de métadonnées Windows.
- **Non** : désactive la génération de fichiers de métadonnées Windows.

### <a name="windows-metadata-file"></a>Fichier de métadonnées Windows

Commutateur de l’option [/WINMDFILE](winmdfile-specify-winmd-file.md) .

### <a name="windows-metadata-key-file"></a>Fichier de clé des métadonnées Windows

Spécifiez une clé ou une paire de clés pour signer les métadonnées Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): nom_fichier)

### <a name="windows-metadata-key-container"></a>Conteneur de clé de métadonnées Windows

Spécifiez un conteneur de clé pour signer les métadonnées Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): nom)

### <a name="windows-metadata-delay-sign"></a>Signature de délai des métadonnées Windows

Signer partiellement les métadonnées Windows. Utilisez [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) si vous souhaitez uniquement placer la clé publique dans les métadonnées Windows. La valeur par défaut est/WINMDDELAYSIGN : NO.

## <a name="advanced-property-page"></a>Page de propriétés avancé

### <a name="entry-point"></a>Point d'entrée

L’option [/entry](entry-entry-point-symbol.md) spécifie une fonction de point d’entrée comme adresse de départ pour un fichier. exe ou une dll.

### <a name="no-entry-point"></a>Aucun point d’entrée

L’option [/noentry](noentry-no-entry-point.md)est requise pour la création d’une dll de ressource uniquement. Utilisez cette option pour empêcher Link de lier une référence à `_main` dans la dll.

### <a name="set-checksum"></a>Définir la somme de contrôle

L’option [/Release](release-set-the-checksum.md) définit la somme de contrôle dans l’en-tête d’un fichier. exe.

### <a name="base-address"></a>Adresse de base

Définit une adresse de base pour le programme. ([/Base](base-base-address.md): {adresse \[ , taille] | @filename , clé})

### <a name="randomized-base-address"></a>Adresse de base aléatoire

Adresse de base aléatoire. ([/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) \[ : no])

### <a name="fixed-base-address"></a>Adresse de base fixe

Crée un programme qui peut être chargé uniquement à son adresse de base préférée. ([/fixed](fixed-fixed-base-address.md) \[ : no])

### <a name="data-execution-prevention-dep"></a>Prévention de l’exécution des données 

Marque un fichier exécutable comme ayant été testé pour qu’il soit compatible avec la fonctionnalité de prévention de l’exécution des données Windows. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md) \[ : no])

### <a name="turn-off-assembly-generation"></a>Désactiver la génération de l’assembly

L’option [/noAssembly](noassembly-create-a-msil-module.md) indique à l’éditeur de liens de créer une image pour le fichier de sortie actif sans assembly .NET Framework.

### <a name="unload-delay-loaded-dll"></a>Décharger la DLL à chargement différé

Le qualificateur **Unload** indique à la fonction d’assistance de chargement différé de prendre en charge le déchargement explicite de la dll. ([/delay](delay-delay-load-import-settings.md): Unload)

### <a name="nobind-delay-loaded-dll"></a>DLL à chargement différé NOBIND

Le qualificateur **NOBIND** indique à l’éditeur de liens de ne pas inclure une IAT pouvant être liée dans l’image finale. L'option par défaut consiste à créer la table IAT pouvant être liée pour les DLL chargées en différé. ([/delay](delay-delay-load-import-settings.md): nobind)

### <a name="import-library"></a>Bibliothèque d'importation

Remplace le nom par défaut de la bibliothèque d’importation. ([/IMPLIB](implib-name-import-library.md): NomFichier)

### <a name="merge-sections"></a>Fusionner les sections

L’option [/Merge](merge-combine-sections.md) combine la première section (from) à la deuxième section (to), en nommant la section résultante en. Par exemple,/Merge :. rdata =. Text.

### <a name="target-machine"></a>Ordinateur cible

L’option [/machine](machine-specify-target-platform.md) spécifie la plateforme cible pour le programme.

**Choices**

- **Non défini**
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

Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances. Requiert la définition de GenerateDebugInformation (/[/Debug](debug-generate-debug-info.md)). ([/Profile](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Attribut de thread CLR

Spécifiez explicitement l’attribut de thread pour le point d’entrée de votre programme CLR.

**Choices**

- **Attribut de thread MTA** : applique l’attribut MTAThreadAttribute au point d’entrée de votre programme.
- **Attribut de thread STA** : applique l’attribut STAThreadAttribute au point d’entrée de votre programme.
- **Attribut de thread par défaut** -identique à ne pas spécifier [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Permet au Common Language Runtime (CLR) de définir l’attribut de thread par défaut.

### <a name="clr-image-type"></a>Type d’image CLR

Définit le type (IJW, pure ou sécurisée) d’une image CLR.

**Choices**

- **Forcer l’image IJW**
- **Forcer l’image IL pure**
- **Forcer l’image IL sécurisée**
- **Type d’image par défaut**

### <a name="key-file"></a>Fichier de clé

Spécifiez une clé ou une paire de clés pour signer un assembly. ([/Keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): NomFichier)

### <a name="key-container"></a>Conteneur de clé

Spécifiez un conteneur de clé pour signer un assembly. ([/Keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md): nom)

### <a name="delay-sign"></a>Temporisation de la signature

Signer partiellement un assembly. Utilisez [/delaysign](delaysign-partially-sign-an-assembly.md) si vous souhaitez uniquement placer la clé publique dans l’assembly. La valeur par défaut est/DELAYSIGN : NO.

### <a name="clr-unmanaged-code-check"></a>Vérification du code non managé CLR

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) spécifie si l’éditeur de liens applique SuppressUnmanagedCodeSecurityAttribute aux appels PInvoke générés par l’éditeur de liens à partir du code managé dans des DLL natives.

### <a name="error-reporting"></a>Rapport d'erreurs

Vous permet de signaler les erreurs internes du compilateur (ICE) directement à l'équipe Visual C++.

**Choices**

- **PromptImmediately** -invite immédiatement.
- **File** d’attente pour la prochaine connexion-file d’attente pour la prochaine connexion.
- **Envoyer** le rapport d’erreurs-envoyer le rapport d’erreurs.
- **Aucun rapport d’erreurs** -aucun rapport d’erreurs.

### <a name="sectionalignment"></a>SectionAlignment

L’option [/align](align-section-alignment.md) spécifie l’alignement de chaque section dans l’espace d’adressage linéaire du programme. L’argument number est en octets et doit être une puissance de deux.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Conserver le dernier code d’erreur pour les appels PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), qui est activé par défaut, conserve le dernier code d’erreur des fonctions appelées via le mécanisme P/Invoke, qui vous permet d’appeler des fonctions natives dans des dll, à partir du code compilé avec/CLR.

**Choices**

- **Activé** : activez CLRSupportLastError.
- **Désactivé** : désactive CLRSupportLastError.
- **DLL système uniquement** : activez CLRSupportLastError uniquement pour les DLL système.

### <a name="image-has-safe-exception-handlers"></a>L’image a des gestionnaires d’exceptions sécurisés

Lorsque [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) est spécifié, l’éditeur de liens produira uniquement une image s’il peut également générer une table des gestionnaires d’exceptions sécurisés de l’image. Ce tableau spécifie pour le système d’exploitation les gestionnaires d’exceptions qui sont valides pour l’image.
