---
title: -Fp (nom. Aucun fichier PCH) | Documents Microsoft
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
ms.openlocfilehash: 80f59477695b83b33dd3cfa2b37837c5b52c8002
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376330"
---
# <a name="fp-name-pch-file"></a>/Fp (Nom de fichier .pch)
Fournit un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom de chemin d’accès par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
> **/ Fp**_chemin d’accès_  
  
## <a name="remarks"></a>Notes  
 Utilisez cette option avec [/Yc (créer un en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) ou [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) pour fournir un nom de chemin d’accès pour un en-tête précompilé au lieu d’utiliser le nom de chemin d’accès par défaut. Vous pouvez également utiliser **/FP** avec **/Yc** pour spécifier l’utilisation d’un fichier d’en-tête précompilé qui diffère de la **/Yc *** filename* argument et le nom de base du fichier source.  
  
 Si vous ne spécifiez pas une extension en tant que partie du nom de chemin d’accès, une extension .pch est supposée. Si vous spécifiez un répertoire sans nom de fichier, le nom de fichier par défaut est VC*x*0.pch, où *x* est la version principale de Visual C++ en cours d’utilisation.  
  
 Vous pouvez également utiliser le **/FP** option avec **/Yu**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **les en-têtes précompilés** page de propriétés.  
  
4.  Modifier la **fichier d’en-tête précompilé** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.  
  
## <a name="example"></a>Exemple  
 Si vous souhaitez créer un fichier d’en-tête précompilé pour une version de débogage de votre programme et que vous compilez les fichiers d’en-tête et le code source, vous pouvez spécifier une commande telle que :  
  
```  
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP  
```  
  
## <a name="example"></a>Exemple  
 La commande suivante spécifie l’utilisation d’un fichier d’en-tête précompilé nommé MYPCH.pch. Le compilateur suppose que le code source dans PROG.cpp a été précompilé par MYAPP.h et que le code précompilé réside dans MYPCH.pch. Il utilise le contenu de MYPCH.pch et compile le reste de PROG.cpp pour créer un fichier .obj. La sortie de cet exemple est un fichier nommé PROG.exe.  
  
```  
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)