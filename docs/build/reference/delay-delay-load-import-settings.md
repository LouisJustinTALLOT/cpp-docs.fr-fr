---
title: /DELAY (Paramètres d'importation à chargement différé)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493006"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (Paramètres d'importation à chargement différé)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Notes

L’option/DELAY contrôle le [chargement différé](linker-support-for-delay-loaded-dlls.md) des dll:

- Le qualificateur UNLOAD indique à la fonction d'assistance de chargement différé de prendre en charge le déchargement explicite de la DLL. La table IAT (Import Address Table) est réinitialisée à sa forme d'origine, ce qui invalide les pointeurs IAT et entraîne leur remplacement.

   Si vous ne sélectionnez pas décharger, tout appel à [FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md) échouera.

- Le qualificateur NOBIND indique à l'éditeur de liens de ne pas inclure dans l'image finale de table IAT pouvant être liée. L'option par défaut consiste à créer la table IAT pouvant être liée pour les DLL chargées en différé. L'image obtenue ne peut pas être liée statiquement. (Les images avec des tables IAT pouvant être liées sont susceptibles d'être liées statiquement avant leur exécution.) Consultez [/Bind](bind.md).

   Si la DLL est liée, la fonction d’assistance tente d’utiliser les informations liées au lieu d’appeler [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) sur chacune des importations référencées. Si l'horodatage ou l'adresse préférée ne correspondent pas à ceux de la DLL chargée, la fonction d'assistance suppose que la table IAT liée est obsolète et continuera comme si la table IAT liée n'existe pas.

   NOBIND augmente la taille de votre image de programme mais peut réduire le temps de chargement de la DLL. Si vous n'avez pas l'intention de lier la DLL, NOBIND empêchera la création de la table IAT liée.

Pour spécifier les dll dont le chargement doit être différé, utilisez l’option [/delayload](delayload-delay-load-import.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définir C++ les propriétés de compilation et de compilation dans Visual Studio](../working-with-project-properties.md).

1. Développez **Propriétés de configuration**, **éditeur de liens**, puis sélectionnez **avancé**.

1. Modifiez la propriété retarder le chargement de la **dll** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
