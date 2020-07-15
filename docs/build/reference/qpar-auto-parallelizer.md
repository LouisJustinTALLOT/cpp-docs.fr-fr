---
title: /Qpar (paralléliseur automatique)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: 18aaa1dc678ca2c73f9fad6c016aa40cfa95982b
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373799"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (paralléliseur automatique)

Active la fonctionnalité de [paralléliseur automatique](../../parallel/auto-parallelization-and-auto-vectorization.md) du compilateur pour paralléliser automatiquement les boucles dans votre code.

## <a name="syntax"></a>Syntaxe

```
/Qpar
```

## <a name="remarks"></a>Notes

Lorsque le compilateur parallélise automatiquement des boucles dans le code, il propage le calcul sur plusieurs cœurs de processeur. Une boucle est parallélisée uniquement si le compilateur détermine qu’il est autorisé à le faire et que la parallélisation améliore les performances.

Les `#pragma loop()` directives sont disponibles pour aider l’optimiseur à paralléliser des boucles spécifiques. Pour plus d’informations, consultez [Loop](../../preprocessor/loop.md).

Pour plus d’informations sur l’activation des messages de sortie pour l’auto-paralléliseur, consultez [/QPAR-Report (niveau de rapport paralléliseur automatique)](qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Pour définir l’option du compilateur/QPAR dans Visual Studio

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** , sous **C/C++**, sélectionnez **ligne de commande**.

1. Dans la zone **options supplémentaires** , entrez `/Qpar` .

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Pour définir l’option du compilateur/QPAR par programmation

- Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[/QPAR-Report (niveau de rapport paralléliseur automatique)](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[boucle de #pragma ()](../../preprocessor/loop.md)<br/>
[Vectorisation de code natif dans Visual Studio](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
