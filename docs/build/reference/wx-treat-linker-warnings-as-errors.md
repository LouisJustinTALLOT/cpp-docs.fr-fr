---
description: En savoir plus sur:/WX (traiter les avertissements de l’éditeur de liens comme des erreurs)
title: /WX (Traiter les avertissements de l'Éditeur de liens comme des erreurs)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: 965c48ff9c9f975350f3c1e54d8090823be8fd2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261032"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Traiter les avertissements de l'Éditeur de liens comme des erreurs)

```
/WX[:NO]
```

## <a name="remarks"></a>Notes

/WX n’entraîne la génération d’aucun fichier de sortie si l’éditeur de liens génère un avertissement.

Cela est similaire à **/WX** pour le compilateur (consultez [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)](compiler-option-warning-level.md) pour plus d’informations). Toutefois, la spécification de **/WX** pour la compilation n’implique pas que **/WX** sera également appliqué pour la phase Link ; vous devez spécifier explicitement **/WX** pour chaque outil.

Par défaut, **/WX** n’est pas activé. Pour traiter les avertissements de l’éditeur de liens comme des erreurs, spécifiez **/WX**. **/WX : no** est le même que si vous ne spécifiez pas **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
