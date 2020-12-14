---
description: En savoir plus sur:/FM (nom de mappage)
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
ms.openlocfilehash: 5c86a18ae9880a499997bcac2d8411859753d858
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200479"
---
# <a name="fm-name-mapfile"></a>/Fm (Nom de fichier de mappage)

Indique à l’éditeur de liens de produire un fichier de mappage contenant une liste de segments dans l’ordre dans lequel ils apparaissent dans le fichier. exe ou la DLL correspondant.

## <a name="syntax"></a>Syntaxe

```
/Fmpathname
```

## <a name="remarks"></a>Notes

Par défaut, le fichier de mappage reçoit le nom de base du fichier source C ou C++ correspondant avec un. Extension de mappage.

La spécification de **/FM** a le même effet que si vous aviez spécifié l’option de l’éditeur [de liens/Map (générer le mappage)](map-generate-mapfile.md) .

Si vous spécifiez [/c (compiler sans liaison)](c-compile-without-linking.md) pour supprimer la liaison, **/FM** n’a aucun effet.

Les symboles globaux dans un mappage ont généralement un ou plusieurs traits de soulignement de début, car le compilateur ajoute un trait de soulignement de début aux noms de variables. De nombreux symboles globaux qui apparaissent dans le mappage sont utilisés en interne par le compilateur et les bibliothèques standard.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du chemin d’accès](specifying-the-pathname.md)
