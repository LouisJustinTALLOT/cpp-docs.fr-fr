---
title: /CLRIMAGETYPE (spécifier le Type d’Image CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5efb2e73e854591be7134753cec21a708fff3e5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705008"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Spécifier le type d'une image CLR)

Définir le type d’image CLR dans l’image liée.

## <a name="syntax"></a>Syntaxe

> **/ CLRIMAGETYPE :**{**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>Notes

L’éditeur de liens accepte des objets natifs, et également MSIL objets qui sont compilées à l’aide de [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Le **/CLR : pure** et **/CLR : safe** options du compilateur ont été déconseillées dans Visual Studio 2015 et sont prises en charge dans Visual Studio 2017. Lorsque des objets mixtes dans la même build sont transmis, la vérifiabilité du fichier de sortie résultant est, par défaut, égale à niveau le plus bas de vérifiabilité des modules d’entrée. Par exemple, si vous passez une image native et une image en mode mixte (compilée à l’aide de **/CLR**), l’image résultante est une image en mode mixte.

Vous pouvez utiliser **CLRIMAGETYPE** pour spécifier un niveau inférieur de vérifiabilité, si c’est ce dont vous avez besoin.

Pour plus d’informations sur la façon de déterminer le type d’image CLR d’un fichier, consultez [/CLRHEADER](../../build/reference/clrheader.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le **propriétés de Configuration** nœud.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier la **Type d’Image CLR** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
- [Options de l’éditeur de liens](../../build/reference/linker-options.md)
