---
description: En savoir plus sur:/CLRIMAGETYPE (spécifier le type d’image CLR)
title: /CLRIMAGETYPE (Spécifier le type d'une image CLR)
ms.date: 05/16/2019
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: 7c499eeddcacd674a9dfc2134e059fd8b3b9a6b6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179146"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Spécifier le type d'une image CLR)

Définissez le type d’image CLR dans l’image liée.

## <a name="syntax"></a>Syntaxe

> **/CLRIMAGETYPE:**{**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Notes

L’éditeur de liens accepte les objets natifs ainsi que les objets MSIL qui sont compilés à l’aide de [/clr](clr-common-language-runtime-compilation.md). Les options de compilateur **/clr:pure** et **/clr:safe** ont été dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017 et ultérieur. Quand des objets mixtes de la même build sont passés, la vérifiabilité du fichier de sortie obtenu est, par défaut, égale au niveau de vérifiabilité le plus bas des modules d’entrée. Par exemple, si vous passez une image native et une image en mode mixte (compilées à l’aide de **/clr**), l’image obtenue sera une image en mode mixte.

Vous pouvez utiliser **/CLRIMAGETYPE** pour spécifier un niveau de vérifiabilité inférieur, si c’est ce dont vous avez besoin.

Pour plus d’informations sur la façon de déterminer le type d’image CLR d’un fichier, consultez [/CLRHEADER](clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **Avancé**.

1. Modifiez la propriété **Type d’image CLR**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
