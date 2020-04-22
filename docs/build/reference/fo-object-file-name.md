---
title: /Fo (Nom de fichier objet)
description: Guide de référence de l’option compilateur Microsoft CMD /Fo (nom de fichier d’objets) dans Visual Studio.
ms.date: 04/20/2020
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748975"
---
# <a name="fo-object-file-name"></a>/Fo (Nom de fichier objet)

Spécifie*`.obj`* un nom de fichier ou un répertoire à utiliser au lieu de la valeur par défaut.

## <a name="syntax"></a>Syntaxe

> **`/Fo`**_Chemin_

## <a name="remarks"></a>Notes

Vous pouvez **`/Fo`** utiliser l’option compilateur pour définir un répertoire de sortie pour tous les fichiers d’objets générés par la commande de compilateur CL. Ou, vous pouvez l’utiliser pour renommer un fichier d’objet unique.

Par défaut, les fichiers d’objets générés par le compilateur sont placés dans l’annuaire actuel. On leur donne le nom de base *`.obj`* du fichier source et une extension.

Pour utiliser **`/Fo`** l’option de renommer un fichier d’objets, spécifiez le nom de fichier de sortie comme argument de *nom de voie.* Lorsque vous renommez un fichier d’objets, vous pouvez utiliser n’importe *`.obj`* quel nom et extension que vous voulez, mais la convention recommandée est d’utiliser . Le compilateur génère l’erreur de ligne de commande D8036 si vous spécifiez un nom de fichier à **`/Fo`** l’endroit où vous avez spécifié plus d’un fichier source à compiler.

Pour utiliser **`/Fo`** l’option de définir un répertoire de sortie pour tous les fichiers d’objets créés par la commande CL, spécifiez l’annuaire comme argument du *nom de voie.* Un répertoire est indiqué par une barre oblique de fuite dans l’argument *du nom de chemin.* L’annuaire spécifié doit exister; il n’est pas créé automatiquement.

## <a name="example"></a>Exemple

La ligne de commande suivante crée un fichier d’objet nommé *sample.obj* dans un répertoire existant, * \\intermédiaire,* sur le disque D.

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Définissez l’option dans Visual Studio ou programmatiquement

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page propriété **Configuration Properties** > **C/CMD** > **Output Files.**

1. Modifier la propriété **Nom du fichier d’objets** pour définir l’annuaire de sortie. Dans l’IDE, le fichier objet *`.obj`* doit avoir une extension de .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
