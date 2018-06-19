---
title: -TSAWARE (créer une Application prenant en charge du serveur Terminal Server) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs:
- C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e386c9024ea7736adb2766488c1c51c80ff7177b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379131"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Créer une application sensible à Terminal Server)
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 L’option /TSAWARE définit un indicateur dans le champ DllCharacteristics IMAGE_OPTIONAL_HEADER de l’en-tête facultatif de l’image du programme. Si cet indicateur est défini, le serveur Terminal Server n’apportera aucune modification à l’application.  
  
 Lorsqu’une application n’est pas compatible Terminal Server (également appelé une application héritée), serveur Terminal Server apporte des modifications pour l’application héritée pour qu’il fonctionne correctement dans un environnement multi-utilisateur. Par exemple, serveur Terminal Server créera un dossier virtuel de Windows, telles que chaque utilisateur obtienne un dossier Windows au lieu d’obtenir le répertoire du système Windows. Cela fournit aux utilisateurs un accès à leurs propres fichiers INI. En outre, Terminal Server modifie certains ajustements dans le Registre pour une application héritée. Ces modifications ralentissent le chargement de l’application héritée sur le serveur Terminal Server.  
  
 Si une application est compatible Terminal Server, il doit s’appuient sur les fichiers INI ni écrire dans le **HKEY_CURRENT_USER** Registre pendant l’installation.  
  
 Si vous utilisez /TSAWARE et que votre application utilise toujours les fichiers INI, les fichiers seront partagés par tous les utilisateurs du système. Si ce n’est acceptable, vous pouvez toujours lier votre application avec l’option /TSAWARE ; Sinon, vous devez utiliser/TSAWARE : no.  
  
 L’option /TSAWARE est activée par défaut pour les applications Windows et console. Consultez [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) et [/VERSION](../../build/reference/version-version-information.md) pour plus d’informations.  
  
 /TSAWARE n’est pas valide pour les pilotes, VXD ou DLL.  
  
 Si une application a été liée avec l’option/TSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) affiche des informations à cet effet.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **système** page de propriétés.  
  
4.  Modifier la **Terminal Server** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [Stocker des informations spécifiques à l’utilisateur](http://msdn.microsoft.com/library/aa383452)   
 [Applications héritées dans un environnement de Services Terminal Server](https://msdn.microsoft.com/en-us/library/aa382957.aspx)