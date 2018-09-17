---
title: -SUBSYSTEM (spécifier le sous-système) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75e4612104fdc57fd1442f1a35efbf317a60310d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717091"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Spécifier le sous-système)

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>Arguments

**BOOT_APPLICATION**<br/>
Application qui s'exécute dans l'environnement de démarrage de Windows. Pour plus d’informations sur les applications de démarrage, consultez [BCD sur](/previous-versions/windows/desktop/bcd/about-bcd).

**CONSOLE**<br/>
Application en mode caractères Win32. Le système d'exploitation fournit une console pour les applications console. Si `main` ou `wmain` est défini pour le code natif, `int main(array<String ^> ^)` est défini pour le code managé, ou si vous générez complètement l’application à l’aide de `/clr:safe`, CONSOLE est la valeur par défaut.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Les sous-systèmes Extensible Firmware Interface. Consultez la spécification EFI pour plus d’informations. Pour obtenir des exemples, consultez le site Web d’Intel. La version minimale de version et la valeur par défaut est 1.0.

**NATIF**<br/>
Pilotes en mode noyau pour Windows NT. Cette option est généralement réservée pour les composants du système Windows. Si [/Driver : WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) est spécifié, NATIVE est la valeur par défaut.

**POSIX**<br/>
Application qui s’exécute avec le sous-système POSIX sous Windows NT.

**WINDOWS**<br/>
Application ne nécessite pas une console, probablement parce qu’il crée ses propres fenêtres pour l’interaction avec l’utilisateur. Si `WinMain` ou `wWinMain` est défini pour le code natif, ou `WinMain(HISTANCE *, HINSTANCE *, char *, int)` ou `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` est défini pour le code managé, WINDOWS est la valeur par défaut.

*principales* et *mineure*<br/>
(Facultatif) Spécifiez la version minimale requise du sous-système. Les arguments sont des nombres décimaux compris entre 0 et 65 535. Consultez la section Notes pour plus d’informations. Il n’y a aucune limite supérieure pour les numéros de version.

## <a name="remarks"></a>Notes

Le **/SUBSYSTEM** option spécifie l’environnement pour l’exécutable.

Le choix du sous-système affecte le symbole de point d’entrée (ou une fonction de point d’entrée) qui sélectionne l’éditeur de liens.

Le minimum facultatif et par défaut *majeure* et *mineure* numéros de version pour les sous-systèmes sont comme suit.

|Sous-système|Minimum|Par défaut|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|CONSOLE|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|WINDOWS|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|Code natif (avec DRIVER : WDM)|1,00 (x 86) 1.10 (x64, ARM)|1,00 (x 86) 1.10 (x64, ARM)|
|NATIF (sans/Driver : WDM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le dossier de l’éditeur de liens.

1. Sélectionnez le **système** page de propriétés.

1. Modifier le `SubSystem` propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)