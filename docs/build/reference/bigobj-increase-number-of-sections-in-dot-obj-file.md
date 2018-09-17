---
title: -bigobj (augmentation du nombre de Sections dans. Fichier obj) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bigobj
dev_langs:
- C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f10456bea8be552df42efe135818ac9c47393fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721485"
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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)