---
title: -Qpar-report (niveau de rapport du PARALLÉLISEUR automatique) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 847a93efc74c4e6111f49679219e1b26a70022f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707504"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (Niveau de rapport du paralléliseur automatique)

Active la fonctionnalité de création de rapports du compilateur [PARALLÉLISEUR](../../parallel/auto-parallelization-and-auto-vectorization.md) et spécifie le niveau des messages d’information pour la sortie pendant la compilation.

## <a name="syntax"></a>Syntaxe

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Notes

**/ Qpar-report : 1**<br/>
Génère un message d'information pour les boucles parallélisées.

**/ Qpar-report : 2**<br/>
Génère un message d'information pour les boucles parallélisées et non parallélisées, ainsi qu'un code motif.

Les messages sont signalés à stdout. Si aucun message d'information n'est signalé, cela signifie que le code ne contient pas de boucle ou que le niveau de rapport n'a pas été défini pour signaler les boucles non parallélisées. Pour plus d’informations sur les codes motifs et les messages, consultez [Messages du Vectoriseur et du PARALLÉLISEUR](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /Qpar-report dans Visual Studio

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.

1. Dans le **Pages de propriétés** boîte de dialogue **C/C++**, sélectionnez **ligne de commande**.

1. Dans le **des Options supplémentaires** , entrez `/Qpar-report:1` ou `/Qpar-report:2`.

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Pour définir l'option de compilateur /Qpar-report par programmation

- Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q (opérations de bas niveau), options](../../build/reference/q-options-low-level-operations.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[Programmation parallèle en Code natif](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)