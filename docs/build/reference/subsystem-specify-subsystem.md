---
title: -SUBSYSTEM (spécifier le sous-système) | Documents Microsoft
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
ms.openlocfilehash: 70d6f047cf18b8b768d40533e2acc6cb2f649327
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379001"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Spécifier le sous-système)
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 Application qui s'exécute dans l'environnement de démarrage de Windows. Pour plus d’informations sur les applications de démarrage, consultez [BCD sur](http://msdn.microsoft.com/library/windows/desktop/aa362639).  
  
 CONSOLE  
 Application Win32 en mode caractère. Le système d'exploitation fournit une console pour les applications console. Si `main` ou `wmain` est défini pour le code natif, `int main(array<String ^> ^)` est défini pour le code managé, ou si vous générez complètement l’application à l’aide de `/clr:safe`, CONSOLE est la valeur par défaut.  
  
 Interface micrologicielle extensible  
 Les sous-systèmes EFI_ *. Consultez la spécification EFI pour plus d’informations. Par exemple, consultez le site Web d’Intel. La version minimale de version et la valeur par défaut est 1,0.  
  
 NATIVE  
 Pilotes en mode noyau pour Windows NT. Cette option est généralement réservée pour les composants du système Windows. Si [/Driver : WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) est spécifié, NATIVE est la valeur par défaut.  
  
 POSIX  
 Application qui s’exécute avec le sous-système POSIX sous Windows NT.  
  
 WINDOWS  
 Application ne requiert pas une console, probablement parce qu’il crée ses propres fenêtres d’interaction avec l’utilisateur. Si `WinMain` ou `wWinMain` est défini pour le code natif, ou `WinMain(HISTANCE *, HINSTANCE *, char *, int)` ou `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` est défini pour le code managé, WINDOWS est la valeur par défaut.  
  
 `Major` et `minor` (facultatif)  
 Spécifiez la version minimale requise du sous-système. Les arguments sont des nombres décimaux compris entre 0 et 65 535. Consultez la section Notes pour plus d’informations. Il n’y a aucune limite supérieure pour les numéros de version.  
  
## <a name="remarks"></a>Notes  
 L’option /SUBSYSTEM spécifie l’environnement pour le fichier exécutable.  
  
 Le choix du sous-système affecte le symbole de point d’entrée (ou une fonction de point d’entrée) que l’éditeur de liens sélectionnez.  
  
 Le minimum facultatif et la valeur par défaut `major` et `minor` les numéros de version pour les sous-systèmes sont les suivantes.  
  
|Sous-système|Minimum|Par défaut|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|CONSOLE|5.01 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6,00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|WINDOWS|5.01 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6,00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|Code natif (avec DRIVER : WDM)|1,00 (x 86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|1,00 (x 86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|  
|NATIF (sans/Driver : WDM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, UN EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le dossier de l’éditeur de liens.  
  
3.  Sélectionnez le **système** page de propriétés.  
  
4.  Modifier le `SubSystem` propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)