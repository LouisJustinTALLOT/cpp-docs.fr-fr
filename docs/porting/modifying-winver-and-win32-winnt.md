---
title: Mettre à jour WINVER et _WIN32_WINNT
ms.date: 09/04/2017
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: 0cfdb3d065a85bd02ef21de9c4c5282cf54fcb2a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627258"
---
# <a name="update-winver-and-_win32_winnt"></a>Mettre à jour WINVER et _WIN32_WINNT

Visual C++ ne prend plus en charge le ciblage de Windows 95, Windows 98, Windows ME, Windows NT ou Windows 2000. Si vos macros **WINVER** ou **_WIN32_WINNT** sont affectées à l'une de ces versions de Windows, vous devez les changer. Quand vous mettez à niveau un projet créé à l'aide d'une version antérieure de Visual C ++, vous pouvez voir s'afficher des erreurs de compilation liées aux macros **WINVER** ou **_WIN32_WINNT** , si ces dernières sont affectées à une version de Windows qui n'est plus prise en charge.

## <a name="remarks"></a>Notes

Pour modifier les macros, ajoutez les lignes suivantes à un fichier d'en-tête (par exemple, targetver.h, qui est inclus quand vous créez un projet ciblant Windows).

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Ceci permet de cibler le système d'exploitation Windows 10. Ces valeurs sont répertoriées dans le fichier d'en-tête Windows SDKDDKVer.h, qui définit également des macros pour chaque version de Windows. Vous devez ajouter l'instruction #define avant d'inclure SDKDDKVer.h. Voici les lignes de la version Windows 10 de SDKDDKVer.h qui codent les valeurs pour chaque version de Windows :

```C
//
// _WIN32_WINNT version constants
//
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10
```

Si vous ne voyez pas toutes ces versions de Windows dans votre copie de SDKDDKVer.h, vous utilisez probablement une ancienne version du SDK Windows. Par défaut, les projets Win32 dans Visual Studio 2017 utilisent le SDK Windows 10.

> [!NOTE]
> Il n'est pas certain que les valeurs fonctionnent si vous incluez des en-têtes MFC internes dans votre application.

Vous pouvez également définir cette macro à l'aide de l'option de compilateur `/D`. Pour plus d’informations, consultez [/D (Définitions de préprocesseur)](../build/reference/d-preprocessor-definitions.md).

Pour plus d’informations sur les significations de ces macros, consultez [Utilisation des en-têtes Windows](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Voir aussi

[Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
