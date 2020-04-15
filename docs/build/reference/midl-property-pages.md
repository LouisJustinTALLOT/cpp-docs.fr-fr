---
title: Pages de propriété de compilateur DE MIDL
ms.date: 07/24/2019
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
ms.openlocfilehash: d6833230baca892836c187799df7f0658aa16772
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336251"
---
# <a name="midl-property-pages"></a>Pages de propriétés MIDL

Les pages de propriété MIDL sont disponibles comme une propriété d’article sur un . Fichier IDL dans un projet CMD qui utilise COM. Utilisez-les pour configurer le [compilateur MIDL](/windows/win32/midl/using-the-midl-compiler-2). Pour plus d’informations sur l’accès par programmation aux options MIDL des projets C++, consultez l’objet <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>. Voir aussi [General MIDL Command-line Syntax](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Page de propriétés Général

### <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Spécifie une ou plusieurs définitions, y\[compris\]les macros MIDL ([/D)](/windows/win32/midl/-d)macros ).

### <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter\]au chemin inclus ([/I](/windows/win32/midl/-i)\[chemin ).

### <a name="additional-metadata-directories"></a>Répertoires de métadonnées supplémentaires

Spécifier l’annuaire contenant le fichier Windows.Foundation.WinMD ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[chemin\]).

### <a name="enable-windows-runtime"></a>Activez Windows Runtime

Activez la sémantique Windows Runtime pour créer un fichier windows de métadonnées ([/winrt](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Ignorer la norme Inclure la voie

Ignorer le courant et les répertoires INCLUDE ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>MkTypLib Compatible

Forces compatibilité avec mktyplib.exe version 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Niveau d’avertissement

Sélectionne la rigueur des erreurs de code MIDL ([/W](/windows/win32/midl/-w)).

**Choix**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Permet à MIDL de traiter tous les avertissements comme des erreurs ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprimer l’affichage de la bannière de démarrage et le message[d’information ( /nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>C Compiler Char Type

Spécifie le type de caractère par défaut du compilateur C qui sera utilisé pour compiler le code généré. [(/char](/windows/win32/midl/-char) signé’unsigned’ascii7).

**Choix**

- **Signé** - Signé
- **Non signé** - Non signé
- **Ascii** - Ascii

### <a name="target-environment"></a>Environnement cible

Précise quel environnement cibler ([/env](/windows/win32/midl/-env) arm32-win32-ia64-x64).

**Choix**

- **Pas fixé** - Win32
- **Microsoft Windows 32 bits** - Win32
- **Microsoft Windows 64 bits sur Itanium** - IA64
- **Microsoft Windows ARM** - ARM
- **Microsoft Windows ARM64** - ARM64
- **Microsoft Windows 64 bits sur x64** - X64

### <a name="generate-stubless-proxies"></a>Générer des procurations Stubless

Générer des talons entièrement interprétés avec des extensions et des procurations stubless pour les interfaces d’objets ([/Oicf](/windows/win32/midl/-oi), [/Oif](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Supprimer les avertissements du compilateur

Supprimer les messages d’avertissement compilateur ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Mode configuration d’application

Autoriser certains attributs ACF dans le fichier IDL ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>ID des paramètres régionaux

Spécifie le LCID pour les fichiers d’entrée, les noms de fichiers et les trajectoires d’annuaire[(/lcid](/windows/win32/midl/-lcid) DECIMAL).

### <a name="multi-processor-compilation"></a>Compilation multi-processeur

Exécutez plusieurs instances en même temps.

## <a name="output-property-page"></a>Page de propriété de sortie

### <a name="output-directory"></a>Répertoire de sortie

Spécifie le répertoire de sortie[(/out](/windows/win32/midl/-out) [directory]).

### <a name="metadata-file"></a>Fichier de métadonnées

Spécifie le nom du fichier des métadonnées générées (nom de fichier[winmd).](/windows/win32/midl/-winmd)

### <a name="header-file"></a>Fichier d'en-tête

Spécifie le nom du fichier d’en-tête généré[(/h](/windows/win32/midl/-h) nom de fichier).

### <a name="dlldata-file"></a>Fichier DllData

Précise le nom du fichier DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) nom de fichier).

### <a name="iid-file"></a>Fichier IID

Spécifie le nom du fichier Interface Identifier (/nom de fichier[iid).](/windows/win32/midl/-iid)

### <a name="proxy-file"></a>Fichier proxy

Spécifie le nom du fichier proxy[(/nom](/windows/win32/midl/-proxy) de fichier proxy).

### <a name="generate-type-library"></a>Générer type bibliothèque

Spécifier pour ne pas générer une bibliothèque de type ([/notlb] pour non).

### <a name="type-library"></a>Bibliothèque de type

Spécifie le nom du fichier de bibliothèque type ([/tlb](/windows/win32/midl/-tlb) nom de fichier).

### <a name="generate-client-stub-files"></a>Générer des fichiers Stub Clients

Générer le fichier de talon client seulement ([/client](/windows/win32/midl/-client) [stub’none]).

**Choix**

- **Stub** - Stub
- **Aucun** - Aucun

### <a name="generate-server-stub-files"></a>Générer des fichiers de talon serveur

Générer le fichier de talon serveur seulement ([/serveur](/windows/win32/midl/-server) [stub’none]).

**Choix**

- **Stub** - Stub
- **Aucun** - Aucun

### <a name="client-stub-file"></a>Fichier Stub client

Spécifier le fichier de talon client[(/cstub](/windows/win32/midl/-cstub) [fichier]).

### <a name="server-stub-file"></a>Fichier De talon de serveur

Spécifier le fichier de talon serveur ([/sstub](/windows/win32/midl/-sstub) [fichier]).

### <a name="type-library-format"></a>Format de bibliothèque de type

Spécifie le format de fichier de bibliothèque de type ([/oldtlbMD/newtlb]).

**Choix**

- **NewFormat** - Nouveau format
- **OldFormat** - Ancien Format

## <a name="advanced-property-page"></a>Page de propriété avancée

### <a name="c-preprocess-options"></a>Options de prétraitement C

Spécifie les commutateurs pour passer au préprocesseur de compilateur C[(/cpp_opt](/windows/win32/midl/-cpp-opt) commutateurs).

### <a name="undefine-preprocessor-definitions"></a>Annuler la définition de définitions de préprocesseur

Spécifie un ou plusieurs indéfines, y compris les macros MIDL ([/U](/windows/win32/midl/-U) [macros]).

### <a name="enable-error-checking"></a>Activez la vérification des erreurs

Sélectionnez l’option de vérification des erreurs ([/erreur all’none]).

**Choix**

- **EnableCustom** - Tous
- **Tous** - Tous
- **Aucun** - Aucun

### <a name="check-allocations"></a>Vérifier les allocations

Découvrez les erreurs de mémoire[(/allocation d’erreurs).](/windows/win32/midl/-error)

### <a name="check-bounds"></a>Vérifier les limites

Vérifier la taille vs la spécification de longueur de transmission[(/erreur](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Vérifiez la gamme Enum

Vérifiez que les valeurs enum sont dans la plage autorisée[(/enum d’erreur).](/windows/win32/midl/-error)

### <a name="check-reference-pointers"></a>Vérifier les pointeurs de référence

Vérifiez que les pointeurs d’arbitres ne sont pas nuls[(/arbitre d’erreur).](/windows/win32/midl/-error)

### <a name="check-stub-data"></a>Vérifier les données Stub

Émettre une vérification supplémentaire de la validité des données de talon côté serveur ([/erreur](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Prepend avec 'ABI' namespace

Préciez l’espace nom 'ABI' à tous les types.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Valider les paramètres

Générer des informations supplémentaires pour valider les paramètres ([/robuste](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Alignement des membres de Struct

Spécifie le niveau d’emballage des structures dans le système cible (/ZpN).

**Choix**

- **Non réglé** - Pas réglé
- **1 Byte** - Zp1
- **2 Byte** - Zp2
- **4 Byte** - Zp4
- **8 Byte** - Zp8

### <a name="redirect-output"></a>Rendement redirection

Redirige la sortie de l’écran vers un fichier ([/o](/windows/win32/midl/-o) fichier).

### <a name="minimum-target-system"></a>Système cible minimum

Définissez le système cible minimum ([/target](/windows/win32/midl/-target) STRING).
