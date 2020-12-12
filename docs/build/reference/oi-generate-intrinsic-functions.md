---
description: En savoir plus sur:/Oi (générer des fonctions intrinsèques)
title: /Oi (Générer des fonctions intrinsèques)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
ms.openlocfilehash: fc08ff495391092115197fe70e8c3673b77f32e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214277"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Générer des fonctions intrinsèques)

Remplace certains appels de fonction par des formes intrinsèques ou des formes spéciales de la fonction qui aident votre application à s’exécuter plus rapidement.

## <a name="syntax"></a>Syntaxe

```
/Oi[-]
```

## <a name="remarks"></a>Notes

Les programmes qui utilisent des fonctions intrinsèques sont plus rapides, car ils n’ont pas la surcharge des appels de fonction, mais ils peuvent être plus volumineux en raison de la création d’un code supplémentaire.

Pour plus d’informations sur les fonctions qui ont des formes intrinsèques, consultez [intrinsic](../../preprocessor/intrinsic.md) .

**/OI** est uniquement une demande au compilateur de remplacer certains appels de fonction par des intrinsèques ; le compilateur peut appeler la fonction (et ne pas remplacer l’appel de fonction par un intrinsèque) si cela entraîne de meilleures performances.

**Section spécifique à x86**

Les fonctions à virgule flottante intrinsèques n’effectuent pas de vérifications spéciales sur les valeurs d’entrée et fonctionnent donc dans des plages d’entrée restreintes, et ont des conditions de gestion des exceptions et des limites différentes de celles des routines de bibliothèque portant le même nom. L’utilisation des véritables formes intrinsèques implique la perte de la gestion des exceptions IEEE, ainsi que la perte de `_matherr` et des `errno` fonctionnalités ; cette dernière implique une perte de conformité ANSI. Toutefois, les formes intrinsèques permettent d’accélérer considérablement les programmes nécessitant beaucoup de ressources en virgule flottante, et pour de nombreux programmes, les problèmes de conformité sont très pratiques.

Vous pouvez utiliser l’option de compilateur [za](za-ze-disable-language-extensions.md) pour remplacer la génération d’options à virgule flottante intrinsèques vraies. Dans ce cas, les fonctions sont générées en tant que routines de bibliothèque qui passent directement des arguments au processeur de calcul en virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme.

**FIN spécifique x86**

Vous utilisez également [intrinsic](../../preprocessor/intrinsic.md) pour créer des fonctions intrinsèques, ou [Function (C/C++)](../../preprocessor/function-c-cpp.md) pour forcer explicitement un appel de fonction.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **optimisation** .

1. Modifiez la propriété **activer les fonctions intrinsèques** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le code), options](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Intrinsèques du compilateur](../../intrinsics/compiler-intrinsics.md)
