---
description: En savoir plus sur:/QPAR-Report (niveau de rapport paralléliseur automatique)
title: /Qpar-report (Niveau de rapport du paralléliseur automatique)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 573ab7535b63ba8d3f19f2917c17709ac7726b38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225529"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (Niveau de rapport du paralléliseur automatique)

Active la fonctionnalité de création de rapports de l' [auto-paralléliseur](../../parallel/auto-parallelization-and-auto-vectorization.md) du compilateur et spécifie le niveau de messages d’information pour la sortie pendant la compilation.

## <a name="syntax"></a>Syntaxe

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Notes

**/QPAR-Report : 1**<br/>
Génère un message d'information pour les boucles parallélisées.

**/QPAR-Report : 2**<br/>
Génère un message d'information pour les boucles parallélisées et non parallélisées, ainsi qu'un code motif.

Les messages sont signalés à stdout. Si aucun message d'information n'est signalé, cela signifie que le code ne contient pas de boucle ou que le niveau de rapport n'a pas été défini pour signaler les boucles non parallélisées. Pour plus d’informations sur les codes de raison et les messages, consultez [messages vectoriseur et paralléliseur](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /Qpar-report dans Visual Studio

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** , sous **C/C++**, sélectionnez **ligne de commande**.

1. Dans la zone **options supplémentaires** , entrez `/Qpar-report:1` ou `/Qpar-report:2` .

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Pour définir l'option de compilateur /Qpar-report par programmation

- Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Vectorisation de code natif dans Visual Studio](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
