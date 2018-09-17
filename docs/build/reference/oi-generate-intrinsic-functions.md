---
title: -Oi (générer des fonctions intrinsèques) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs:
- C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527f326d629bc8d41efcd73a938994570bed4d2e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725918"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Générer des fonctions intrinsèques)

Remplace certains appels de fonction avec des formes intrinsèques ou sinon spéciaux de la fonction permettant à votre application s’exécute plus rapidement.

## <a name="syntax"></a>Syntaxe

```
/Oi[-]
```

## <a name="remarks"></a>Notes

Les programmes qui utilisent des fonctions intrinsèques sont plus rapides, car ils n’ont pas la surcharge d’appels de fonction, mais peuvent être plus volumineux en raison du code supplémentaire créé.

Consultez [intrinsèque](../../preprocessor/intrinsic.md) pour plus d’informations sur les fonctions possédant des formes intrinsèques.

**/Oi** est uniquement une demande au compilateur Remplacez-les par des appels de fonctions intrinsèques ; le compilateur peut appeler la fonction (et pas remplacer l’appel de fonction intrinsèque) si cela entraîne de meilleures performances.

**x86 spécifique**

Les fonctions à virgule flottante intrinsèques ne pas effectuer des vérifications spéciales sur les valeurs d’entrée et donc travailler dans des plages restreints d’entrée et ont différentes exceptions et les restrictions que les routines de bibliothèque portant le même nom. À l’aide de formes intrinsèques véritables implique une perte de la gestion des exceptions IEEE et une perte de `_matherr` et `errno` fonctionnalités ; cette dernière implique la perte de compatibilité ANSI. Toutefois, les formes intrinsèques peuvent accélérer considérablement les programmes de beaucoup de virgule flottante, et pour de nombreux programmes, les problèmes de conformité sont peu d’intérêt pratique.

Vous pouvez utiliser la [Za](../../build/reference/za-ze-disable-language-extensions.md) option du compilateur pour remplacer la génération d’options à virgule flottante intrinsèques vraies. Dans ce cas, les fonctions sont générées en tant que routines de bibliothèque qui passent directement des arguments au processeur de calcul en virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme.

**FIN x86 spécifique**

Vous utilisez également [intrinsèque](../../preprocessor/intrinsic.md) pour créer des fonctions intrinsèques ou [(fonction) (C/C++)](../../preprocessor/function-c-cpp.md) pour forcer explicitement un appel de fonction.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **optimisation** page de propriétés.

1. Modifier le **activation des fonctions intrinsèques** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le Code), options](../../build/reference/o-options-optimize-code.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[compilateur, fonctions intrinsèques](../../intrinsics/compiler-intrinsics.md)