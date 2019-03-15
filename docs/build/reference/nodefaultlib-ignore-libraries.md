---
title: /NODEFAULTLIB (Ignorer les bibliothèques)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: cacc1ef312065da5d6e62ddba1040e87fae9d709
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807453"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignorer les bibliothèques)

```
/NODEFAULTLIB[:library]
```

## <a name="arguments"></a>Arguments

*library*<br/>
Une bibliothèque de l’éditeur de liens à ignorer lors de la résolution des références externes.

## <a name="remarks"></a>Notes

L’option /NODEFAULTLIB indique à l’éditeur de liens pour supprimer une ou plusieurs bibliothèques par défaut dans la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes.

Pour créer un fichier .obj qui ne contient-elle pas de références aux bibliothèques par défaut, utilisez [/Zl (omettre le nom de bibliothèque par défaut)](zl-omit-default-library-name.md).

Par défaut, /NODEFAULTLIB supprime toutes les bibliothèques par défaut dans la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes. Le paramètre facultatif *bibliothèque* paramètre vous permet de supprimer une ou plusieurs bibliothèques spécifiées dans la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes. Spécifiez une option /NODEFAULTLIB pour chaque bibliothèque que vous souhaitez exclure.

L’éditeur de liens résout les références aux définitions externes en recherchant d’abord dans les bibliothèques que vous spécifiez explicitement, puis par défaut spécifié de bibliothèques avec l’option /DEFAULTLIB, puis dans les bibliothèques par défaut nommées dans les fichiers .obj.

/ NODEFAULTLIB :*bibliothèque* substitue [/DEFAULTLIB :](defaultlib-specify-default-library.md)*bibliothèque* lors de la même *bibliothèque* nom est spécifié dans les deux.

Si vous utilisez/NODEFAULTLIB, par exemple, pour générer votre programme sans la bibliothèque Runtime C, vous devrez peut-être également utiliser [/Entry](entry-entry-point-symbol.md) pour spécifier le point d’entrée (fonction) dans votre programme. Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée**page de propriétés.

1. Sélectionnez le **ignorer toutes les bibliothèques par défaut** propriété ou spécifier une liste des bibliothèques à ignorer dans le **bibliothèque spécifique ignorée** propriété. Le **ligne de commande** page de propriétés affiche l’effet des modifications que vous apportez à ces propriétés.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
