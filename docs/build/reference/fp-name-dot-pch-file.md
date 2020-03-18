---
title: /FP (nom &period;fichier PCH)
description: Utilisez l’option du compilateur/FP pour spécifier le nom du fichier d’en-tête précompilé.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
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
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439785"
---
# <a name="fp-name-periodpch-file"></a>/FP (nom &period;fichier PCH)

Fournit un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom de chemin d’accès par défaut.

## <a name="syntax"></a>Syntaxe

> **/Fp**<em>Nom de chemin d’accès</em> /FP

## <a name="remarks"></a>Notes

Utilisez l’option **/FP** avec [/Yc (créer un fichier d’en-tête précompilé)](yc-create-precompiled-header-file.md) ou [/Yu (utiliser un fichier d’en-tête précompilé)](yu-use-precompiled-header-file.md) pour spécifier le chemin d’accès et le nom de fichier du fichier d’en-tête précompilé (PCH). Par défaut, l’option **/Yc** crée un nom de fichier PCH en utilisant le nom de base du fichier source et une extension *PCH* .

Si vous ne spécifiez pas d’extension dans le *chemin d’accès*, une extension de *PCH* est utilisée. Lorsque vous spécifiez un nom de répertoire à l’aide d’une barre oblique ( **/** ) à la fin du *chemin d’accès*, le nom de fichier par défaut est VC*version*0. pch, où *version* est la version principale de l’ensemble d’outils Visual Studio. Ce répertoire doit exister, ou l’erreur C1083 est générée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez la page de propriétés **Propriétés de configuration** > **en-têtes précompilés** **C/C++**  > .

1. Modifiez la propriété **fichier d’en-tête précompilé de sortie** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Exemples

Pour créer une version nommée distincte du fichier d’en-tête précompilé pour la version Debug de votre programme, vous pouvez spécifier une commande telle que :

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

La commande suivante spécifie l’utilisation d’un fichier d’en-tête précompilé nommé MYPCH. pch. Le compilateur précompile le code source dans PROG. cpp à la fin de MYAPP. h et place le code précompilé dans MYPCH. pch. Il utilise ensuite le contenu de MYPCH. pch et compile le reste de PROG. cpp pour créer un fichier. obj. La sortie de cet exemple est un fichier nommé PROG. exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
