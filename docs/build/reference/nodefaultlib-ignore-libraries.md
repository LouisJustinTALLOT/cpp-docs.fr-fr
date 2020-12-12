---
description: En savoir plus sur:/NODEFAULTLIB (ignorer les bibliothèques)
title: /NODEFAULTLIB (Ignorer les bibliothèques)
ms.date: 03/26/2019
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
ms.openlocfilehash: 1443d7ac1e17d464baa829d8297234ae80f3b998
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196709"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignorer les bibliothèques)

> **/NODEFAULTLIB**[__:__*Library*]

## <a name="arguments"></a>Arguments

*Bibliothèque*<br/>
Bibliothèque que l’éditeur de liens doit ignorer lorsqu’il résout des références externes.

## <a name="remarks"></a>Notes

L’option/NODEFAULTLIB indique à l’éditeur de liens de supprimer une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’il recherche lors de la résolution des références externes.

Pour créer un fichier. obj qui ne contient aucune référence aux bibliothèques par défaut, utilisez [/zl (omettre le nom de la bibliothèque par défaut)](zl-omit-default-library-name.md).

Par défaut,/NODEFAULTLIB supprime toutes les bibliothèques par défaut de la liste des bibliothèques qu’il recherche lors de la résolution des références externes. Le paramètre de *bibliothèque* facultatif vous permet de supprimer une bibliothèque spécifiée de la liste des bibliothèques qu’elle recherche lors de la résolution des références externes. Spécifiez une option/NODEFAULTLIB pour chaque bibliothèque que vous souhaitez exclure.

L’éditeur de liens résout les références à des définitions externes en effectuant une recherche dans les bibliothèques que vous spécifiez explicitement, puis dans les bibliothèques par défaut spécifiées avec l’option [/DEFAULTLIB :](defaultlib-specify-default-library.md) , puis dans les bibliothèques par défaut nommées dans les fichiers. obj.

/NODEFAULTLIB :*Library* remplace/DEFAULTLIB :*Library* lorsque le même nom de *bibliothèque* est spécifié dans les deux.

Si vous utilisez/NODEFAULTLIB pour générer votre programme sans la bibliothèque Runtime C, vous devrez peut-être également utiliser [/entry](entry-entry-point-symbol.md) pour spécifier la fonction de point d’entrée dans votre programme. Pour plus d’informations, consultez [Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés entrée de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Sélectionnez la propriété **Ignorer toutes les bibliothèques par défaut** . Vous pouvez également spécifier une liste séparée par des points-virgules des bibliothèques que vous souhaitez ignorer dans la propriété **Ignorer les bibliothèques par défaut spécifiques** . La page de propriétés **ligne de commande** affiche l’effet des modifications apportées à ces propriétés.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Localisez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
