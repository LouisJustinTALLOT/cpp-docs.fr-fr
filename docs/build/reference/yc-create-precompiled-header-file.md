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
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825754"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Créer un fichier d'en-tête précompilé)

Indique au compilateur de créer un fichier d’en-tête précompilé (. pch) qui représente l’état de la compilation à un moment donné.

## <a name="syntax"></a>Syntaxe

> __/YC__\
> __/Yc__*nom de fichier*

## <a name="arguments"></a>Arguments

*extension*<br/>
Spécifie un fichier d’en-tête (. h). Lorsque cet argument est utilisé, le compilateur compile tout le code jusqu’au fichier. h, y compris.

## <a name="remarks"></a>Notes 

Lorsque **/Yc** est spécifié sans argument, le compilateur compile tout le code jusqu’à la fin du fichier source de base, ou jusqu’au point du fichier de base où une directive [hdrstop](../../preprocessor/hdrstop.md) se produit. Le fichier. pch résultant a le même nom de base que votre fichier source de base, sauf si vous spécifiez un autre nom de fichier à l’aide du pragma **hdrstop** ou de l’option **/FP** .

Le code précompilé est enregistré dans un fichier avec un nom créé à partir du nom de base du fichier spécifié avec l’option **/Yc** et une extension. pch. Vous pouvez également utiliser le [nom de la. Fichier PCH)](fp-name-dot-pch-file.md) pour spécifier un nom pour le fichier d’en-tête précompilé.

Si vous utilisez __/Yc__*filename*, le compilateur compile tout le code jusqu’à et y compris le fichier spécifié pour une utilisation ultérieure avec l’option [/Yu (utiliser un fichier d’en-tête précompilé)](yu-use-precompiled-header-file.md) .

Si les options __/Yc__*filename* et __/Yu__*filename* se trouvent sur la même ligne de commande et qu’elles référencent, ou impliquent, le même nom de fichier, __/Yc__*filename* est prioritaire. Cette fonctionnalité simplifie l’écriture de makefiles.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (En-têtes précompilés)](y-precompiled-headers.md)

- [Fichiers d'en-tête précompilés](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Sélectionnez un fichier. cpp. Le fichier. cpp doit #include le fichier. h qui contient les informations d’en-tête précompilé. Le paramètre **/Yc** du projet peut être substitué au niveau du fichier.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez la page de propriétés **Propriétés de configuration**, **C/C++**, **en-têtes précompilés** .

1. Modifiez la propriété d' **en-tête précompilé** .

1. Pour définir le nom de fichier, modifiez la propriété **fichier d’en-tête précompilé** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Localisez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a> Exemple

Examinons le code ci-dessous.

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Quand ce code est compilé avec la commande `CL /YcMYAPP.H PROG.CPP`, le compilateur enregistre tout le prétraitement pour AFXWIN. h, Resource. h et MyApp. h dans un fichier d’en-tête précompilé nommé MyApp. pch.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Fichiers d'en-tête précompilés](../creating-precompiled-header-files.md)
