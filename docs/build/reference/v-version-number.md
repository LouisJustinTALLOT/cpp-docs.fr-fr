---
description: En savoir plus sur:/V (numéro de version)
title: /V (Numéro de version)
ms.date: 11/04/2016
f1_keywords:
- /v
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
ms.openlocfilehash: 5025642d4ae30315d24754a7ee46268050cfb22a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187050"
---
# <a name="v-version-number"></a>/V (Numéro de version)

Action déconseillée. Incorpore une chaîne de texte dans le fichier. obj.

## <a name="syntax"></a>Syntaxe

```
/Vstring
```

## <a name="arguments"></a>Arguments

*string*<br/>
Chaîne spécifiant le numéro de version ou la mention de droits d’auteur à incorporer dans un fichier. obj.

## <a name="remarks"></a>Notes

Le stringcan étiquette un fichier. obj avec un numéro de version ou une mention de droits d’auteur. Tout espace ou caractère de tabulation doit être placé entre guillemets doubles (") s’ils font partie de la chaîne. Une barre oblique inverse ( \\ ) doit précéder les guillemets doubles s’ils font partie de la chaîne. Un espace entre **/v** et `string` est facultatif.

Vous pouvez également utiliser [Comment (C/C++)](../../preprocessor/comment-c-cpp.md) avec l’argument de type commentaire du compilateur pour placer le nom et le numéro de version du compilateur dans le fichier. obj.

L’option **/v** est déconseillée à compter de Visual Studio 2005 ; **/V** était principalement utilisé pour prendre en charge la création de pilotes de périphériques virtuels (VxD) et la création de VxD n’est plus prise en charge par l’ensemble d’outils Visual C++. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
