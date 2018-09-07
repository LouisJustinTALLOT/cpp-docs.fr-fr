---
title: -doc (traiter les commentaires de Documentation) (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee09b3fe61c86015d8dc7464ef9925419fc745d9
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100325"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Traiter les commentaires de documentation) (C/C++)
Indique au compilateur de traiter les commentaires de documentation dans les fichiers de code source et pour créer un fichier .xdc pour chaque fichier de code source qui a des commentaires de documentation.

## <a name="syntax"></a>Syntaxe

> **/doc**[*nom*]

## <a name="arguments"></a>Arguments

*name*<br/>
Le nom du fichier .xdc que le compilateur va créer. Valide uniquement lorsqu’un fichier .cpp est passé dans la compilation.

## <a name="remarks"></a>Notes

Les fichiers .xdc sont traités dans un fichier .xml avec xdcmake.exe. Pour plus d’informations, consultez [XDCMake référence](../../ide/xdcmake-reference.md).

Vous pouvez ajouter des commentaires de documentation à vos fichiers de code source. Pour plus d’informations, consultez [balises recommandées pour commentaires de Documentation](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).

Pour utiliser le fichier .xml généré avec IntelliSense, vérifiez le nom de fichier du fichier .xml est de même que l’assembly que vous souhaitez prendre en charge et placez le fichier .xml dans le même répertoire que l’assembly. Lorsque l’assembly est référencé dans le projet Visual Studio, le fichier .xml est également trouvé. Pour plus d’informations, consultez [IntelliSense à l’aide de](/visualstudio/ide/using-intellisense) et [insertion de commentaires de Code XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **fichiers de sortie** page de propriétés.

1. Modifier le **générer des fichiers de Documentation XML** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)