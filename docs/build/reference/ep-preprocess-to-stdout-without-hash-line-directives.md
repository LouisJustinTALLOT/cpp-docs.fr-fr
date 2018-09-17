---
title: '-EP (Prétraiter dans stdout sans directive #line) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598c202cbac0176cb77243c7f0f891ef94c3dcc6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714881"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Prétraiter dans stdout sans directive #line)

Prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.

## <a name="syntax"></a>Syntaxe

```
/EP
```

## <a name="remarks"></a>Notes

Dans le processus, toutes les directives du préprocesseur sont exécutées, les expansions macro sont effectuées et commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez le [/C (conserver les commentaires pendant le prétraitement)](../../build/reference/c-preserve-comments-during-preprocessing.md) option avec **/EP**.

Le **/EP** option supprime la compilation. Vous devez renvoyer le fichier prétraité pour la compilation. **/EP** supprime également les fichiers de sortie à partir de la **/FA**, **/Fa**, et **/Fm** options. Pour plus d’informations, consultez [/FA, /Fa (fichier Listing)](../../build/reference/fa-fa-listing-file.md) et [/Fm (nom de fichier de mappage)](../../build/reference/fm-name-mapfile.md).

Erreurs générées pendant les phases ultérieures du traitement désignent les numéros de ligne du fichier prétraité plutôt que le fichier source d’origine. Si vous souhaitez que les numéros de ligne pour faire référence au fichier source d’origine, utilisez [/E (Prétraiter dans stdout)](../../build/reference/e-preprocess-to-stdout.md) à la place. Le **/E** option ajoute `#line` directives pour la sortie à cet effet.

Pour envoyer la sortie prétraitée, avec `#line` directives, dans un fichier, utilisent le [/P (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) plutôt l’option.

Pour envoyer la sortie prétraitée dans stdout, avec `#line` directives, utilisez **/P** et **/EP** ensemble.

Vous ne pouvez pas utiliser des en-têtes précompilés avec le **/EP** option.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **préprocesseur** page de propriétés.

1. Modifier le **génération du fichier prétraité** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante prétraite le fichier `ADD.C`, conserve les commentaires et affiche le résultat sur le périphérique de sortie standard :

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)