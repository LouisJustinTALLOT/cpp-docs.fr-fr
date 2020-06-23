---
title: Mettre à jour WINVER et _WIN32_WINNT
description: Quand et comment mettre à jour WINVER et _WIN32_WINNT macros dans des projets Visual Studio C++ mis à niveau.
ms.date: 06/19/2020
helpviewer_keywords:
- WINVER in an upgraded Visual Studio C++ project
- _WIN32_WINNT in an upgraded Visual Studio C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
ms.openlocfilehash: a0faed612517bf26cd89473e1aef248fb9e7b33e
ms.sourcegitcommit: 493fd8747f832e1facb9a76c437a25a5c9fb55f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141052"
---
# <a name="update-winver-and-_win32_winnt"></a>Mettre à jour WINVER et _WIN32_WINNT

Lorsque vous utilisez l’SDK Windows, vous pouvez spécifier les versions de Windows sur lesquelles votre code peut s’exécuter. Les macros de préprocesseur **winver** et **_WIN32_WINNT** spécifient la version minimale du système d’exploitation que votre code prend en charge. Visual Studio et le compilateur Microsoft C++ prennent en charge le ciblage de Windows 7 SP1 et versions ultérieures. Les ensembles d’outils plus anciens incluent la prise en charge de Windows XP SP2, Windows Server 2003 SP1, Vista et Windows Server 2008. Windows 95, Windows 98, Windows ME, Windows NT et Windows 2000 ne sont pas pris en charge.

Lorsque vous mettez à niveau un ancien projet, vous devrez peut-être mettre à jour vos macros **winver** ou **_WIN32_WINNT** . S’il s’agit de valeurs affectées à une version non prise en charge de Windows, vous pouvez voir des erreurs de compilation liées à ces macros.

## <a name="remarks"></a>Remarques

Pour modifier les macros, dans un fichier d’en-tête (par exemple, dans *targetver. h*, qui est inclus par certains modèles de projet qui ciblent Windows), ajoutez les lignes suivantes.

```C
#define WINVER 0x0A00
#define _WIN32_WINNT 0x0A00
```

Les macros de l’exemple sont définies pour cibler chaque version du système d’exploitation Windows 10. Les valeurs possibles sont répertoriées dans le fichier d’en-tête Windows *sdkddkver. h*, qui définit des macros pour chaque version principale de Windows. Pour générer votre application afin de prendre en charge une plateforme Windows précédente, incluez *WinSDKVer. h*. Ensuite, définissez les macros **winver** et **_WIN32_WINNT** sur la plateforme la plus ancienne prise en charge avant d’inclure *sdkddkver. h*. Voici les lignes de la version du kit de développement logiciel (SDK) Windows 10 de *sdkddkver. h* qui encodent les valeurs pour chaque version principale de Windows :

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

Pour une approche plus fine du contrôle de version, vous pouvez utiliser les constantes de version NTDDI dans *sdkddkver. h*. Voici quelques-unes des macros définies par *sdkddkver. h* dans le kit de développement logiciel (SDK) Windows 10 version 10.0.18362.0 :

```C
//
// NTDDI version constants
//
#define NTDDI_WIN7                          0x06010000
#define NTDDI_WIN8                          0x06020000
#define NTDDI_WINBLUE                       0x06030000
#define NTDDI_WINTHRESHOLD                  0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10                         0x0A000000  /* ABRACADABRA_THRESHOLD */
#define NTDDI_WIN10_TH2                     0x0A000001  /* ABRACADABRA_WIN10_TH2 */
#define NTDDI_WIN10_RS1                     0x0A000002  /* ABRACADABRA_WIN10_RS1 */
#define NTDDI_WIN10_RS2                     0x0A000003  /* ABRACADABRA_WIN10_RS2 */
#define NTDDI_WIN10_RS3                     0x0A000004  /* ABRACADABRA_WIN10_RS3 */
#define NTDDI_WIN10_RS4                     0x0A000005  /* ABRACADABRA_WIN10_RS4 */
#define NTDDI_WIN10_RS5                     0x0A000006  /* ABRACADABRA_WIN10_RS5 */
#define NTDDI_WIN10_19H1                    0x0A000007  /* ABRACADABRA_WIN10_19H1*/

#define WDK_NTDDI_VERSION                   NTDDI_WIN10_19H1 /* ABRACADABRA_WIN10_19H1 */

//
// masks for version macros
//
#define OSVERSION_MASK      0xFFFF0000
#define SPVERSION_MASK      0x0000FF00
#define SUBVERSION_MASK     0x000000FF

//
// macros to extract various version fields from the NTDDI version
//
#define OSVER(Version)  ((Version) & OSVERSION_MASK)
#define SPVER(Version)  (((Version) & SPVERSION_MASK) >> 8)
#define SUBVER(Version) (((Version) & SUBVERSION_MASK) )
```

Les macros **OSVER**, **SPVER**et **SUBVER** peuvent être utilisées dans votre code pour contrôler la compilation conditionnelle pour différents niveaux de prise en charge des API.

Vous ne verrez peut-être pas toutes ces versions de Windows listées dans *sdkddkver. h* que vous recherchez. Cela signifie que vous utilisez probablement une version antérieure du SDK Windows. Par défaut, les nouveaux projets Windows dans Visual Studio utilisent le kit de développement logiciel (SDK) Windows 10.

> [!NOTE]
> Il n'est pas certain que les valeurs fonctionnent si vous incluez des en-têtes MFC internes dans votre application.

Vous pouvez également définir cette macro à l'aide de l'option de compilateur `/D`. Pour plus d'informations, consultez [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md).

Pour plus d’informations sur les significations de ces macros, consultez [Utilisation des en-têtes Windows](/windows/win32/WinProg/using-the-windows-headers).

## <a name="see-also"></a>Voir aussi

[Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
