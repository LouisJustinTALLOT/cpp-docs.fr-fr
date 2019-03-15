---
title: /DEFAULTLIB (Spécifier la bibliothèque par défaut)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 0b7d4569c7be70bd97094ebbe09a7ae462331983
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815955"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Spécifier la bibliothèque par défaut)

Spécifiez une bibliothèque par défaut à Explorer afin de résoudre des références externes.

## <a name="syntax"></a>Syntaxe

> **/DEFAULTLIB**:_bibliothèque_

### <a name="arguments"></a>Arguments

*library*<br/>
Le nom d’une bibliothèque à rechercher lors de la résolution des références externes.

## <a name="remarks"></a>Notes

Le **/DEFAULTLIB** option ajoute une *bibliothèque* à la liste des bibliothèques que LINK recherche lors de la résolution des références. Une bibliothèque spécifiée avec **/DEFAULTLIB** est recherchée après les bibliothèques spécifiées explicitement sur la ligne de commande et avant les bibliothèques par défaut nommées dans les fichiers .obj.

Lorsqu’il est utilisé sans arguments, le [/NODEFAULTLIB (ignorer toutes les bibliothèques par défaut)](nodefaultlib-ignore-libraries.md) option substitue à tous les **/DEFAULTLIB**:*bibliothèque* options. Le **/NODEFAULTLIB**:*bibliothèque* option remplacements **/DEFAULTLIB**:*bibliothèque* lors de la même *bibliothèque*nom est spécifié dans les deux.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Dans **des Options supplémentaires**, entrez un **/DEFAULTLIB**:*bibliothèque* option pour chaque bibliothèque à rechercher. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Référence de l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
