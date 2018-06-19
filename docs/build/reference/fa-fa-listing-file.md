---
title: / FA, /Fa (fichier Listing) | Documents Microsoft
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
ms.openlocfilehash: 1840d2f2ff7d968fdcc19e2013a89af9cec32d24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378949"
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (Fichier listing)
Crée un fichier listing contenant du code assembleur.  
  
## <a name="syntax"></a>Syntaxe  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/FA**_chemin d’accès_  
  
## <a name="remarks"></a>Notes  
Le `/FA` option du compilateur génère un fichier du listing assembleur pour chaque unité de traduction dans la compilation, ce qui correspond généralement à un fichier source C ou C++. Par défaut, l’assembleur uniquement est inclus dans le fichier de liste, qui est encodé comme ANSI. Le paramètre facultatif `c`, `s`, et `u` arguments `/FA` contrôle si les code machine ou code source sont générés avec l’assembleur de liste, et si la liste est encodée en UTF-8.  
  
Par défaut, chaque fichier listing Obtient le même nom que le fichier source et a une extension .asm. Lorsque le code machine est inclus à l’aide de la `c` option, le fichier de liste a une extension .cod. Vous pouvez modifier le nom et l’extension de fichier listing et le répertoire dans lequel il est créé à l’aide de la `/Fa` option.  

### <a name="fa-arguments"></a>/FA arguments  
aucun  
Uniquement les langage assembleur sont inclus dans la liste.  
  
`c`  
Facultatif. Inclut le code machine dans la liste.  
  
`s`  
Facultatif. Inclut le code source dans la liste.  
  
`u` Facultatif. Encode le fichier d’annonce au format UTF-8 et inclut un marqueur d’ordre d’octet. Par défaut, le fichier est encodé comme ANSI. Utilisez `u` pour créer un fichier listing qui s’affiche correctement sur n’importe quel système, ou si vous utilisez Unicode des fichiers de code source comme entrée pour le compilateur.  
  
Si les deux `s` et `u` sont spécifiés et si une source de fichier de code utilise un encodage Unicode autre que UTF-8, puis les lignes de code dans le fichier .asm peut ne pas affichent correctement.  
  
### <a name="fa-argument"></a>/FA argument  
aucun  
Un *source*fichier .asm est créé pour chaque fichier de code source dans la compilation.  
  
*nom de fichier* un fichier listing nommé *nom de fichier*.asm est placé dans le répertoire actif. Cela n’est valide que lors de la compilation d’un fichier de code source unique.  
  
*nomfichier.extension*  
Un fichier listing nommé *nomfichier.extension* est placé dans le répertoire actif. Cela n’est valide que lors de la compilation d’un fichier de code source unique.  
  
*Répertoire*\  
Un *source_file*.asm est créé et placé dans le texte spécifié *répertoire* pour chaque fichier de code source dans la compilation. Notez la barre oblique de fin requise. Uniquement les chemins d’accès sur le disque en cours sont autorisés.  
  
*répertoire*\\*nom de fichier* un fichier listing nommé *nom de fichier*.asm est placé dans le texte spécifié *active*. Cela n’est valide que lors de la compilation d’un fichier de code source unique.  
  
*répertoire*\\*nomfichier.extension*  
Un fichier listing nommé *nomfichier.extension* est placé dans le texte spécifié *active*. Cela n’est valide que lors de la compilation d’un fichier de code source unique.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Ouvrez le **C/C++** dossier et sélectionnez le **fichiers de sortie** page de propriétés.  
  
3.  Modifier la **sortie de l’assembleur** propriété à définir le `/FAc` et `/FAs` options pour le code source, machine et assembleur. Modifier la **utiliser Unicode pour Assembler répertoriant** propriété à définir la `/FAu` option de sortie ANSI ou UTF-8. Modifier la **emplacement d’un listing ASM** pour définir le `/Fa` option pour répertorier le nom de fichier et l’emplacement.  
  
Notez que l’affectation à la fois **sortie de l’assembleur** et **utiliser Unicode pour Assembler répertoriant** propriétés peuvent entraîner [avertissement de ligne de commande D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Pour combiner ces options dans l’IDE, utilisez le **des Options supplémentaires** champ dans le **ligne de commande** page de propriétés à la place.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> ou <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Pour spécifier `/FAu`, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Exemple  
La ligne de commande suivante génère une source combinée et le listing de code machine appelé Hello.cod combinant :  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)