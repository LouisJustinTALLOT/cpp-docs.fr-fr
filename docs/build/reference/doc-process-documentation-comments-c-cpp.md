---
description: En savoir plus sur:/doc (traiter les commentaires de documentation) (C/C++)
title: /doc (Traiter les commentaires de documentation) (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
ms.openlocfilehash: ed811edff544c4b5b28baa67ed216fa09ea51092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192874"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Traiter les commentaires de documentation) (C/C++)

Fait en sorte que le compilateur traite les commentaires de documentation dans les fichiers de code source et crée un fichier. XDC pour chaque fichier de code source qui contient des commentaires de documentation.

## <a name="syntax"></a>Syntaxe

> **/doc**[*Name*]

## <a name="arguments"></a>Arguments

*name*<br/>
Nom du fichier. XDC que le compilateur va créer. Valide uniquement lorsqu’un fichier. cpp est passé dans la compilation.

## <a name="remarks"></a>Notes

Les fichiers. XDC sont traités dans un fichier. XML avec xdcmake.exe. Pour plus d’informations, consultez [référence XDCMake](xdcmake-reference.md).

Vous pouvez ajouter des commentaires de documentation à vos fichiers de code source. Pour plus d’informations, consultez [Balises recommandées pour commentaires de documentation](recommended-tags-for-documentation-comments-visual-cpp.md).

Pour utiliser le fichier. XML généré avec IntelliSense, définissez le nom de fichier du fichier. XML de la même façon que l’assembly que vous souhaitez prendre en charge et placez le fichier. xml dans le même répertoire que l’assembly. Lorsque l’assembly est référencé dans le projet Visual Studio, le fichier. xml est également trouvé. Pour plus d’informations, consultez [utilisation d’IntelliSense](/visualstudio/ide/using-intellisense) et spécification de commentaires de [code XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >  fichiers de sortie **C/C++**  >   .

1. Modifiez la propriété **générer des fichiers de documentation XML** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
