---
title: -/CLR (Compilation pour le Common Language Runtime) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1284d0300fcea3adc5f2884a7d1eff7862ff2b65
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379612"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Compilation pour le Common Language Runtime)
Permet aux applications et aux composants d’utiliser les fonctionnalités du Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>Arguments  
 `options`  
 Un ou plusieurs des commutateurs suivants, séparés par des virgules.  
  
 **/clr**  
 Crée des métadonnées pour l'application. Ces métadonnées peuvent être utilisées par d'autres applications CLR et permettent à votre application d'utiliser les types et données des métadonnées appartenant à d'autres composants CLR.  
  
 Pour plus d'informations, consultez  
  
 [Mixte (natifs et managés) assemblys](../../dotnet/mixed-native-and-managed-assemblies.md) et  
  
 [How to: Migrate to /clr](../../dotnet/how-to-migrate-to-clr.md).  
  
 **/clr:pure**  
 /clr:pure est déconseillé. Une prochaine version du compilateur risque de ne plus prendre en charge cette option. Nous vous recommandons de porter vers C# du code devant être écrit en MSIL pur.  
  
 **/clr:safe**  
 /clr:safe est déconseillé. Une prochaine version du compilateur risque de ne plus prendre en charge cette option. Nous vous recommandons de porter du code doit être MSIL sécurisé en c#. 
  
 **/clr:noAssembly**  
 Indique qu'un manifeste d'assembly ne doit pas être inséré dans le fichier de sortie. Par défaut, l’option **noAssembly** n’est pas activée.  
  
 L’option **noAssembly** est déconseillée. Utilisez plutôt [/LN (Create MSIL Module)](../../build/reference/ln-create-msil-module.md) .  
  
 Un programme managé qui ne possède pas de métadonnées d'assembly dans le manifeste est appelé *module*. L’option **noAssembly** peut être utilisée uniquement pour produire un module. Si vous compilez en utilisant [/c](../../build/reference/c-compile-without-linking.md) et **/clr:noAssembly**, spécifiez l’option [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) dans la phase de l’éditeur de liens pour créer un module.  
  
 Avant Visual C++ 2005, **/clr:noAssembly** nécessitait l’option **/LD**. **/LD** est désormais implicite quand vous spécifiez **/clr:noAssembly**.  
  
 **/clr:initialAppDomain**  
 Permet à une application [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] de s'exécuter sur la version 1 du CLR. Si vous utilisez **initialAppDomain**, vous pouvez voir certains des problèmes mentionnés dans [bogue : exception AppDomainUnloaded lorsque vous utilisez des extensions managées pour des composants Visual C++](http://go.microsoft.com/fwlink/p/?linkid=169465) sur Microsoft Site Web du support technique.  
  
 Une application compilée en utilisant **initialAppDomain** ne doit pas être utilisée par une application qui utilise ASP.NET car elle n’est pas prise en charge dans la version 1 du CLR.  
  
 **/clr:nostdlib**  
 Indique au compilateur d'ignorer le répertoire \clr par défaut. Le compilateur produit des erreurs si vous incluez plusieurs versions d'une DLL telle que System.dll. Cette option vous permet de spécifier l'infrastructure spécifique à utiliser pendant la compilation.  
  
## <a name="remarks"></a>Notes  
 Le code managé est du code qui peut être inspecté et géré par le CLR. Le code managé peut accéder aux objets managés. Pour plus d'informations, consultez [/clr Restrictions](../../build/reference/clr-restrictions.md).  
  
 Pour plus d’informations sur la façon de développer des applications qui définissent et utilisent des types managés, consultez [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Une application compilée en utilisant **/clr** peut contenir ou non des données managées.  
  
 Pour activer le débogage sur une application managée, consultez [/ASSEMBLYDEBUG (Ajouter DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md).  
  
 Seuls les types CLR seront instanciés sur le tas récupéré par le garbage collector. Pour plus d’informations, consultez [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md). Pour compiler une fonction en code natif, utilisez le pragma `unmanaged` . Pour plus d’informations, consultez [managé, non managé](../../preprocessor/managed-unmanaged.md).  
  
 Par défaut, l’option **/clr** n’est pas activée. Quand l’option **/clr** est activée, **/MD** l’est également. Pour plus d’informations, consultez l’article [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md). **/MD** garantit que les versions multithreads dynamiquement liées des routines d’exécution sont sélectionnées à partir des fichiers d’en-tête standard (.h). Le multithreading est requis pour la programmation managée, car le garbage collector CLR exécute les finaliseurs dans un thread auxiliaire.  
  
 Si vous compilez à l’aide de **/c**, vous pouvez spécifier le type CLR du fichier de sortie résultant avec [CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
 **/clr** implique **/EHa**et aucune autre option **/EH** n’est prise en charge pour **/clr**. Pour plus d’informations, consultez l’article [/EH (Modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md).  
  
 Pour plus d’informations sur la façon de déterminer le type d’image CLR d’un fichier, consultez [/CLRHEADER](../../build/reference/clrheader.md).  
  
 Tous les modules passés à un appel donné de l’éditeur de liens doivent être compilés avec la même option du compilateur de la bibliothèque Runtime (**/MD** ou **/LD**).  
  
 Utilisez l'option de l'éditeur de liens [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) pour incorporer une ressource dans un assembly. Les options[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)et [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) de l'éditeur de liens vous permettent également de personnaliser la façon dont un assembly est créé.  
  
 Quand l’option **/clr** est utilisée, le symbole `_MANAGED` est défini à 1. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).  
  
 Les variables globales dans un fichier objet natif sont initialisées en premier (pendant DllMain si le fichier exécutable est une DLL), puis les variables globales figurant dans la section managée sont initialisées (avant l'exécution de tout code managé). `#pragma`[init_seg](../../preprocessor/init-seg.md) affecte uniquement l’ordre d’initialisation dans les catégories managées et non managées.  
  
## <a name="metadata-and-unnamed-classes"></a>Métadonnées et classes sans nom  
 Les classes sans nom apparaîtront dans les métadonnées nommées comme suit : `$UnnamedClass$`*crc-nom-fichier-actuel*`$`*index*`$`, où *index* est un compteur séquentiel des classes sans nom dans la compilation. Ainsi, l'exemple de code suivant génère une classe sans nom dans les métadonnées.  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 Utilisez ildasm.exe pour afficher les métadonnées.  
  
## <a name="managed-extensions-for-c"></a>Extensions managées pour C++  
 Visual C++ ne prend plus en charge l’option **/clr:oldsyntax** . Cette option était déconseillée dans Visual Studio 2015. La syntaxe prise en charge pour l'écriture de code managé en C++ est C++/CLI. Pour plus d'informations, consultez [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Si vous possédez du code qui utilise les extensions managées pour C++, nous vous recommandons de le porter pour utiliser la syntaxe C++/CLI. Pour plus d’informations sur la façon de porter votre code, consultez [C++/CLI Migration Primer](../../dotnet/cpp-cli-migration-primer.md).  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés** du projet.  
  
2.  Sélectionnez le dossier **Propriétés de configuration** .  
  
3.  Dans la page de propriétés **Général** , modifiez la propriété **Prise en charge du Common Language Runtime** .  
  
    > [!NOTE]
    >  Quand l’option **/clr** est activée dans la boîte de dialogue **Pages de propriétés** , les propriétés des options du compilateur qui ne sont pas compatibles avec **/clr** sont également ajustées selon les besoins. Par exemple, si l’option **/RTC** est définie, puis l’option **/clr** activée, l’option **/RTC** est désactivée.  
    >   
    >  De plus, quand vous déboguez une application **/clr** , affectez à la propriété **Type de débogueur** la valeur **Mixte** ou **Managé uniquement**. Pour plus d’informations, consultez [paramètres de projet pour une Configuration Debug C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration).  
  
     Pour plus d’informations sur la façon de créer un module, consultez [/NOASSEMBLY (créer un Module MSIL)](../../build/reference/noassembly-create-a-msil-module.md).  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)