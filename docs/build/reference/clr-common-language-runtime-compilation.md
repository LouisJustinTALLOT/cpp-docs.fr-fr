---
title: /clr (Compilation pour le Common Language Runtime)
ms.date: 09/18/2018
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
ms.openlocfilehash: 1946fdabe66934e64cf95d3c3f12e16bc98ba664
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272544"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Compilation pour le Common Language Runtime)

Permet aux applications et aux composants d’utiliser les fonctionnalités du Common Language Runtime (CLR).

## <a name="syntax"></a>Syntaxe

> **/clr**[**:**_options_]

## <a name="arguments"></a>Arguments

*options*<br/>
Un ou plusieurs des commutateurs suivants, séparés par des virgules.

- none

   Aucune option, **/CLR** crée les métadonnées pour l’application. Ces métadonnées peuvent être utilisées par d'autres applications CLR et permettent à votre application d'utiliser les types et données des métadonnées appartenant à d'autres composants CLR. Pour plus d’informations, consultez [assemblys mixtes (natif et managé)](../../dotnet/mixed-native-and-managed-assemblies.md).

- **pure**

   **/ CLR : pure est déconseillé**. L’option est supprimée dans Visual Studio 2017. Nous vous recommandons de porter vers C# du code devant être écrit en MSIL pur.

- **safe**

   **/ CLR : safe est déconseillé**. L’option est supprimée dans Visual Studio 2017. Nous vous recommandons de porter le code qui doit être MSIL sécurisé en c#.

- **noAssembly**

   **/ CLR : noAssembly est déconseillée**. Utilisez plutôt [/LN (Create MSIL Module)](ln-create-msil-module.md) .

   Indique qu'un manifeste d'assembly ne doit pas être inséré dans le fichier de sortie. Par défaut, l’option **noAssembly** n’est pas activée.

   Un programme managé qui ne possède pas de métadonnées d'assembly dans le manifeste est appelé *module*. L’option **noAssembly** peut être utilisée uniquement pour produire un module. Si vous compilez en utilisant [/c](c-compile-without-linking.md) et **/clr:noAssembly**, spécifiez l’option [/NOASSEMBLY](noassembly-create-a-msil-module.md) dans la phase de l’éditeur de liens pour créer un module.

   Avant Visual C++ 2005, **/clr:noAssembly** nécessitait l’option **/LD**. **/LD** est désormais implicite quand vous spécifiez **/clr:noAssembly**.

- **initialAppDomain**

   Permet à une application Visual C++ à exécuter sur la version 1 du CLR.  Une application compilée en utilisant **initialAppDomain** ne doit pas être utilisée par une application qui utilise ASP.NET car elle n’est pas prise en charge dans la version 1 du CLR.

- **nostdlib**

   Indique au compilateur d'ignorer le répertoire \clr par défaut. Le compilateur produit des erreurs si vous incluez plusieurs versions d'une DLL telle que System.dll. Cette option vous permet de spécifier l'infrastructure spécifique à utiliser pendant la compilation.

## <a name="remarks"></a>Notes

Le code managé est du code qui peut être inspecté et géré par le CLR. Le code managé peut accéder aux objets managés. Pour plus d'informations, consultez [/clr Restrictions](clr-restrictions.md).

Pour plus d’informations sur la façon de développer des applications qui définissent et utilisent des types managés, consultez [Component Extensions for Runtime Platforms](../../extensions/component-extensions-for-runtime-platforms.md).

Une application compilée en utilisant **/clr** peut contenir ou non des données managées.

Pour activer le débogage sur une application managée, consultez [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](assemblydebug-add-debuggableattribute.md).

Seuls les types CLR seront instanciés sur le tas récupéré par le garbage collector. Pour plus d’informations, consultez [les Classes et Structs](../../extensions/classes-and-structs-cpp-component-extensions.md). Pour compiler une fonction en code natif, utilisez le pragma `unmanaged` . Pour plus d’informations, consultez [managed, unmanaged](../../preprocessor/managed-unmanaged.md).

Par défaut, l’option **/clr** n’est pas activée. Quand l’option **/clr** est activée, **/MD** l’est également. Pour plus d’informations, consultez l’article [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](md-mt-ld-use-run-time-library.md). **/MD** garantit que les versions multithreads dynamiquement liées des routines d’exécution sont sélectionnées à partir des fichiers d’en-tête standard (.h). Le multithreading est requis pour la programmation managée, car le garbage collector CLR exécute les finaliseurs dans un thread auxiliaire.

Si vous compilez à l’aide de **/c**, vous pouvez spécifier le type CLR de fichier de sortie résultant avec [CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md).

**/clr** implique **/EHa**et aucune autre option **/EH** n’est prise en charge pour **/clr**. Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](eh-exception-handling-model.md).

Pour plus d’informations sur la façon de déterminer le type d’image CLR d’un fichier, consultez [/CLRHEADER](clrheader.md).

Tous les modules passés à un appel donné de l’éditeur de liens doivent être compilés avec la même option du compilateur de la bibliothèque Runtime (**/MD** ou **/LD**).

Utilisez l'option de l'éditeur de liens [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) pour incorporer une ressource dans un assembly. Les options[/DELAYSIGN](delaysign-partially-sign-an-assembly.md), [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)et [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) de l'éditeur de liens vous permettent également de personnaliser la façon dont un assembly est créé.

Quand l’option **/clr** est utilisée, le symbole `_MANAGED` est défini à 1. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).

Les variables globales dans un fichier objet natif sont initialisées en premier (pendant DllMain si le fichier exécutable est une DLL), puis les variables globales figurant dans la section managée sont initialisées (avant l'exécution de tout code managé). `#pragma` [init_seg](../../preprocessor/init-seg.md) affecte uniquement l’ordre d’initialisation dans les catégories managées et non managées.

## <a name="metadata-and-unnamed-classes"></a>Métadonnées et classes sans nom

Les classes sans nom apparaîtront dans les métadonnées nommées comme suit : `$UnnamedClass$`*crc-nom-fichier-actuel*`$`*index*`$`, où *index* est un compteur séquentiel des classes sans nom dans la compilation. Ainsi, l'exemple de code suivant génère une classe sans nom dans les métadonnées.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

Utilisez ildasm.exe pour afficher les métadonnées.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
