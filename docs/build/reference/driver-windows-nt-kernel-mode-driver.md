---
title: -(Pilote Windows NT en Mode noyau) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs:
- C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66291391ed38c27ce7446eccc6fca227c7c2c2d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373112"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Pilote Windows NT en mode noyau)

>/ PILOTE [ : UPONLY | : WDM]

## <a name="remarks"></a>Notes

Utilisez le **c** option de l’éditeur de liens pour générer un pilote de mode noyau Windows NT.

**/DRIVER:UPONLY** entraîne l’éditeur de liens ajouter la **IMAGE_FILE_UP_SYSTEM_ONLY figurant** les caractéristiques dans l’en-tête de sortie pour spécifier qu’il s’agit d’un monoprocesseur pilote au bit. Le système d’exploitation refuse de chargement d’un pilote sur un système multiprocesseur de (MP).

**/ Driver : WDM** entraîne l’éditeur de liens définir le **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** bit dans le champ DllCharacteristics de l’en-tête facultatif.

Si **c** n’est pas spécifié, ces bits ne sont pas définis par l’éditeur de liens.

Si **c** est spécifié :

- **/ Fixed : no** est en vigueur. Pour plus d’informations, consultez l’article [/BASE (Adresse de base fixe)](../../build/reference/fixed-fixed-base-address.md).

- L’extension du fichier de sortie est définie sur .sys. Utilisez **/OUT** pour modifier le nom de fichier par défaut et l’extension. Pour plus d’informations, consultez l’article [/OUT (Nom du fichier de sortie)](../../build/reference/out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **système** page de propriétés.

1. Modifier la **pilote** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez [VCLinkerTool.driver propriété](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Voir aussi

[Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
