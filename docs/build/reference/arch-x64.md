---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: d1ee086eff73b0538390764ef26b051919d65bcf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456795"
---
# <a name="arch-x64"></a>/arch (x64)

Spécifie l'architecture pour la génération de code sur x64. Consultez également [/arch (x86)](../../build/reference/arch-x86.md) et [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Arguments

**/ arch : AVX**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions.

**/ arch : avx2**<br/>
Active l’utilisation des instructions Intel Advanced Vector Extensions 2.

## <a name="remarks"></a>Notes

**/ arch** uniquement affecte la génération pour les fonctions natives de code. Lorsque vous utilisez [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) à compiler, **/arch** n’a aucun effet sur la génération de code pour les fonctions managées.

Le `__AVX__` symbole de préprocesseur est défini lors de la **/arch : AVX** option du compilateur est spécifiée. Le `__AVX2__` symbole de préprocesseur est défini lors de la **/arch : avx2** option du compilateur est spécifiée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md). Le **/arch : avx2** option a été introduite dans Visual Studio 2013 Update 2, version 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /arch:AVX ou /arch:AVX2 dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.

1. Sélectionnez le **génération de Code** page de propriétés.

1. Dans le **activer du jeu d’instructions amélioré** liste déroulante, sélectionnez **Advanced Vector Extensions (/ arch : AVX)** ou **Advanced Vector Extensions 2 (/ arch : AVX2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)