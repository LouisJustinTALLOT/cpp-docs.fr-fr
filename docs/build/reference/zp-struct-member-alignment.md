---
title: /Zp (Alignement des membres de la structure)
ms.date: 04/04/2019
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
ms.openlocfilehash: d76cd93c7af4228bff8f73fa3bcbf40fa149b0be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315909"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Alignement des membres de la structure)

Contrôle la façon dont les membres d’une structure sont compressés en mémoire et spécifie la même compression pour toutes les structures dans un module.

## <a name="syntax"></a>Syntaxe

> **/Zp**[**1**|**2**|**4**|**8**|**16**]

## <a name="remarks"></a>Notes

Le **/Zp**_n_ option indique au compilateur où stocker chaque membre de structure. Le compilateur stocke des membres après le premier sur une limite qui est la plus petite de la taille du type du membre, ou un *n*-limite d’octets.

Les valeurs de compression disponibles sont décrites dans le tableau suivant :

|/Zp argument|Effet|
|-|-|
|1|Compresse les structures sur des limites de 1 octets. Identique à **/Zp**.|
|2|Compresse les structures sur des limites de 2 octets.|
|4|Compresse les structures sur des limites de 4 octets.|
|8|Compresse les structures sur des limites de 8 octets (valeur par défaut pour x86, ARM et ARM64).|
|16| Compresse les structures sur des limites de 16 octets (valeur par défaut pour x64).|

N’utilisez pas cette option, sauf si vous avez des exigences spécifiques d’alignement.

> [!WARNING]
> En-têtes de C++ dans le Kit de développement Windows et de supposent **/Zp8** de livraison en interne. Mémoire corruption peut se produire si le **/Zp** paramètre est modifié dans les en-têtes Windows SDK. Les en-têtes ne sont pas affectés par les **/Zp** option que vous définissez sur la ligne de commande.

Vous pouvez également utiliser [pack](../../preprocessor/pack.md) à la compression de structure de contrôle. Pour plus d'informations sur l'alignement, consultez :

- [align](../../cpp/align-cpp.md)

- [__alignof, opérateur](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [/ALIGN (Alignement des sections)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **génération de Code** page de propriétés.

1. Modifier le **alignement des membres de Struct** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md) \
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
