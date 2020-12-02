---
title: /FA, /Fa (Fichier listing)
description: Guide de référence de l’option du compilateur Microsoft C++/FA et/FA (fichier listing).
ms.date: 11/21/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.openlocfilehash: 7e8e39fea55bb69eaa0ae914eeabcafef4ac7849
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440239"
---
# <a name="fa-fa-listing-file"></a>`/FA`, `/Fa` (Fichier listing)

Crée un fichier listing contenant du code assembleur.

## <a name="syntax"></a>Syntaxe

> **`/FA`**[**`c`**\][**`s`**\][**`u`**]\
> **`/Fa`**_chemin_

## <a name="remarks"></a>Remarques

L' **`/FA`** option de compilateur génère un fichier d’énumération assembleur pour chaque unité de traduction dans la compilation, qui correspond généralement à un fichier source C ou C++. Par défaut, seul l’assembleur est inclus dans le fichier de liste, qui est encodé au format ANSI. Les **`c`** arguments, **`s`** et facultatifs **`u`** pour **`/FA`** contrôler si le code machine ou le code source sont générés avec la liste de l’assembleur, et si la liste est encodée au format UTF-8.

Par défaut, chaque fichier listing reçoit le même nom de base que le fichier source et a une *`.asm`* extension. Lorsque le code machine est inclus à l’aide de l' **`c`** option, le fichier listing a une *`.cod`* extension. Vous pouvez modifier le nom et l’extension du fichier listing et le répertoire dans lequel il est créé à l’aide de l' **`/Fa`** option.

### <a name="fa-arguments"></a>`/FA` arguments

None
Seule la langue de l’assembleur est incluse dans la liste.

**`c`**\
Optionnel. Comprend le code machine dans la liste.

**`s`**\
Optionnel. Comprend le code source dans la liste.

**`u`**\
Optionnel. Encode le fichier listing au format UTF-8 et comprend un marqueur d’ordre d’octet. Par défaut, le fichier est encodé au format ANSI. Utilisez **`u`** pour créer un fichier listing qui s’affiche correctement sur tout système ou si vous utilisez des fichiers de code source Unicode comme entrée pour le compilateur.

Si **`s`** et **`u`** sont spécifiés, et si un fichier de code source utilise un encodage Unicode autre qu’UTF-8, les lignes de code dans le *`.asm`* fichier peuvent ne pas s’afficher correctement.

### <a name="fa-argument"></a>Argument `/Fa`

None
Un fichier *. asm source* est créé pour chaque fichier de code source dans la compilation.

*extension*\
Le compilateur place un fichier listing nommé *filename*. asm dans le répertoire actif. Ce formulaire d’argument est valide uniquement lors de la compilation d’un fichier de code source unique.

*nom de fichier. extension*\
Le compilateur place un fichier listing nommé *filename. extension* dans le répertoire actif. Ce formulaire d’argument est valide uniquement lors de la compilation d’un fichier de code source unique.

*Directory*__\\__\
Le compilateur crée un fichier *SOURCE_FILE. asm* pour chaque fichier de code source dans la compilation. Il est placé dans le *répertoire* spécifié. La barre oblique inverse de fin est obligatoire. Seuls les chemins d’accès sur le disque actuel sont autorisés.

*répertoire* __\\__ *nom du fichier*\
Un fichier listing nommé *filename. asm* est placé dans le *répertoire* spécifié. Ce formulaire d’argument est valide uniquement lors de la compilation d’un fichier de code source unique.

*répertoire* __\\__ *nom de fichier. extension*\
Un fichier listing nommé *filename. extension* est placé dans le *répertoire* spécifié. Ce formulaire d’argument est valide uniquement lors de la compilation d’un fichier de code source unique.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >  fichiers de sortie **C/C++**  >  **Output Files** .

1. Modifiez la propriété sortie de l' **assembleur** pour définir les options **/FAC** et **/FAS** de l’assembleur, de l’ordinateur et du code source. Modifiez la propriété **utiliser Unicode pour la liste des assembleurs** pour définir l' **`/FAu`** option de sortie ANSI ou UTF-8. Modifiez l' **emplacement de la liste ASM** pour définir l' **`/Fa`** option d’affichage du nom et de l’emplacement du fichier.

La définition de la **sortie** de l’assembleur et l' **utilisation d’Unicode pour les propriétés de la liste des assembleurs** peuvent entraîner [un avertissement de ligne de commande D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Pour combiner ces options dans l’IDE, utilisez à la place le champ **options supplémentaires** dans la page de propriétés **ligne de commande** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> ou <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Pour spécifier **/FAu**, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> .

## <a name="example"></a>Exemple

La ligne de commande suivante génère une liste combinée de codes machine et de sources, appelée *`HELLO.cod`* :

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)\
[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)\
[Spécification du chemin d’accès](specifying-the-pathname.md)
