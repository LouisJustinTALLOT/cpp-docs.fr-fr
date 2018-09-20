---
title: -Fp (nom. Fichier PCH) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a851f93ae845d56b9c986e822e94970ad5cccd5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427132"
---
# <a name="fp-name-pch-file"></a>/Fp (Nom de fichier .pch)

Fournit un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom de chemin d’accès par défaut.

## <a name="syntax"></a>Syntaxe

> **/ Fp**<em>chemin d’accès</em>

## <a name="remarks"></a>Notes

Utilisez cette option avec [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) ou [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) pour fournir un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom de chemin d’accès par défaut. Vous pouvez également utiliser **/FP** avec **/Yc** pour spécifier l’utilisation d’un fichier d’en-tête précompilé qui diffère la **/Yc**<em>filename</em> argument et le nom de base du fichier source.

Si vous ne spécifiez pas une extension en tant que partie du nom de chemin d’accès, une extension .pch est supposée. Si vous spécifiez un répertoire sans nom de fichier, le nom de fichier par défaut est VC*x*0.pch, où *x* est la version principale de Visual C++ en cours d’utilisation.

Vous pouvez également utiliser le **/FP** option avec **/Yu**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **en-têtes précompilés** page de propriétés.

1. Modifier le **fichier d’en-tête précompilé** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.

## <a name="example"></a>Exemple

Si vous souhaitez créer un fichier d’en-tête précompilé pour une version de débogage de votre programme et que vous compilez les fichiers d’en-tête et le code source, vous pouvez spécifier une commande telles que :

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>Exemple

La commande suivante spécifie l’utilisation d’un fichier d’en-tête précompilé nommé MYPCH.pch. Le compilateur suppose que le code source dans PROG.cpp a été précompilé par MYAPP.h et que le code précompilé réside dans MYPCH.pch. Il utilise le contenu de MYPCH.pch et compile le reste de PROG.cpp pour créer un fichier .obj. La sortie de cet exemple est un fichier nommé PROG.exe.

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](../../build/reference/output-file-f-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)