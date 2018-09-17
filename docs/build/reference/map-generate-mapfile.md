---
title: -MAP (générer fichier de mappage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c39134f45b1a044a76139d33aa9e761a0f14c8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725580"
---
# <a name="map-generate-mapfile"></a>/MAP (Générer fichier de mappage)

```
/MAP[:filename]
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Un nom spécifié par l’utilisateur pour le fichier de mappage. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

L’option /MAP indique à l’éditeur de liens pour créer un fichier de mappage.

Par défaut, l’éditeur de liens nomme le fichier de mappage avec le nom de base du programme et l’extension .map. Le paramètre facultatif *filename* vous permet de substituer le nom par défaut pour un fichier de mappage.

Un fichier de mappage est un fichier texte qui contient les informations suivantes sur le programme lié :

- Le nom du module, qui est le nom du fichier de base

- L’horodatage de l’en-tête du fichier de programme (pas du système de fichiers)

- Une liste de groupes dans le programme, avec l’adresse de début de chaque groupe (en tant que *section*:*décalage*), longueur et nom du groupe de classe

- Une liste de symboles publics avec chaque adresse (en tant que *section*:*décalage*), nom du symbole, adresse et le fichier .obj dans lequel le symbole est défini.

- Le point d’entrée (en tant que *section*:*décalage*)

Le [/Map.](../../build/reference/mapinfo-include-information-in-mapfile.md) option spécifie des informations supplémentaires à inclure dans le fichier de mappage.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modifier le **générer un fichier de mappage** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)