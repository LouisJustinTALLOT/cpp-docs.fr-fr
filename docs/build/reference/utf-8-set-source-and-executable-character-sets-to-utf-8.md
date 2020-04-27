---
title: /UTF-8 (définir les jeux de caractères source et exécutable UTF-8sur)
ms.date: 04/26/2020
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
no-loc:
- UTF
- UTF-8
- UTF-16
ms.openlocfilehash: c98a30b0ec4b36b8bd87fb0956d9382751975cfd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168863"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-opno-locutf-8"></a>`/utf-8`(Définir les jeux de caractères source et exécutable UTF-8sur)

Spécifie le jeu de caractères source et le jeu de caractères UTF-8d’exécution comme.

## <a name="syntax"></a>Syntaxe

> **`/utf-8`**

## <a name="remarks"></a>Notes

Vous pouvez utiliser l' **`/utf-8`** option pour spécifier les jeux de caractères source et d’exécution comme étant encodés UTF-8à l’aide de. Cela équivaut à spécifier **`/source-charset:utf-8 /execution-charset:utf-8`** sur la ligne de commande. L’une de ces options active également **`/validate-charset`** l’option par défaut. Pour obtenir la liste des identificateurs de pages de codes et des noms de jeux de caractères pris en charge, consultez [identificateurs de page de codes](/windows/win32/Intl/code-page-identifiers).

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est dans un format Unicode encodé, par exemple UTF-16 ou. UTF-8 Si aucune marque d’ordre d’octet n’est trouvée, il suppose que le fichier source est encodé à l’aide de la page de codes de l’utilisateur actuel, à moins que **`/utf-8`** vous n' **`/source-charset`** ayez spécifié une page de codes à l’aide de ou de l’option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide de plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Définir l’option dans Visual Studio ou par programme

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés**ligne de commande** des **Propriétés** > de configuration**C/C++** > .

1. Dans **options supplémentaires**, ajoutez l' **`/utf-8`** option permettant de spécifier l’encodage de votre choix.

1. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (définir le jeu de caractères d’exécution)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (Définir le jeu de caractères source)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (Valider les caractères compatibles)](validate-charset-validate-for-compatible-characters.md)
