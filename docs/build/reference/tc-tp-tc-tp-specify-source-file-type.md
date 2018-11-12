---
title: /Tc, /Tp, /TC, /TP (Spécifier le type de fichier source)
ms.date: 1/11/2018
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
ms.openlocfilehash: e435b48359a708408ff8659e53c9e7c4f7e80261
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619113"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Spécifier le type de fichier source)

Le **TP** option spécifie que son argument de nom de fichier est un fichier source C, même si elle n’a pas d’extension .c. Le **/Tp** option spécifie que son argument de nom de fichier est un fichier source C++, même si elle n’a pas une extension .cpp ou .cxx. Un espace entre l’option et le nom de fichier est facultatif. Chaque option spécifie un seul fichier ; Pour spécifier des fichiers supplémentaires, répétez l’option.

**/TC** et **/TP** sont des variantes globales de **TP** et **/Tp**. Ils indiquent au compilateur de traiter tous les fichiers nommés sur la ligne de commande en tant que fichiers sources C (**TP**) ou des fichiers sources C++ (**/TP**), quel que soit l’emplacement sur la ligne de commande en relation avec l’option. Ces options globales peuvent être substituées sur un seul fichier par le biais de **TP** ou **/Tp**.

## <a name="syntax"></a>Syntaxe

> **/TC** _filename_
>  **/Tp** _filename_
> **TP** 
>  **/TP**

## <a name="arguments"></a>Arguments

*filename*<br/>
Un fichier source C ou C++.

## <a name="remarks"></a>Notes

Par défaut, **CL** suppose que les fichiers portant l’extension .c sont des fichiers sources C et les fichiers avec le .cpp ou .cxx sont des fichiers sources C++.

Lorsque soit la **TC** ou **Tc** option est spécifiée, une spécification de la [/Zc : wchar_t (wchar_t est un Type natif)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option est ignorée.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **avancé** page de propriétés.

1. Modifier le **compilation sous** propriété. Choisissez **OK** ou **appliquer** pour appliquer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Exemples

Cette ligne de commande CL Spécifie que MAIN.c, TEST.prg et COLLATE.prg sont tous des fichiers source C. CL ne reconnaîtra pas PRINT.prg.

> CL PRINCIPAL. C /TcTEST.PRG /TcCOLLATE.PRG imprimer. PRG

Cette ligne de commande CL Spécifie que TEST1.c, TEST2.cxx, TEST3.huh et TEST4.o sont compilés en tant que fichiers C++, et que TEST5.z est compilé en tant qu’un fichier C.

> CL TEST1. C TEST2. CXX TEST3. NON TEST4. O TP TEST5. Z /TP

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
