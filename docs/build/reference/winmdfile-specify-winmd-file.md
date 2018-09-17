---
title: -WINMDFILE (spécifier un fichier winmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdea558f1c9a56e68a8e2e61703b92ea569a0629
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709889"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (spécifier un fichier winmd)

Spécifie le nom de fichier pour le fichier de sortie de métadonnées du Runtime Windows (.winmd) qui est généré par le [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) option de l’éditeur de liens.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Notes

Utilisez la valeur spécifiée dans `filename` pour remplacer le nom de fichier .winmd par défaut (`binaryname`.winmd). Notez que vous n’ajoutez pas de « .winmd » au `filename`.  Si plusieurs valeurs sont répertoriés sur le **/WINMDFILE** ligne de commande, le dernier est prioritaire.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **fichier de métadonnées Windows** , entrez l’emplacement du fichier.

## <a name="see-also"></a>Voir aussi

[/ WINMD (générer des métadonnées de Windows)](../../build/reference/winmd-generate-windows-metadata.md)
[définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)