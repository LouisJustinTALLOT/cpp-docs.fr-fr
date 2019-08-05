---
title: Pages de propriétés du compilateur MIDL
ms.date: 7/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: 0113fbd68d7687236b91b098ead2ac6b8338fee9
ms.sourcegitcommit: af4ab63866ed09b5988ed53f1bb6996a54f02484
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787074"
---
# <a name="midl-property-pages"></a>Pages de propriétés MIDL

Les pages de propriétés MIDL sont disponibles en tant que propriété d’élément sur un. Fichier IDL dans un C++ projet qui utilise com. Utilisez-les pour configurer le [compilateur MIDL](/windows/win32/midl/using-the-midl-compiler-2). Pour plus d’informations sur l’accès par programmation aux options MIDL des projets C++, consultez l’objet <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>. Voir aussi [syntaxe générale de la ligne de commande MIDL](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Général, page de propriétés

### <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Spécifie une ou plusieurs définitions, y compris les macros MIDL\[([/d](/windows/win32/midl/-d))\].

### <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter au chemin d’accès include ([/i](/windows/win32/midl/-i)\[Path\]).

### <a name="additional-metadata-directories"></a>Répertoires de métadonnées supplémentaires

Spécifiez le répertoire contenant le fichier Windows. Foundation. WinMD (chemin\]d’accès[/metadata_dir](/windows/win32/midl/-metadata-dir) \[).

### <a name="enable-windows-runtime"></a>Activer Windows Runtime

Activez Windows Runtime sémantique pour créer un fichier de métadonnées Windows ([/WinRT](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignorer le chemin d’accès Include standard

Ignorez les répertoires actuels et INCLUDe ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>Compatible MkTypLib

Force la compatibilité avec mktyplib. exe version 2,03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Niveau d’avertissement

Sélectionne la rigueur des erreurs de code MIDL ([/w](/windows/win32/midl/-w)).

**Choix**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Permet à MIDL de traiter tous les avertissements comme des erreurs ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprimer l’affichage de la bannière de démarrage et du message d’information ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>Type de caractère du compilateur C

Spécifie le type de caractère par défaut du compilateur C qui sera utilisé pour compiler le code généré. ([/char](/windows/win32/midl/-char) signé | unsigned | ascii7).

**Choix**

- **Signé** -signé
- Non **signé** -non signé
- **ASCII** -ASCII

### <a name="target-environment"></a>Environnement cible

Spécifie l’environnement à cibler ([/env](/windows/win32/midl/-env) Arm32 | Win32 | ia64 | x64).

**Choix**

- **Non défini** -Win32
- **Microsoft Windows 32** bits-Win32
- **Microsoft Windows 64 bits sur Itanium** -ia64
- **ARM Microsoft Windows** -ARM
- **Microsoft Windows ARM64** -ARM64
- **Microsoft Windows 64 bits sur x64** -x64

### <a name="generate-stubless-proxies"></a>Générer des proxies avec stub

Générez des stubs entièrement interprétés avec des extensions et des proxies sans stub pour les interfaces d’objet ([/Oicf](/windows/win32/midl/-oi), [/OIF](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Supprimer les avertissements du compilateur

Supprimez les messages d’avertissement du compilateur ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Mode de configuration de l’application

Autorisez les attributs ACF sélectionnés dans le fichier IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>ID de paramètres régionaux

Spécifie le LCID pour les fichiers d’entrée, les noms de fichiers et les chemins d’accès aux répertoires ([/LCID](/windows/win32/midl/-lcid) décimal).

### <a name="multi-processor-compilation"></a>Compilation multiprocesseur

Exécutez plusieurs instances en même temps.

## <a name="output-property-page"></a>Page de propriétés de sortie

### <a name="output-directory"></a>Répertoire de sortie

Spécifie le répertoire de sortie ([/out](/windows/win32/midl/-out) [Directory]).

### <a name="metadata-file"></a>Fichier de métadonnées

Spécifie le nom du fichier de métadonnées généré ([/winmd](/windows/win32/midl/-winmd) filename).

### <a name="header-file"></a>Fichier d’en-tête

Spécifie le nom du fichier d’en-tête généré ([/h](/windows/win32/midl/-h) filename).

### <a name="dlldata-file"></a>Fichier DllData

Spécifie le nom du fichier DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) filename).

### <a name="iid-file"></a>Fichier IID

Spécifie le nom du fichier d’identificateur d’interface (nom de fichier[/IID](/windows/win32/midl/-iid) ).

### <a name="proxy-file"></a>Fichier proxy

Spécifie le nom du fichier proxy (nom de fichier[/proxy](/windows/win32/midl/-proxy) ).

### <a name="generate-type-library"></a>Générer une bibliothèque de types

Spécifiez de ne pas générer de bibliothèque de types ([/notlb] pour non).

### <a name="type-library"></a>Bibliothèque de types

Spécifie le nom du fichier bibliothèque de types (nom de fichier[/TLB](/windows/win32/midl/-tlb) ).

### <a name="generate-client-stub-files"></a>Générer des fichiers stub client

Générer le fichier stub du client uniquement ([/client](/windows/win32/midl/-client) [stub | None]).

**Choix**

- Stub-stub
- **Aucun** -aucun

### <a name="generate-server-stub-files"></a>Générer des fichiers stub serveur

Générer le fichier stub du serveur uniquement ([/Server](/windows/win32/midl/-server) [stub | None]).

**Choix**

- Stub-stub
- **Aucun** -aucun

### <a name="client-stub-file"></a>Fichier stub client

Spécifiez le fichier stub du client ([/cstub](/windows/win32/midl/-cstub) [fichier]).

### <a name="server-stub-file"></a>Fichier stub serveur

Spécifiez le fichier stub du serveur ([/sstub](/windows/win32/midl/-sstub) [fichier]).

### <a name="type-library-format"></a>Format de bibliothèque de types

Spécifie le format de fichier de bibliothèque de types ([/oldtlb |/newtlb]).

**Choix**

- **NewFormat** -nouveau format
- **OldFormat** -ancien format

## <a name="advanced-property-page"></a>Page de propriétés avancé

### <a name="c-preprocess-options"></a>Options de prétraitement C

Spécifie les commutateurs à passer au préprocesseur du compilateur C (commutateurs[/cpp_opt](/windows/win32/midl/-cpp-opt) ).

### <a name="undefine-preprocessor-definitions"></a>Annuler la définition de définitions de préprocesseur

Spécifie une ou plusieurs non-définition, y compris les macros MIDL ([/u](/windows/win32/midl/-U) [macros]).

### <a name="enable-error-checking"></a>Activer la vérification des erreurs

Sélectionnez l’option de vérification des erreurs ([/Error All | None]).

**Choix**

- **EnableCustom** -tout
- **Tout** -tout
- **Aucun** -aucun

### <a name="check-allocations"></a>Vérifier les allocations

Rechercher les erreurs de mémoire insuffisante (attribution de[/Error](/windows/win32/midl/-error) ).

### <a name="check-bounds"></a>Vérifier les limites

Vérifiez la taille par rapport à la spécification de longueur de transmission ([/Error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Vérifier la plage d’énumération

Vérifiez que les valeurs enum se trouvent dans la plage autorisée ([/Error](/windows/win32/midl/-error) enum).

### <a name="check-reference-pointers"></a>Vérifier les pointeurs de référence

Vérifiez que les pointeurs de référence sont non null ([/Error](/windows/win32/midl/-error) Ref).

### <a name="check-stub-data"></a>Vérifier les données stub

Émettez une vérification supplémentaire pour la validité des données stub côté serveur ([/Error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Ajouter au début l’espace de noms’ABI'

Ajoutez l’espace de noms’ABI’à tous les types.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Valider les paramètres

Générez des informations supplémentaires pour valider les paramètres ([/Robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Alignement des membres de la structure

Spécifie le niveau de compression des structures dans le système cible (/ZpN).

**Choix**

- **Non défini** -non défini
- **1 octet** -Zp1
- **2 octets** -ZP2
- **4 octets** -zp4
- **8 octets** -Zp8

### <a name="redirect-output"></a>Rediriger la sortie

Redirige la sortie de l’écran vers un fichier (fichier[/o](/windows/win32/midl/-o) ).

### <a name="minimum-target-system"></a>Système cible minimal

Définissez le système cible minimal ([/target](/windows/win32/midl/-target) String).



