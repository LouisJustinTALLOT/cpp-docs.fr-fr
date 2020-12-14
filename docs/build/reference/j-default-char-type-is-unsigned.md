---
description: En savoir plus sur:/J (type de caractère par défaut non signé)
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
ms.openlocfilehash: 0e6f09a05925fd0248f1e777d578570cd7b44946
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191223"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Type de caractère par défaut non signé)

Modifie le type par défaut **`char`** de **`signed char`** en **`unsigned char`** , et le **`char`** type est étendu par zéro lorsqu’il est élargi à un **`int`** type.

## <a name="syntax"></a>Syntaxe

```
/J
```

## <a name="remarks"></a>Notes

Si une **`char`** valeur est déclarée explicitement comme **`signed`** , l’option **/j** ne l’affecte pas, et la valeur est étendue par un signe lorsqu’elle est élargie à un **`int`** type.

L’option **/j** définit `_CHAR_UNSIGNED` , qui est utilisé avec `#ifndef` dans le fichier limits. h pour définir la plage du type par défaut **`char`** .

ANSI C et C++ n’ont pas besoin d’une implémentation spécifique du **`char`** type. Cette option est utile lorsque vous travaillez avec des données de caractères qui seront finalement traduites dans une langue autre que l’anglais.

> [!NOTE]
> Si vous utilisez cette option du compilateur avec ATL/MFC, une erreur peut être générée. Bien que vous puissiez désactiver cette erreur en définissant `_ATL_ALLOW_CHAR_UNSIGNED` , cette solution de contournement n’est pas prise en charge et ne fonctionnera peut-être pas toujours.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** du projet, dans le volet gauche, sous **Propriétés de configuration**, développez **C/C++** , puis sélectionnez **ligne de commande**.

1. Dans le volet **options supplémentaires** , spécifiez l’option du compilateur **/j** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)
