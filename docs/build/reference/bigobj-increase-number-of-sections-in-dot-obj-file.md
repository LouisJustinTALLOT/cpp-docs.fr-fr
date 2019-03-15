---
title: /bigobj (Augmenter le nombre de sections dans le fichier .obj)
ms.date: 11/04/2016
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: a9685834fc3e1de246c9d9d60d206538b744ce3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809858"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Augmenter le nombre de sections dans le fichier .obj)

**/bigobj** augmente le nombre de sections qu’un fichier objet peut contenir.

## <a name="syntax"></a>Syntaxe

```
/bigobj
```

## <a name="remarks"></a>Notes

Par défaut, un fichier objet peut contenir jusqu'à 65 536 (2 ^ 16) sections adressables. C’est le cas, peu importe les plateforme cible est spécifié. **/bigobj** augmente cette capacité d’adressage à 4 294 967 296 (2 ^ 32).

La plupart des modules ne génèrent jamais d’un fichier .obj qui contient plus de 65 536 sections. Toutefois, code générées par l’ordinateur ou le code qui fait un usage intensif de bibliothèques de modèles peut nécessiter des fichiers .obj qui peuvent contenir plusieurs sections. **/bigobj** est activé par défaut sur les projets de plateforme universelle Windows (UWP), car le code XAML générées par l’ordinateur inclut un grand nombre d’en-têtes. Si vous désactivez cette option sur un projet d’application UWP, vous êtes susceptible de rencontrer l’erreur du compilateur C1128.

Éditeurs de liens fourni avant Visual C++ 2005 ne peut pas lire les fichiers .obj qui ont été générées avec **/bigobj**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
