---
title: -arch (ARM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17f0f0735981c0a851bcab62ca1ad39c97af3965
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700675"
---
# <a name="arch-arm"></a>/arch (ARM)

Spécifie l'architecture pour la génération de code sur ARM. Voir aussi [/arch (x86)](../../build/reference/arch-x86.md) et [/arch (x64)](../../build/reference/arch-x64.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Arguments

**armv7ve**<br/>
Permet l’utilisation des instructions des extensions de virtualisation ARMv7VE.

**vfpv4**<br/>
Permet l'utilisation des instructions ARM VFPv4. Si cette option n'est pas spécifiée, VFPv3 est utilisé par défaut.

## <a name="remarks"></a>Notes

Le `_M_ARM_FP` macro (pour ARM uniquement) qui indique, le cas échéant, **/arch** option du compilateur a été utilisée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).

Lorsque vous utilisez [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) à compiler, **/arch** n’a aucun effet sur la génération de code pour les fonctions managées. **/ arch** uniquement affecte la génération pour les fonctions natives de code.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /arch:ARMv7VE ou /arch:VFPv4 dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez `/arch:ARMv7VE` ou `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/arch (Architecture d’UC minimale)](../../build/reference/arch-minimum-cpu-architecture.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)