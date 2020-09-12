---
title: /DRIVER (Pilote Windows NT en mode noyau)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: c935c20d6c1c009cff64d48e0c0122c8b91bbba3
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041157"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Pilote Windows NT en mode noyau)

>/DRIVER [ : ONLY | : WDM]

## <a name="remarks"></a>Remarques

Utilisez l’option **/Driver** de l’éditeur de liens pour générer un pilote en mode noyau Windows NT.

**/Driver : empêche uniquement** l’éditeur de liens d’ajouter le bit **IMAGE_FILE_UP_SYSTEM_ONLY** aux caractéristiques de l’en-tête de sortie pour spécifier qu’il s’agit d’un pilote monoprocesseur (up). Le système d’exploitation refuse de charger un pilote UP sur un système multiprocesseur (MP).

**/Driver : WDM** force l’éditeur de liens à définir le bit de **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** dans le champ DLLCHARACTERISTICS de l’en-tête facultatif.

Si **/Driver** n’est pas spécifié, ces bits ne sont pas définis par l’éditeur de liens.

Si **/Driver** est spécifié :

- **/Fixed : no** est activé. Pour plus d’informations, consultez l’article [/BASE (Adresse de base fixe)](fixed-fixed-base-address.md).

- L’extension du fichier de sortie est définie sur. sys. Utilisez **/out** pour modifier le nom de fichier et l’extension par défaut. Pour plus d’informations, consultez l’article [/OUT (Nom du fichier de sortie)](out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **système** .

1. Modifiez la propriété **Driver** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez la [propriété VCLinkerTool. Driver](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
