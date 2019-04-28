---
title: /J (Type de caractère par défaut non signé)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: ed296d339949814dbd796bb5d8e23a406be71c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269399"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Type de caractère par défaut non signé)

Modifie la valeur par défaut `char` type à partir de `signed char` à `unsigned char`et le `char` type est étendu par zéro lorsqu’il est élargi à un `int` type.

## <a name="syntax"></a>Syntaxe

```
/J
```

## <a name="remarks"></a>Notes

Si un `char` valeur est déclarée explicitement comme `signed`, le **/J** option ne l’affecte pas, et la valeur est étendue avec un signe lorsqu’elle est élargie à un `int` type.

Le **/J** option définit `_CHAR_UNSIGNED`, qui est utilisé avec `#ifndef` dans le fichier LIMITS.h pour définir la plage de la valeur par défaut `char` type.

ANSI C et C++ ne nécessitent pas une implémentation spécifique de la `char` type. Cette option est utile lorsque vous travaillez avec des données de caractères qui seront finalement être converties en une langue autre que l’anglais.

> [!NOTE]
>  Si vous utilisez cette option du compilateur avec ATL/MFC, une erreur peut être générée. Bien que vous pouvez désactiver cette erreur en définissant `_ATL_ALLOW_CHAR_UNSIGNED`, cette solution de contournement n’est pas pris en charge et ne marchent pas toujours.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.

1. Dans le projet **Pages de propriétés** boîte de dialogue, dans le volet gauche sous **propriétés de Configuration**, développez **C/C++** , puis **la ligne de commande**.

1. Dans le **des Options supplémentaires** volet, spécifiez la **/J** option du compilateur.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)
