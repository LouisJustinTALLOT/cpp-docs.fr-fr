---
description: En savoir plus sur:/qvec-Report (niveau de rapport Vectoriseur automatique)
title: /Qvec-report (Niveau de rapport du vectoriseur automatique)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 734dabffa3bf19ecaba42d35d208eb27ec7b2968
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225464"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Niveau de rapport du vectoriseur automatique)

Active la fonctionnalité de création de rapports du [Vectoriseur automatique](../../parallel/auto-parallelization-and-auto-vectorization.md) du compilateur et spécifie le niveau de messages d’information pour la sortie pendant la compilation.

## <a name="syntax"></a>Syntaxe

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Notes

**/Qvec-Report : 1**<br/>
Génère un message d’information pour les boucles qui sont vectorisées.

**/Qvec-Report : 2**<br/>
Génère un message d’information pour les boucles qui sont vectorisées et pour les boucles qui ne sont pas vectorisées, ainsi qu’un code de raison.

Pour plus d’informations sur les codes de raison et les messages, consultez [messages vectoriseur et paralléliseur](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Pour définir l’option du compilateur/qvec-report dans Visual Studio

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Propriétés**.

1. Dans la boîte de dialogue **pages de propriétés** , sous **C/C++**, sélectionnez **ligne de commande**.

1. Dans la zone **options supplémentaires** , entrez `/Qvec-report:1` ou `/Qvec-report:2` .

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Pour définir l’option du compilateur/qvec-report par programmation

- Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Vectorisation de code natif dans Visual Studio](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
