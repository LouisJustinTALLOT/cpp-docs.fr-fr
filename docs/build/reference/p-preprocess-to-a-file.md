---
description: En savoir plus sur:/P (Prétraiter dans un fichier)
title: /P (Prétraiter jusqu'à un fichier)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 20bca03694c866baa0575445271fc4f587268096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226192"
---
# <a name="p-preprocess-to-a-file"></a>/P (Prétraiter jusqu'à un fichier)

Prétraite les fichiers sources C et C++ et écrit la sortie prétraitée dans un fichier.

## <a name="syntax"></a>Syntaxe

```
/P
```

## <a name="remarks"></a>Notes

Le fichier a le même nom de base que le fichier source et une extension. i. Dans le processus, toutes les directives de préprocesseur sont exécutées, les expansions de macro sont effectuées et les commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez l’option [/c (conserver les commentaires pendant le prétraitement)](c-preserve-comments-during-preprocessing.md) avec **/p**.

**/P** ajoute des `#line` directives à la sortie, au début et à la fin de chaque fichier inclus et autour des lignes supprimées par les directives de préprocesseur pour la compilation conditionnelle. Ces directives renumérotent les lignes du fichier prétraité. Par conséquent, les erreurs générées lors des étapes ultérieures de traitement font référence aux numéros de ligne du fichier source d’origine plutôt qu’aux lignes du fichier prétraité. Pour supprimer la génération de `#line` directives, utilisez [/EP (Prétraiter dans stdout sans directives #line)](ep-preprocess-to-stdout-without-hash-line-directives.md) , ainsi que **/p**.

L’option **/p** supprime la compilation. Elle ne produit pas de fichier. obj, même si vous utilisez [/FO (nom du fichier objet)](fo-object-file-name.md). Vous devez soumettre à nouveau le fichier prétraité pour la compilation. **/P** supprime également les fichiers de sortie des options **/FA**, **/FA** et **/FM** . Pour plus d’informations, consultez [/FA,/FA (liste de fichiers)](fa-fa-listing-file.md) et [/FM (nom de fichier de mappage)](fm-name-mapfile.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés du **préprocesseur** .

1. Modifiez la propriété **générer le fichier prétraité** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante prétraite `ADD.C` , conserve les commentaires, ajoute des `#line` directives et écrit le résultat dans un fichier `ADD.I` :

```
CL /P /C ADD.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/FI (prétraiter le nom du fichier de sortie)](fi-preprocess-output-file-name.md)
