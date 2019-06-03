---
title: /Fp (nom &period;fichier pch)
description: Utilisez l’option de compilateur/FP pour spécifier le nom de fichier d’en-tête précompilé.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460876"
---
# <a name="fp-name-periodpch-file"></a>/Fp (nom &period;fichier pch)

Fournit un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom de chemin d’accès par défaut.

## <a name="syntax"></a>Syntaxe

> **/Fp**<em>pathname</em>

## <a name="remarks"></a>Notes

Utilisez le **/FP** option avec [/Yc (créer un fichier d’en-tête précompilé)](yc-create-precompiled-header-file.md) ou [/Yu (utiliser un en-tête précompilé)](yu-use-precompiled-header-file.md) pour spécifier le chemin d’accès et le nom de l’en-tête précompilé (PCH) fichier. Par défaut, le **/Yc** option permet de créer un nom de fichier d’en-tête Précompilé en utilisant le nom de base du fichier source et un *pch* extension.

Si vous ne spécifiez pas une extension dans le cadre de la *pathname*, une extension de *pch* est supposé. Lorsque vous spécifiez un nom de répertoire à l’aide d’une barre oblique ( **/** ) à la fin de *pathname*, le nom de fichier par défaut est vc*version*0.pch, où  *version* est la version principale de l’ensemble d’outils de Visual Studio. Ce répertoire doit exister, ou erreur C1083 est générée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez le **propriétés de Configuration** > **C /C++**  > **en-têtes précompilés** page de propriétés.

1. Modifier le **fichier de sortie d’en-tête précompilé** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Exemples

Pour créer un distinct nommé version du fichier d’en-tête précompilé pour la version debug de votre programme, vous pouvez spécifier une commande telle que :

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

La commande suivante spécifie l’utilisation d’un fichier d’en-tête précompilé nommé MYPCH.pch. Le compilateur précompile le code source dans PROG.cpp jusqu'à la fin de MYAPP.h et place le code précompilé dans MYPCH.pch. Il utilise le contenu de MYPCH.pch et compile le reste de PROG.cpp pour créer un fichier .obj. La sortie de cet exemple est un fichier nommé PROG.exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
