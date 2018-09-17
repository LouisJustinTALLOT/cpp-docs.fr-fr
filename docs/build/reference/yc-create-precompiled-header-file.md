---
title: -Yc (créer le fichier d’en-tête précompilé) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5288e748956a405073697ddd7331a73b95d8650
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714244"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Créer un fichier d’en-tête précompilé)

Indique au compilateur de créer un fichier d’en-tête précompilé (.pch) qui représente l’état de la compilation à un moment donné.

## <a name="syntax"></a>Syntaxe

> __/Yc__
>  __/Yc__*nom de fichier*

## <a name="arguments"></a>Arguments

*filename*<br/>
Spécifie un fichier d’en-tête (.h). Lorsque cet argument est utilisé, le compilateur compile tout le code jusqu'à et y compris le fichier .h.

## <a name="remarks"></a>Notes

Lorsque **/Yc** est spécifiée sans argument, le compilateur compile tout le code jusqu'à la fin du fichier source de base, ou au point dans le fichier de base où un [hdrstop](../../preprocessor/hdrstop.md) directive se produit. Le fichier .pch résultant a le même nom que votre fichier de source de base, sauf si vous spécifiez un nom de fichier différent à l’aide de la **hdrstop** pragma ou **/FP** option.

Le code précompilé est enregistré dans un fichier avec un nom créé à partir du nom de base du fichier spécifié avec le **/Yc** option et une extension .pch. Vous pouvez également utiliser le  [ /fp (nom. Fichier PCH)](../../build/reference/fp-name-dot-pch-file.md) option pour spécifier un nom pour le fichier d’en-tête précompilé.

Si vous utilisez __/Yc__*filename*, le compilateur compile tout le code jusqu'à et y compris le fichier spécifié pour une utilisation ultérieure avec le [/Yu (utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) option.

Si les options __/Yc__*filename* et __/Yu__*filename* se produisent sur la même ligne de commande et les deux référence ou impliquent, le même nom de fichier __/Yc__*filename* est prioritaire. Cette fonctionnalité simplifie l’écriture de makefiles.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (En-têtes précompilés)](../../build/reference/y-precompiled-headers.md)

- [Création de fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Sélectionnez un fichier .cpp. Le fichier .cpp doit #include le fichier .h qui contient des informations d’en-tête précompilé. Le projet **/Yc** paramètre peut être remplacé au niveau du fichier.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Ouvrez le **propriétés de Configuration**, **C/C++**, **en-têtes précompilés** page de propriétés.

1. Modifier le **en-tête précompilé** propriété.

1. Pour définir le nom de fichier, modifiez le **fichier d’en-tête précompilé** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Exemple

Examinons le code ci-dessous.

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Lorsque ce code est compilé avec la commande `CL /YcMYAPP.H PROG.CPP`, le compilateur enregistre tout le prétraitement pour AFXWIN.h, RESOURCE.h et MYAPP.h dans un fichier d’en-tête précompilé appelé MYAPP.pch.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Création de fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md)