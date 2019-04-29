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
ms.openlocfilehash: f6ed6184f8ae4b3a0f9db3c1f962a2918a185138
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317430"
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

L’option /TSAWARE est activée par défaut pour Windows et les applications de console. Consultez [/SUBSYSTEM](subsystem-specify-subsystem.md) et [/VERSION](version-version-information.md) pour plus d’informations.

/TSAWARE n’est pas valide pour les pilotes, VxDs ou DLL.

Si une application a été liée avec l’option/TSAWARE, DUMPBIN [/HEADERS](headers.md) affiche des informations à cet effet.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **système** page de propriétés.

1. Modifier le **Terminal Server** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Stocker des informations spécifiques à l’utilisateur](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Applications héritées dans un environnement de Services Terminal Server](https://msdn.microsoft.com/library/aa382957.aspx)
