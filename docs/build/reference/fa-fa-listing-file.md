---
title: / FA, /Fa (fichier Listing) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs:
- C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9f1d205eff155b628081c5bc615570c44a88f08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412806"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (Fichier listing)

Crée un fichier listing contenant du code assembleur.

## <a name="syntax"></a>Syntaxe

> **/FA**[**c**\][**s**\][**u**] **/Fa**_chemin d’accès_

## <a name="remarks"></a>Notes

Le **/FA** option du compilateur génère un fichier de listing assembleur pour chaque unité de traduction dans la compilation, ce qui correspond généralement à un fichier source C ou C++. Par défaut, l’assembleur uniquement est inclus dans le fichier de liste, qui est encodé comme ANSI. Le paramètre facultatif **c**, **s**, et **u** arguments à **/FA** contrôle machine si le code ou de code source sont générés avec l’assembleur liste, et si la liste est encodée au format UTF-8.

Par défaut, chaque fichier listing Obtient le même nom que le fichier source et a une extension .asm. Lorsque le code machine est inclus à l’aide de la **c** option, le fichier de liste a une extension .cod. Vous pouvez modifier le nom et l’extension de fichier listing et le répertoire où il est créé à l’aide de la **/Fa** option.

### <a name="fa-arguments"></a>/FA arguments

none<br/>
Uniquement les langage assembleur sont inclus dans la liste.

**c**<br/>
Facultatif. Inclut le code machine dans la liste.

**s**<br/>
Facultatif. Inclut le code source dans la liste.

**u**<br/>
Facultatif. Encode le fichier d’annonce au format UTF-8 et inclut un marqueur d’ordre d’octet. Par défaut, le fichier est codé en ANSI. Utilisez `u` pour créer un fichier listing qui s’affiche correctement sur n’importe quel système, ou si vous utilisez Unicode des fichiers de code source en tant qu’entrée pour le compilateur.

Si les deux **s** et **u** sont spécifiés et si une source de fichier de code utilise un encodage Unicode autre que UTF-8, puis les lignes de code dans le fichier .asm affichent ne peut-être pas correctement.

### <a name="fa-argument"></a>/FA argument

none<br/>
Un *source*fichier .asm est créé pour chaque fichier de code source dans la compilation.

*filename*<br/>
Un fichier listing nommé *filename*.asm est placé dans le répertoire actif. Cela est uniquement valide lors de la compilation d’un fichier de code source unique.

*nomfichier.extension*<br/>
Un fichier listing nommé *nomfichier.extension* est placé dans le répertoire actif. Cela est uniquement valide lors de la compilation d’un fichier de code source unique.

*Répertoire*__\\__<br/>
Un *source_file*fichier .asm est créé et placé dans le texte spécifié *directory* pour chaque fichier de code source dans la compilation. Notez la barre oblique de fin requise. Uniquement les chemins d’accès sur le disque en cours sont autorisées.

*répertoire*__\\__*nom de fichier*<br/>
Un fichier listing nommé *filename*.asm est placé dans le texte spécifié *directory*. Cela est uniquement valide lors de la compilation d’un fichier de code source unique.

*répertoire*__\\__*nomfichier.extension*<br/>
Un fichier listing nommé *nomfichier.extension* est placé dans le texte spécifié *directory*. Cela est uniquement valide lors de la compilation d’un fichier de code source unique.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

2. Sélectionnez le **propriétés de Configuration** > **C/C++** > **fichiers de sortie** page de propriétés.

3. Modifier le **sortie de l’assembleur** propriété à définir le **/FAc** et **/FA** options assembleur, machine et code source. Modifier le **utiliser Unicode pour assembleur répertoriant** propriété à définir le **/FAu** option pour la sortie ANSI ou UTF-8. Modifier le **emplacement de la liste ASM** pour définir le **/Fa** option permettant de répertorier le nom de fichier et l’emplacement.

Notez que l’affectation à la fois **sortie de l’assembleur** et **utiliser Unicode pour assembleur répertoriant** propriétés peuvent entraîner [avertissement de ligne de commande D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Pour combiner ces options dans l’IDE, utilisez le **des Options supplémentaires** champ dans le **ligne de commande** page de propriétés à la place.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> ou <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Pour spécifier **/FAu**, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante produit une source combinée et listing de code machine appelé Hello.cod combinant :

```cmd
CL /FAcs HELLO.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](../../build/reference/output-file-f-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)