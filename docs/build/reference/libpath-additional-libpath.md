---
description: En savoir plus sur:/LIBPATH (autre chemin d’accès)
title: /LIBPATH (Autre chemin de bibliothèque)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: 5db7a0f80cb741a65bac5a4dbb7fd79e28b67459
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191028"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (Autre chemin de bibliothèque)

```
/LIBPATH:dir
```

## <a name="parameters"></a>Paramètres

*dir*<br/>
Spécifie un chemin d’accès que l’éditeur de liens recherchera avant de rechercher le chemin d’accès spécifié dans l’option d’environnement LIB.

## <a name="remarks"></a>Notes

Utilisez l’option/LIBPATH pour remplacer le chemin d’accès de la bibliothèque d’environnement. L’éditeur de liens recherche d’abord dans le chemin d’accès spécifié par cette option, puis effectue une recherche dans le chemin d’accès spécifié dans la variable d’environnement LIB. Vous ne pouvez spécifier qu’un seul répertoire pour chaque option/LIBPATH que vous entrez. Si vous souhaitez spécifier plusieurs répertoires, vous devez spécifier plusieurs options/LIBPATH. L’éditeur de liens recherche ensuite les répertoires spécifiés dans l’ordre.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **général** .

1. Modifiez la propriété **répertoires de bibliothèques supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
