---
title: /TSAWARE (Créer une application sensible à Terminal Server)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: 4b6cebfd30c6572c2ea7d9a0e59625ac8fd66de1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566593"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Créer une application sensible à Terminal Server)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Notes

L’option /TSAWARE définit un indicateur dans le champ DllCharacteristics IMAGE_OPTIONAL_HEADER de l’en-tête facultatif de l’image du programme. Si cet indicateur est défini, le serveur Terminal Server n’apportera aucune modification à l’application.

Lorsqu’une application n’est pas compatible Terminal Server (également appelé une application héritée), Terminal Server apporte des modifications pour l’application héritée pour qu’il fonctionne correctement dans un environnement multi-utilisateur. Par exemple, Terminal Server créera un dossier virtuel de Windows, telles que chaque utilisateur obtienne un dossier Windows au lieu d’obtenir le répertoire du système Windows. Ainsi, les utilisateurs l’accès à leurs propres fichiers INI. En outre, Terminal Server modifie certains ajustements dans le Registre pour une application héritée. Ces modifications ralentissent le chargement de l’application héritée sur le serveur Terminal Server.

Si une application est compatible Terminal Server, il doit s’appuyer sur les fichiers INI ni écrire dans le **HKEY_CURRENT_USER** Registre pendant l’installation.

Si vous utilisez /TSAWARE et que votre application utilise toujours les fichiers INI, les fichiers sont partagés par tous les utilisateurs du système. Si tel est acceptable, vous pouvez toujours lier votre application avec l’option /TSAWARE ; Sinon, vous devez utiliser : no.

L’option /TSAWARE est activée par défaut pour Windows et les applications de console. Consultez [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) et [/VERSION](../../build/reference/version-version-information.md) pour plus d’informations.

/TSAWARE n’est pas valide pour les pilotes, VxDs ou DLL.

Si une application a été liée avec l’option/TSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) affiche des informations à cet effet.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **système** page de propriétés.

1. Modifier le **Terminal Server** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)<br/>
[Stocker des informations spécifiques à l’utilisateur](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Applications héritées dans un environnement de Services Terminal Server](https://msdn.microsoft.com/library/aa382957.aspx)