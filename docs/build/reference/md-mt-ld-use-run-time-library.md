---
title: -MD, -MT, -LD (utiliser la bibliothèque Runtime) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
dev_langs:
- C++
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee8e59fbc88e63343d4da75a4cbf95d4f83bf815
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701361"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (Utiliser la bibliothèque Runtime)

Indique si un module multithread est une DLL et spécifie les versions retail ou debug de la bibliothèque Runtime.

## <a name="syntax"></a>Syntaxe

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Notes

|Option|Description|
|------------|-----------------|
|**/MD**|Indique à l'application d'utiliser la version multithread spécifique à la DLL de la bibliothèque Runtime. Définit `_MT` et `_DLL`, puis indique au compilateur de placer le nom de la bibliothèque MSVCRT.lib dans le fichier .obj.<br /><br /> Les applications compilées avec cette option sont liées de manière statique à MSVCRT.lib. Cette bibliothèque fournit une couche de code qui permet à l'éditeur de liens de résoudre des références externes. Le code de travail effectif est contenu dans MSVCR*versionnumber*. DLL, qui doit être disponible au moment de l’exécution pour les applications liées avec MSVCRT.lib.|
|**/MDd**|Définit `_DEBUG`, `_MT` et `_DLL`, puis indique à l'application d'utiliser la version debug multithread spécifique à la DLL de la bibliothèque Runtime. Le compilateur place également le nom de la bibliothèque MSVCRTD.lib dans le fichier .obj.|
|**/MT**|Indique à l'application d'utiliser la version statique multithread de la bibliothèque Runtime. Définit `_MT` et indique au compilateur de placer le nom de la bibliothèque LIBCMT.lib dans le fichier .obj de façon à ce que l'éditeur de liens utilise LIBCMT.lib pour résoudre les symboles externes.|
|**/MTd**|Définit `_DEBUG` et `_MT`. Cette option indique également au compilateur d'ajouter le nom de bibliothèque LIBCMTD.lib dans le fichier .obj afin que l'Éditeur de liens utilise LIBCMTD.lib pour résoudre les symboles externes.|
|**/LD**|Crée une DLL.<br /><br /> Transmet le **/DLL** option à l’éditeur de liens. L'éditeur de liens recherche, mais n'exige pas, une fonction `DllMain`. Si vous n'écrivez pas de fonction `DllMain`, l'éditeur de liens insère une fonction `DllMain` qui retourne TRUE.<br /><br /> Lie le code de démarrage de la DLL.<br /><br /> Crée une bibliothèque d'importation (.lib), si aucun fichier d'exportation (.exp) n'est spécifié sur la ligne de commande. Vous liez la bibliothèque d'importation aux applications qui appellent votre DLL.<br /><br /> Interprète [/Fe (nom de fichier EXE)](../../build/reference/fe-name-exe-file.md) que de nommer une DLL plutôt qu’un fichier .exe. Par défaut, le nom du programme devient *basename*.dll au lieu de *basename*.exe.<br /><br /> Implique **/MT** , sauf si vous spécifiez explicitement **/MD**.|
|**/LDd**|Crée une DLL de débogage. Définit `_MT` et `_DEBUG`.|

Pour plus d’informations sur les bibliothèques Runtime C et les bibliothèques qui sont utilisées lorsque vous compilez avec [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), consultez [fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

Tous les modules passés à un appel donné de l’éditeur de liens doivent avoir été compilés avec la même option du compilateur de bibliothèque du run-time (**/MD**, **/MT**, **/LD**).

Pour plus d’informations sur la façon d’utiliser les versions debug des bibliothèques Runtime, consultez [C Run-Time Library Reference](../../c-runtime-library/c-run-time-library-reference.md).

L'article de la Base de connaissances Q140584 indique également comment choisir la bibliothèque Runtime C appropriée.

Pour plus d’informations sur les DLL, consultez [DLL dans Visual C++](../../build/dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le **C/C++** dossier.

1. Sélectionnez le **génération de Code** page de propriétés.

1. Modifier le **bibliothèque Runtime** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)