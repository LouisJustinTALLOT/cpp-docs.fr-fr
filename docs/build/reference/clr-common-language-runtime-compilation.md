---
title: /clr (Compilation pour le Common Language Runtime)
description: Utilisez l’option/CLR du compilateur Microsoft C++ pour compiler le code C++/CLI et C++ en tant que code managé.
ms.date: 10/25/2020
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: b4634b63e58344893d99e2217e57693a2c169f66
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639092"
---
# <a name="clr-common-language-runtime-compilation"></a>`/clr` (Compilation pour le Common Language Runtime)

Permet aux applications et aux composants d’utiliser les fonctionnalités du Common Language Runtime (CLR).

## <a name="syntax"></a>Syntaxe

> **`/clr`**\[**`:`**_options_ ]

## <a name="arguments"></a>Arguments

*Options*\
Un ou plusieurs des arguments séparés par des virgules suivants.

- aucun

   Sans option, **`/clr`** crée des métadonnées pour l’application. Ces métadonnées peuvent être utilisées par d'autres applications CLR et permettent à votre application d'utiliser les types et données des métadonnées appartenant à d'autres composants CLR. Pour plus d’informations, consultez [Assemblys mixtes (natif et managé)](../../dotnet/mixed-native-and-managed-assemblies.md).

- **`pure`**

   **`/clr:pure` est déconseillé** . L’option est supprimée dans Visual Studio 2017 et ultérieur. Nous vous recommandons de porter vers C# du code devant être écrit en MSIL pur.

- **`safe`**

   **`/clr:safe` est déconseillé** . L’option est supprimée dans Visual Studio 2017 et ultérieur. Nous vous recommandons de porter sur C# du code devant être écrit en MSIL sécurisé.

- **`noAssembly`**

   **`/clr:noAssembly` est déconseillé** . Utilisez à la place [ `/LN` (créer un module MSIL)](ln-create-msil-module.md) .

   Indique au compilateur de ne pas insérer de manifeste d’assembly dans le fichier de sortie. Par défaut, l' **`noAssembly`** option n’est pas appliquée.

   Un programme managé qui n’a pas de métadonnées d’assembly dans le manifeste est appelé *module* . L' **`noAssembly`** option peut être utilisée uniquement pour produire un module. Si vous compilez à l’aide de [`/c`](c-compile-without-linking.md) et **`/clr:noAssembly`** , spécifiez l' [`/NOASSEMBLY`](noassembly-create-a-msil-module.md) option dans la phase de l’éditeur de liens pour créer un module.

   Avant Visual Studio 2005, **`/clr:noAssembly`** obligatoire **`/LD`** . **`/LD`** est désormais implicite lorsque vous spécifiez **`/clr:noAssembly`** .

- **`initialAppDomain`**

   Permet à une application C++/CLI de s’exécuter sur la version 1 du CLR.  Une application compilée à l’aide de **`initialAppDomain`** ne doit pas être utilisée par une application qui utilise ASP.net, car elle n’est pas prise en charge dans la version 1 du CLR.

- **`nostdlib`**

   Indique au compilateur d’ignorer le répertoire par défaut *`\clr`* . Le compilateur génère des erreurs si vous incluez plusieurs versions d’une DLL, telles que System.dll. Cette option vous permet de spécifier l’infrastructure spécifique à utiliser pendant la compilation.

## <a name="remarks"></a>Notes

Le code managé est du code qui peut être inspecté et géré par le CLR. Le code managé peut accéder aux objets managés. Pour plus d’informations, consultez [ `/clr ` restrictions](clr-restrictions.md).

Pour plus d’informations sur le développement d’applications qui définissent et utilisent des types managés en C++, consultez [extensions de composant pour les plateformes Runtime](../../extensions/component-extensions-for-runtime-platforms.md).

Une application compilée à l’aide de **`/clr`** peut ou ne peut pas contenir de données managées.

Pour activer le débogage sur une application managée, consultez [ `/ASSEMBLYDEBUG` (Add DebuggableAttribute)](assemblydebug-add-debuggableattribute.md).

Seuls les types CLR sont instanciés sur le tas récupéré par le garbage collector. Pour plus d’informations, consultez [Classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md). Pour compiler une fonction en code natif, utilisez le pragma `unmanaged` . Pour plus d’informations, [ `managed` consultez `unmanaged` . ](../../preprocessor/managed-unmanaged.md)

Par défaut, **`/clr`** n’est pas en vigueur. Lorsque **`/clr`** est en vigueur, **`/MD`** est également activé. Pour plus d’informations, consultez [ `/MD` , `/MT` , `/LD` (utilisez Run-Time bibliothèque)](md-mt-ld-use-run-time-library.md). **`/MD`** garantit que les versions multithread, liées de manière dynamique, des routines d’exécution sont sélectionnées à partir des fichiers d’en-tête standard. Le multithreading est requis pour la programmation managée, car le garbage collector CLR exécute les finaliseurs dans un thread auxiliaire.

Si vous compilez à l’aide de **`/c`** , vous pouvez spécifier le type CLR du fichier de sortie résultant à l’aide de l’option de l' [`/CLRIMAGETYPE`](clrimagetype-specify-type-of-clr-image.md) éditeur de liens.

**`/clr`** implique **`/EHa`** , et aucune autre **`/EH`** option n’est prise en charge pour **`/clr`** . Pour plus d’informations, consultez [ `/EH` (modèle de gestion des exceptions)](eh-exception-handling-model.md).

Pour plus d’informations sur la façon de déterminer le type d’image CLR d’un fichier, consultez [`/CLRHEADER`](clrheader.md) .

Tous les modules passés à un appel donné de l’éditeur de liens doivent être compilés à l’aide de la même option du compilateur de la bibliothèque Runtime ( **`/MD`** ou **`/LD`** ).

Utilisez l' [`/ASSEMBLYRESOURCE`](assemblyresource-embed-a-managed-resource.md) option de l’éditeur de liens pour incorporer une ressource dans un assembly. [`/DELAYSIGN`](delaysign-partially-sign-an-assembly.md)[`/KEYCONTAINER`](keycontainer-specify-a-key-container-to-sign-an-assembly.md)les options, et de l' [`/KEYFILE`](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) éditeur de liens vous permettent également de personnaliser la façon dont un assembly est créé.

Lorsque **`/clr`** est utilisé, le `_MANAGED` symbole est défini sur 1. Pour plus d’informations, consultez [macros prédéfinies](../../preprocessor/predefined-macros.md).

Les variables globales dans un fichier objet natif sont initialisées en premier (pendant `DllMain` si l’exécutable est une dll), puis les variables globales de la section managée sont initialisées (avant l’exécution de tout code managé). [`#pragma init_seg`](../../preprocessor/init-seg.md) affecte uniquement l’ordre d’initialisation dans les catégories managées et non managées.

### <a name="metadata-and-unnamed-classes"></a>Métadonnées et classes sans nom

Les classes sans nom apparaissent dans les métadonnées sous des noms tels que  `$UnnamedClass$<crc-of-current-file-name>$<index>$` , où `<index>` est un nombre séquentiel des classes sans nom dans la compilation. Ainsi, l'exemple de code suivant génère une classe sans nom dans les métadonnées.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

Utilisez ildasm.exe pour afficher les métadonnées.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante **configuration** sur **toutes les configurations** , puis définissez la liste déroulante **plateforme** sur **toutes les plateformes** .

1. Sélectionnez la page **Propriétés**  >  **avancées** de configuration.

1. Modifiez la propriété **prise en charge du Common Language Runtime** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
