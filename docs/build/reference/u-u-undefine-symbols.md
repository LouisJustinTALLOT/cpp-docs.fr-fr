---
title: /U, /u (Annuler la définition de symboles)
ms.date: 06/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: 4d7a2b3d5df2b22dc53eb7b58bfb78cdb1824b26
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616659"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Annuler la définition de symboles)

L' **`/U`** option du compilateur annule la définition du symbole de préprocesseur spécifié. L' **`/u`** option de compilateur annule la définition des symboles spécifiques à Microsoft définis par le compilateur.

## <a name="syntax"></a>Syntaxe

> **`/U`**\[]*symbole*\
> **`/u`**

## <a name="arguments"></a>Arguments

*symbole*<br/>
Symbole de préprocesseur à annuler la définition.

## <a name="remarks"></a>Notes

Aucune des **`/U`** options et **`/u`** ne peut annuler la définition d’un symbole créé à l’aide de la **`#define`** directive.

L' **`/U`** option peut annuler la définition d’un symbole qui a été précédemment défini à l’aide de l' **`/D`** option.

Par défaut, le compilateur peut définir un grand nombre de symboles spécifiques à Microsoft. Voici quelques-uns des plus courants :

| Symbole | Fonction |
|--|--|
| `_CHAR_UNSIGNED` | Le type de caractère par défaut est non signé. Défini lorsque l' [**`/J`**](j-default-char-type-is-unsigned.md) option est spécifiée. |
| `_CPPRTTI` | Défini pour le code compilé avec l' [**`/GR`**](gr-enable-run-time-type-information.md) option. |
| `_CPPUNWIND` | Défini pour le code compilé avec l' [**`/EHsc`**](eh-exception-handling-model.md) option. |
| `_DLL` | Défini lorsque l' [**`/MD`**](md-mt-ld-use-run-time-library.md) option est spécifiée. |
| `_M_IX86` | Par défaut, défini sur 600 pour les cibles x86. |
| `_MSC_VER` | Défini en tant que valeur entière unique pour chaque version du compilateur. Pour plus d’informations, consultez [macros prédéfinies](../../preprocessor/predefined-macros.md). |
| `_WIN32` | Défini pour les applications WIN32. Toujours défini. |
| `_MT` | Défini lorsque l’option [ **`/MD`** ou **`/MT`** ](md-mt-ld-use-run-time-library.md) est spécifiée. |

Pour obtenir la liste complète des macros prédéfinies spécifiques à Microsoft, consultez [macros prédéfinies](../../preprocessor/predefined-macros.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé des **Propriétés de configuration**  >  **C/C++**  >  **Advanced** .

1. Modifiez les propriétés des **définitions de préprocesseur non définies** ou **annulez la définition de toutes les définitions de préprocesseur** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> ou <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[**`/J`**(Type de caractère par défaut non signé)](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`**(Activer les informations de type au moment de l’exécution)](gr-enable-run-time-type-information.md)<br/>
[**`/EH`**(Modèle de gestion des exceptions)](eh-exception-handling-model.md)<br/>
[**`/MD`**, **`/MT`** , **`/LD`** (Utiliser la bibliothèque Runtime)](md-mt-ld-use-run-time-library.md)
