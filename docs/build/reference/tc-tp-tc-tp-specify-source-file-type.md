---
description: En savoir plus sur:/TC,/TP,/TC,/TP (spécifier le type de fichier source)
title: /Tc, /Tp, /TC, /TP (Spécifier le type de fichier source)
ms.date: 01/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: 23aed145c8dd9ac36f26bcebe2ea2aab1c39e586
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230027"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Spécifier le type de fichier source)

L’option **/TC** spécifie que son argument FileName est un fichier source C, même s’il n’a pas d’extension. C. L’option **/TP** spécifie que son argument FileName est un fichier source C++, même s’il n’a pas d’extension. cpp ou. cxx. Un espace entre l’option et le nom de fichier est facultatif. Chaque option spécifie un fichier ; pour spécifier des fichiers supplémentaires, répétez l’option.

**/TC** et **/TP** sont des variantes globales de **/TC** et **/TP**. Ils spécifient au compilateur de traiter tous les fichiers nommés sur la ligne de commande en tant que fichiers sources C (**/TC**) ou fichiers sources C++ (**/TP**), sans tenir compte de l’emplacement sur la ligne de commande par rapport à l’option. Ces options globales peuvent être substituées sur un seul fichier au moyen de **/TC** ou **/TP**.

## <a name="syntax"></a>Syntaxe

>  _Nom de fichier_ /TC\
> **/TP** _NomFichier_\
> **/TC**\
> **/TP**

### <a name="arguments"></a>Arguments

*extension*<br/>
Fichier source C ou C++.

## <a name="remarks"></a>Notes

Par défaut, **CL** suppose que les fichiers avec l’extension. c sont des fichiers sources c et des fichiers avec l’extension. cpp ou. cxx sont des fichiers sources C++.

Lorsque l’option **TC** ou **TC** est spécifiée, toute spécification de l’option [/Zc : Wchar_t (wchar_t est un type natif)](zc-wchar-t-wchar-t-is-native-type.md) est ignorée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **compiler en tant que** . Choisissez **OK** ou **appliquer** pour appliquer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Exemples

Cette ligne de commande CL spécifie que MAIN. c, TEST. PRG et COLLATE. PRG sont tous des fichiers sources C. CL ne reconnaît pas PRINT. PRG.

> MAIN CL. C/TcTEST.PRG/TcCOLLATE.PRG imprimer. PRG

Cette ligne de commande CL spécifie que TEST1. c, TEST2. cxx, TEST3. non et TEST4. o sont compilés en tant que fichiers C++, et TEST5. z est compilé en tant que fichier C.

> CL TEST1. TEST2 C. TEST3 CXX. N’EST PAS TEST4. O/TC TEST5. Z/TP

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
