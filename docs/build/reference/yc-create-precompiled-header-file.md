---
title: /Yc (Créer un fichier d'en-tête précompilé)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 0d902b9ebb35bc7f267cb67861b7be0763f378a6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821428"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Créer un fichier d'en-tête précompilé)

Indique au compilateur de créer un fichier d’en-tête précompilé (.pch) qui représente l’état de la compilation à un moment donné.

## <a name="syntax"></a>Syntaxe

> __/Yc__<br/>
> __/Yc__*filename*

## <a name="arguments"></a>Arguments

*filename*<br/>
Spécifie un fichier d’en-tête (.h). Lorsque cet argument est utilisé, le compilateur compile tout le code jusqu'à et y compris le fichier .h.

## <a name="remarks"></a>Notes

Lorsque **/Yc** est spécifiée sans argument, le compilateur compile tout le code jusqu'à la fin du fichier source de base, ou au point dans le fichier de base où un [hdrstop](../../preprocessor/hdrstop.md) directive se produit. Le fichier .pch résultant a le même nom que votre fichier de source de base, sauf si vous spécifiez un nom de fichier différent à l’aide de la **hdrstop** pragma ou **/FP** option.

Le code précompilé est enregistré dans un fichier avec un nom créé à partir du nom de base du fichier spécifié avec le **/Yc** option et une extension .pch. Vous pouvez également utiliser le  [ /fp (nom. Fichier PCH)](fp-name-dot-pch-file.md) option pour spécifier un nom pour le fichier d’en-tête précompilé.

Si vous utilisez __/Yc__*filename*, le compilateur compile tout le code jusqu'à et y compris le fichier spécifié pour une utilisation ultérieure avec le [/Yu (utiliser un fichier d’en-tête précompilé)](yu-use-precompiled-header-file.md) option.

Si les options __/Yc__*filename* et __/Yu__*filename* se produisent sur la même ligne de commande et les deux référence ou impliquent, le même nom de fichier __/Yc__*filename* est prioritaire. Cette fonctionnalité simplifie l’écriture de makefiles.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (En-têtes précompilés)](y-precompiled-headers.md)

- [Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Sélectionnez un fichier .cpp. Le fichier .cpp doit #include le fichier .h qui contient des informations d’en-tête précompilé. Le projet **/Yc** paramètre peut être remplacé au niveau du fichier.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

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

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)
