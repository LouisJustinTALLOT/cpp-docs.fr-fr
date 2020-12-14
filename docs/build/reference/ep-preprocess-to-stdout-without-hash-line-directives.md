---
description: 'En savoir plus sur:/EP (Prétraiter dans stdout sans directives #line)'
title: '/EP (Prétraiter dans stdout sans directive #line)'
ms.date: 11/04/2016
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
ms.openlocfilehash: cbd36cd6bdafe315a7a6ef01b46857725033bd69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200999"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Prétraiter dans stdout sans directive #line)

Prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.

## <a name="syntax"></a>Syntaxe

```
/EP
```

## <a name="remarks"></a>Notes

Dans le processus, toutes les directives de préprocesseur sont exécutées, les expansions de macro sont effectuées et les commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez l’option [/c (conserver les commentaires pendant le prétraitement)](c-preserve-comments-during-preprocessing.md) avec **/EP**.

L’option **/EP** supprime la compilation. Vous devez soumettre à nouveau le fichier prétraité pour la compilation. **/EP** supprime également les fichiers de sortie des options **/FA**, **/FA** et **/FM** . Pour plus d’informations, consultez [/FA,/FA (liste de fichiers)](fa-fa-listing-file.md) et [/FM (nom de fichier de mappage)](fm-name-mapfile.md).

Les erreurs générées lors des étapes ultérieures de traitement font référence aux numéros de ligne du fichier prétraité plutôt qu’au fichier source d’origine. Si vous souhaitez que les numéros de ligne fassent référence au fichier source d’origine, utilisez [/e (Prétraiter dans stdout)](e-preprocess-to-stdout.md) à la place. L’option **/e** ajoute `#line` des directives à la sortie à cet effet.

Pour envoyer la sortie prétraitée, avec des `#line` directives, à un fichier, utilisez à la place l’option [/p (Prétraiter dans un fichier)](p-preprocess-to-a-file.md) .

Pour envoyer la sortie prétraitée à stdout, avec les `#line` directives, utilisez **/P** et **/EP** ensemble.

Vous ne pouvez pas utiliser d’en-têtes précompilés avec l’option **/EP** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés du **préprocesseur** .

1. Modifiez la propriété **générer le fichier prétraité** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante prétraite le fichier `ADD.C` , conserve les commentaires et affiche le résultat sur le périphérique de sortie standard :

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
