---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: b732a74d5fe223fdaf3b161d4ae92093ab5df407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295200"
---
# <a name="arch-arm"></a>/arch (ARM)

Spécifie l'architecture pour la génération de code sur ARM. Voir aussi [/arch (x86)](arch-x86.md) et [/arch (x64)](arch-x64.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Arguments

**/arch:ARMv7VE**<br/>
Permet l'utilisation des instructions des extensions de virtualisation ARMv7VE.

**/arch:VFPv4**<br/>
Permet l'utilisation des instructions ARM VFPv4. Si cette option n'est pas spécifiée, VFPv3 est utilisé par défaut.

## <a name="remarks"></a>Notes

Le `_M_ARM_FP` macro (pour ARM uniquement) qui indique, le cas échéant, **/arch** option du compilateur a été utilisée. Pour plus d'informations, consultez [Predefined Macros](../../preprocessor/predefined-macros.md).

Lorsque vous utilisez [/CLR](clr-common-language-runtime-compilation.md) à compiler, **/arch** n’a aucun effet sur la génération de code pour les fonctions managées. **/ arch** uniquement affecte la génération pour les fonctions natives de code.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /arch:ARMv7VE ou /arch:VFPv4 dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez `/arch:ARMv7VE` ou `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Voir aussi

[/arch (Architecture d’UC minimale)](arch-minimum-cpu-architecture.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
