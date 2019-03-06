---
title: /Qpar (paralléliseur automatique)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: 8563382f9a95d9b7da49efdf1f12d517eae3da3d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416629"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (paralléliseur automatique)

Permet la [PARALLÉLISEUR](../../parallel/auto-parallelization-and-auto-vectorization.md) fonctionnalité du compilateur automatiquement paralléliser les boucles dans votre code.

## <a name="syntax"></a>Syntaxe

```
/Qpar
```

## <a name="remarks"></a>Notes

Lorsque le compilateur parallélise automatiquement des boucles de code, il répartit le calcul sur plusieurs cœurs de processeur. Une boucle est parallélisée uniquement si le compilateur détermine qu’il est autorisé à le faire et cette parallélisation améliorera les performances.

Le `#pragma loop()` directives sont disponibles pour aider à l’optimiseur de paralléliser les boucles spécifiques. Pour plus d’informations, consultez [boucle](../../preprocessor/loop.md).

Pour plus d’informations sur l’activation des messages de sortie pour le PARALLÉLISEUR automatique, consultez [/qpar-report (niveau de rapport du PARALLÉLISEUR automatique)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur /Qpar dans Visual Studio

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.

1. Dans le **Pages de propriétés** boîte de dialogue **C/C++**, sélectionnez **ligne de commande**.

1. Dans le **des Options supplémentaires** , entrez `/Qpar`.

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Pour définir l’option de compilateur /Qpar par programmation

- Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](../../build/reference/q-options-low-level-operations.md)<br/>
[/Qpar-report (Niveau de rapport du paralléliseur automatique)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[#pragma loop()](../../preprocessor/loop.md)<br/>
[Programmation parallèle en Code natif](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
