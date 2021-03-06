---
description: En savoir plus sur:/TSAWARE (créer une application prenant en charge Terminal Server)
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
ms.openlocfilehash: 6086bdcdf4aa41f116491a602286a0c8410bd61d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171970"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Créer une application sensible à Terminal Server)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Notes

L’option/TSAWARE définit un indicateur dans le champ IMAGE_OPTIONAL_HEADER DllCharacteristics dans l’en-tête facultatif de l’image du programme. Si cet indicateur est défini, le serveur Terminal Server n’apportera aucune modification à l’application.

Lorsqu’une application n’est pas Terminal Server prise en charge (également appelée application héritée), Terminal Server apporte certaines modifications à l’application héritée pour la faire fonctionner correctement dans un environnement multi-utilisateur. Par exemple, Terminal Server créera un dossier Windows virtuel, de sorte que chaque utilisateur obtient un dossier Windows au lieu d’obtenir le répertoire Windows du système. Cela permet aux utilisateurs d’accéder à leurs propres fichiers INI. En outre, Terminal Server apporte des ajustements au registre pour une application héritée. Ces modifications ralentissent le chargement de l’application héritée sur Terminal Server.

Si une application ne prend Terminal Server en charge, elle ne doit pas s’appuyer sur les fichiers INI ni écrire dans le Registre **HKEY_CURRENT_USER** lors de l’installation.

Si vous utilisez/TSAWARE et que votre application utilise toujours les fichiers INI, les fichiers sont partagés par tous les utilisateurs du système. Si cela est acceptable, vous pouvez toujours lier votre application à l’aide de la fonction/TSAWARE. Sinon, vous devez utiliser/TSAWARE : NO.

L’option/TSAWARE est activée par défaut pour les applications de console et Windows. Pour plus d’informations, consultez [/Subsystem](subsystem-specify-subsystem.md) et [/version](version-version-information.md) .

L'/TSAWARE n’est pas valide pour les pilotes ou les dll.

Si une application a été liée avec l’utilitaire/TSAWARE, DUMPBIN [/headers](headers.md) affiche des informations à cet effet.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **système** .

1. Modifiez la propriété **Terminal Server** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Stockage des informations de User-Specific](/windows/win32/TermServ/storing-user-specific-information)<br/>
[Applications héritées dans un environnement de services Terminal Server](/previous-versions/aa382957(v=vs.85))
