---
title: /bigobj (Augmenter le nombre de sections dans le fichier .obj)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 46399dc0c1ff552b4fc963b686ac6aa6df8b6f71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272973"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Augmenter le nombre de sections dans le fichier .obj)

**/bigobj** augmente le nombre de sections qu’un fichier objet peut contenir.

## <a name="syntax"></a>Syntaxe

> **/bigobj**

## <a name="remarks"></a>Notes

Par défaut, un fichier objet peut contenir jusqu'à 65 279 (presque 2 ^ 16) sections adressables. Cette limite s’applique quel que soit le qui cible la plateforme est spécifiée. **/bigobj** augmente cette capacité d’adressage à 4 294 967 296 (2 ^ 32).

La plupart des modules ne génèrent jamais un fichier .obj qui contient plus de 65 279 sections. Toutefois, le code machine généré, ou du code qui fait un usage intensif de bibliothèques de modèles, peut-être nécessiter des fichiers .obj qui peuvent contenir plusieurs sections. **/bigobj** est activé par défaut sur les projets de plateforme universelle Windows (UWP), car le code XAML générées par l’ordinateur inclut un grand nombre d’en-têtes. Si vous désactivez cette option sur un projet d’application UWP, votre code peut générer l’erreur du compilateur C1128.

Pour plus d’informations sur le format de fichier objet COFF-PE, consultez [Format PE](/windows/desktop/debug/pe-format) dans la documentation de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez le **/bigobj** option du compilateur dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
