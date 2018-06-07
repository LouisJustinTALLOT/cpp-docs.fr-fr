---
title: /DEFAULTLIB (spécifier la bibliothèque par défaut) | Documents Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9afcaa0e229ec34ba91b4d60a7a4fa9acec2d7e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569779"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Spécifier la bibliothèque par défaut)

Spécifiez une bibliothèque par défaut à Explorer afin de résoudre les références externes.

## <a name="syntax"></a>Syntaxe

> **/DEFAULTLIB**:_bibliothèque_

### <a name="arguments"></a>Arguments

|Argument|Description|
|-|-|
*Bibliothèque*|Le nom d’une bibliothèque à rechercher lors de la résolution des références externes.

## <a name="remarks"></a>Notes

Le **/DEFAULTLIB** option ajoute une *bibliothèque* à la liste des bibliothèques que LINK recherche lors de la résolution des références. Une bibliothèque spécifiée avec **/DEFAULTLIB** est recherchée après les bibliothèques spécifiées explicitement sur la ligne de commande et avant les bibliothèques par défaut nommées dans les fichiers .obj.

Lorsqu’il est utilisé sans arguments, le [/NODEFAULTLIB (ignorer toutes les bibliothèques par défaut)](../../build/reference/nodefaultlib-ignore-libraries.md) option substitue à tous les **/DEFAULTLIB**:*bibliothèque* options. Le **/NODEFAULTLIB**:*bibliothèque* option remplacements **/DEFAULTLIB**:*bibliothèque* lors de la même *bibliothèque*nom est spécifié dans les deux.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Dans **des Options supplémentaires**, entrez un **/DEFAULTLIB**:*bibliothèque* option pour chaque bibliothèque à rechercher. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
- [Options de l’éditeur de liens](../../build/reference/linker-options.md)
