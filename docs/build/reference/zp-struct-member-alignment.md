---
description: En savoir plus sur:/ZP (alignement des membres de la structure)
title: /Zp (Alignement des membres de la structure)
ms.date: 01/08/2021
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: 8d29c442726aff9503a42378fce6a7b8b09526ed
ms.sourcegitcommit: 14d6ae0d527d05d153e26463d4cd5ada0f43e864
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98104776"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Alignement des membres de la structure)

Contrôle la façon dont les membres d’une structure sont empaquetés en mémoire et spécifie la même compression pour toutes les structures dans un module.

## <a name="syntax"></a>Syntaxe

> **`/Zp`**[**`1`**|**`2`**|**`4`**|**`8`**|**`16`**]

## <a name="remarks"></a>Notes

L' **`/ZpN`** option indique au compilateur où stocker chaque membre de la structure. Le compilateur stocke les membres après le premier sur une limite qui est la plus petite de la taille du type de membre ou une limite de *N* octets.

Les valeurs de compression disponibles sont décrites dans le tableau suivant :

|/ZP (argument)|Résultat|
|-|-|
|1|Compresse les structures sur des limites de 1 octet. Identique à **`/Zp`** .|
|2|Compresse les structures sur des limites de 2 octets.|
|4|Compresse les structures sur des limites de 4 octets.|
|8|Compresse les structures sur des limites de 8 octets (valeur par défaut pour x86, ARM et ARM64).|
|16| Compresse les structures sur des limites de 16 octets (valeur par défaut pour x64).|

N’utilisez pas cette option, sauf si vous avez des exigences d’alignement spécifiques.

> [!WARNING]
> Les en-têtes C/C++ du SDK Windows supposent de les **`/Zp8`** compresser en interne. Ne modifiez pas la valeur par défaut lorsque vous incluez les en-têtes SDK Windows, à l’aide **`/Zp`** de sur la ligne de commande ou à l’aide de `#pragma pack` . Dans le cas contraire, votre application risque de provoquer une altération de la mémoire au moment de l’exécution.

Vous pouvez également utiliser le [ `pack` pragma](../../preprocessor/pack.md) pour contrôler la compression de structure. Pour plus d'informations sur l'alignement, consultez :

- [`align`](../../cpp/align-cpp.md)

- [`alignof` And](../../cpp/alignof-operator.md)

- [`__unaligned`](../../cpp/unaligned.md)

- [`/ALIGN` (Alignement des sections)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >  **C/C++**  >  **génération de code** .

1. Modifiez la propriété d' **alignement des membres** de la structure.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md) \
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
