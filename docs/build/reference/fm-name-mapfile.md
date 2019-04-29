---
title: /Fm (Nom de fichier de mappage)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: eebb1bc0c553dba1934aea75e2e63edc0f222fff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292404"
---
# <a name="fm-name-mapfile"></a>/Fm (Nom de fichier de mappage)

Indique à l’éditeur de liens pour produire un fichier de mappage contenant une liste de segments dans l’ordre dans lequel ils apparaissent dans le fichier .exe correspondant ou la DLL.

## <a name="syntax"></a>Syntaxe

```
/Fmpathname
```

## <a name="remarks"></a>Notes

Par défaut, le fichier de mappage reçoit le nom de base du fichier source C ou C++ correspondant avec un. Extension de carte.

Spécification **/Fm** a le même effet que si vous aviez spécifié la [/MAP (générer fichier de mappage)](map-generate-mapfile.md) option de l’éditeur de liens.

Si vous spécifiez [/c (compiler sans liaison)](c-compile-without-linking.md) pour supprimer la liaison, **/Fm** n’a aucun effet.

Symboles globaux dans un fichier de mappage ont généralement un ou plusieurs principaux des traits de soulignement, car le compilateur ajoute un trait de soulignement pour les noms de variables. De nombreux symboles globaux qui s’affichent dans le fichier de mappage sont utilisés en interne par le compilateur et les bibliothèques standards.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
