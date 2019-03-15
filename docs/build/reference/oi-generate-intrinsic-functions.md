---
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
ms.openlocfilehash: f3afedade6f99129c21069e5117daa4ceb616cc2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811886"
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

Vous pouvez utiliser la [Za](za-ze-disable-language-extensions.md) option du compilateur pour remplacer la génération d’options à virgule flottante intrinsèques vraies. Dans ce cas, les fonctions sont générées en tant que routines de bibliothèque qui passent directement des arguments au processeur de calcul en virgule flottante au lieu de leur appliquer une transmission de type push sur la pile du programme.

**FIN x86 spécifique**

Vous utilisez également [intrinsèque](../../preprocessor/intrinsic.md) pour créer des fonctions intrinsèques ou [(fonction) (C/C++)](../../preprocessor/function-c-cpp.md) pour forcer explicitement un appel de fonction.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **optimisation** page de propriétés.

1. Modifier le **activation des fonctions intrinsèques** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[compilateur, fonctions intrinsèques](../../intrinsics/compiler-intrinsics.md)
