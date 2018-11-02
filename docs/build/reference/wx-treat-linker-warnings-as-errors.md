---
title: /WX (Traiter les avertissements de l'Éditeur de liens comme des erreurs)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: 65585e35ac9de590636d9a116dcdb70cee0e785c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517020"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Traiter les avertissements de l'Éditeur de liens comme des erreurs)

```
/WX[:NO]
```

## <a name="remarks"></a>Notes

/WX est spécifiée, aucun fichier de sortie est généré si l’éditeur de liens génère un avertissement.

Cela revient à **/WX** pour le compilateur (voir [wln, / W0, W1, W2, / w3, / W4, W1, W2, / w3, / W4, Wall, WD, / we, Wo, / WV, /WX (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md) pour plus d’informations). Toutefois, la spécification **/WX** pour la compilation n’implique pas que **/WX** sera également appliquée pour la phase de liaison ; vous devez explicitement spécifier **/WX** pour chaque outil.

Par défaut, **/WX** n’est pas en vigueur. Pour traiter les avertissements de l’éditeur de liens comme des erreurs, spécifiez **/WX**. **/WX:no** est identique à ne pas spécifier **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)