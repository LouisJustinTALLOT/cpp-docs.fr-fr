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
ms.openlocfilehash: 7bcf0f2eb2bef08757250999d0a6696b256fb15c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322198"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Type de caractère par défaut non signé)

Modifie le `char` type `signed char` `unsigned char`par défaut `char` à partir de , et le `int` type est de zéro-étendu quand il est élargi à un type.

## <a name="syntax"></a>Syntaxe

```
/J
```

## <a name="remarks"></a>Notes

Si `char` une valeur est `signed`explicitement déclarée comme , l’option **/J** ne l’affecte pas, et la valeur est prolongée lorsque le signe est élargi à un `int` type.

**L’option /J** définit `_CHAR_UNSIGNED`, `#ifndef` qui est utilisé avec dans le fichier `char` LIMITS.h pour définir la plage du type par défaut.

L’ANSI C et le CMD n’exigent pas une mise en œuvre spécifique du `char` type. Cette option est utile lorsque vous travaillez avec des données de caractère qui seront éventuellement traduites dans une langue autre que l’anglais.

> [!NOTE]
> Si vous utilisez cette option de compilateur avec ATL/MFC, une erreur peut être générée. Bien que vous puissiez désactiver `_ATL_ALLOW_CHAR_UNSIGNED`cette erreur en définissant, cette solution de contournement n’est pas prise en charge et ne fonctionne pas toujours.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet, puis choisissez **Propriétés**.

1. Dans le projet **Property Pages** boîte de dialogue, dans le volet gauche sous **Configuration Properties**, étendre C / **C et** ensuite sélectionner la ligne **de commandement**.

1. Dans le volet **Options Supplémentaires,** spécifiez l’option de compilateur **/J.**

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md)
