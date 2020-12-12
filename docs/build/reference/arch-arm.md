---
description: En savoir plus sur les éléments suivants:/Arch (ARM)
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: 885b624eb6a470d24d691641d0be63515ee76a49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179562"
---
# <a name="arch-arm"></a>/arch (ARM)

Spécifie l'architecture pour la génération de code sur ARM. Voir aussi [/Arch (x86)](arch-x86.md) et [/Arch (x64)](arch-x64.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Arguments

**/Arch : ARMv7VE**<br/>
Permet l'utilisation des instructions des extensions de virtualisation ARMv7VE.

**/Arch : VFPv4**<br/>
Permet l'utilisation des instructions ARM VFPv4. Si cette option n'est pas spécifiée, VFPv3 est utilisé par défaut.

## <a name="remarks"></a>Notes

La `_M_ARM_FP` macro (pour ARM uniquement) indique l’option du compilateur **/ARCH** (le cas échéant) qui a été utilisée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).

Quand vous utilisez [/CLR](clr-common-language-runtime-compilation.md) pour compiler, **/ARCH** n’a aucun effet sur la génération de code pour les fonctions managées. **/ARCH** affecte uniquement la génération de code pour les fonctions natives.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /arch:ARMv7VE ou /arch:VFPv4 dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Dans la zone **options supplémentaires** , ajoutez `/arch:ARMv7VE` ou `/arch:VFPv4` .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/Arch (architecture d’UC minimale)](arch-minimum-cpu-architecture.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
