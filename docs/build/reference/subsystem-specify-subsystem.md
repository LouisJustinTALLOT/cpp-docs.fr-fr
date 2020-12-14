---
description: En savoir plus sur:/SUBSYSTEM (spécifier le sous-système)
title: /SUBSYSTEM (Spécifier le sous-système)
ms.date: 11/04/2016
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
ms.openlocfilehash: 18a8ad549cc4aa1e143e43619d549c9eb7ae7324
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236241"
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
Application qui s'exécute dans l'environnement de démarrage de Windows. Pour plus d’informations sur les applications de démarrage, consultez [à propos de BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**CONSOLE**<br/>
Application en mode caractères Win32. Le système d'exploitation fournit une console pour les applications console. Si `main` ou `wmain` est défini pour le code natif, `int main(array<String ^> ^)` est défini pour le code managé ou si vous générez complètement l’application à l’aide de `/clr:safe` , la console est la valeur par défaut.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Sous-systèmes Extensible Firmware Interface. Pour plus d’informations, consultez la spécification EFI. Pour obtenir des exemples, consultez le site Web d’Intel. La version minimale et la version par défaut sont 1,0.

**NATIF**<br/>
Pilotes en mode noyau pour Windows NT. Cette option est généralement réservée aux composants système Windows. Si [/Driver : WDM](driver-windows-nt-kernel-mode-driver.md) est spécifié, native est la valeur par défaut.

**POSIX**<br/>
Application qui s’exécute avec le sous-système POSIX dans Windows NT.

**WINDOWS**<br/>
L’application ne nécessite pas de console, probablement parce qu’elle crée ses propres fenêtres pour l’interaction avec l’utilisateur. Si `WinMain` ou `wWinMain` est défini pour le code natif, `WinMain(HISTANCE *, HINSTANCE *, char *, int)` ou `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` est défini pour le code managé, Windows est la valeur par défaut.

*major* et *Minor*<br/>
Facultatif Spécifiez la version minimale requise du sous-système. Les arguments sont des nombres décimaux compris entre 0 et 65 535. Pour plus d’informations, consultez les notes. Il n’existe aucune limite supérieure pour les numéros de version.

## <a name="remarks"></a>Notes

L’option **/Subsystem** spécifie l’environnement pour l’exécutable.

Le choix du sous-système affecte le symbole de point d’entrée (ou la fonction de point d’entrée) que l’éditeur de liens doit sélectionner.

Les numéros de version *principale* et *secondaire* par défaut et facultatifs pour les sous-systèmes sont les suivants.

|Subsystem|Minimum|Default|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|CONSOLE|5,01 (x86) 5,02 (x64) 6,02 (ARM)|6,00 (x86, x64) 6,02 (ARM)|
|WINDOWS|5,01 (x86) 5,02 (x64) 6,02 (ARM)|6,00 (x86, x64) 6,02 (ARM)|
|NATIF (avec pilote : WDM)|1,00 (x86) 1,10 (x64, ARM)|1,00 (x86) 1,10 (x64, ARM)|
|NATIF (sans/DRIVER : WDM)|4,00 (x86) 5,02 (x64) 6,02 (ARM)|4,00 (x86) 5,02 (x64) 6,02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier Éditeur de liens.

1. Sélectionnez la page de propriétés **système** .

1. Modifiez la `SubSystem` propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
