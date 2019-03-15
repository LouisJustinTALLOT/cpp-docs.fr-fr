---
title: /CLRIMAGETYPE (Spécifier le type d'une image CLR)
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: b2a6df0f778ba079bffefeeacdad22cb398a529a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820674"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Spécifier le type d'une image CLR)

Définir le type d’image CLR dans l’image liée.

## <a name="syntax"></a>Syntaxe

> **/CLRIMAGETYPE:**{**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Notes

L’éditeur de liens accepte des objets natifs et également MSIL objets qui sont compilés à l’aide de [/CLR](clr-common-language-runtime-compilation.md). Le **/CLR : pure** et **/CLR : safe** options du compilateur ont été dépréciées dans Visual Studio 2015 et sont prises en charge dans Visual Studio 2017. Lorsque des objets mixtes dans la même build sont transmis, la vérifiabilité du fichier de sortie résultant est, par défaut, égale à niveau le plus bas de vérifiabilité des modules d’entrée. Par exemple, si vous passez une image native et une image en mode mixte (compilés avec **/CLR**), l’image résultante sera une image en mode mixte.

Vous pouvez utiliser **CLRIMAGETYPE** pour spécifier un niveau inférieur de vérifiabilité, si c’est ce dont vous avez besoin.

Pour plus d’informations sur la façon de déterminer le type d’image CLR d’un fichier, consultez [/CLRHEADER](clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier le **Type d’Image CLR** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Voir aussi

- [Référence de l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
