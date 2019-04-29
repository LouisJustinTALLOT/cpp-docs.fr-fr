---
title: /Qvec-report (Niveau de rapport du vectoriseur automatique)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 655be3581eee4b23a8d0f2bcfaea7d07c8b1b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319250"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Niveau de rapport du vectoriseur automatique)

Active la fonctionnalité de création de rapports du compilateur [Vectoriseur](../../parallel/auto-parallelization-and-auto-vectorization.md) et spécifie le niveau des messages d’information pour la sortie pendant la compilation.

## <a name="syntax"></a>Syntaxe

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Notes

**/Qvec-report:1**<br/>
Génère un message d’information pour les boucles qui sont vectorisées.

**/Qvec-report:2**<br/>
Génère un message d’information pour les boucles qui sont vectorisées et pour les boucles non vectorisées, ainsi que d’un code de raison.

Pour plus d’informations sur les codes motif et les messages, consultez [Messages du Vectoriseur et du PARALLÉLISEUR](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur /Qvec-report dans Visual Studio

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.

1. Dans le **Pages de propriétés** boîte de dialogue **C/C++**, sélectionnez **ligne de commande**.

1. Dans le **des Options supplémentaires** , entrez `/Qvec-report:1` ou `/Qvec-report:2`.

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Pour définir l’option de compilateur /Qvec-report par programmation

- Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Programmation parallèle en Code natif](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
