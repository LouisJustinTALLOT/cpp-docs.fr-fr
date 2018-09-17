---
title: -LIBPATH (autre chemin de bibliothèque) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 784281df23b0a8d43625766297b6cbbd20179c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717195"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (Autre chemin de bibliothèque)

```
/LIBPATH:dir
```

## <a name="parameters"></a>Paramètres

*dir*<br/>
Spécifie un chemin d’accès que l’éditeur de liens recherche avant de rechercher le chemin spécifié dans l’option d’environnement LIB.

## <a name="remarks"></a>Notes

Utilisez l’option /LIBPATH pour substituer le chemin de bibliothèque d’environnement. L’éditeur de liens recherche tout d’abord dans le chemin d’accès spécifié par cette option et puis rechercher dans le chemin d’accès spécifié dans la variable d’environnement LIB. Vous pouvez spécifier qu’un seul répertoire pour chaque option /LIBPATH entrée. Si vous souhaitez spécifier plusieurs répertoires, vous devez spécifier plusieurs options /LIBPATH. L’éditeur de liens recherche alors les répertoires spécifiés dans l’ordre.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **général** page de propriétés.

1. Modifier le **répertoires de bibliothèques supplémentaires** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)