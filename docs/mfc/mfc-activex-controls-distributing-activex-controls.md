---
title: 'Contrôles ActiveX MFC : distribution de contrôles ActiveX'
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364627"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Contrôles ActiveX MFC : distribution de contrôles ActiveX

Cet article traite de plusieurs questions liées à la redistribution des contrôles ActiveX :

- [Versions de contrôle ANSI ou Unicode](#_core_ansi_or_unicode_control_versions)

- [Installation de contrôles ActiveX et DLLs redistributables](#_core_installing_activex_controls_and_redistributable_dlls)

- [Enregistrement des contrôles](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>Versions de contrôle ANSI ou Unicode

Vous devez décider d’expédier une version ANSI ou Unicode du contrôle, ou les deux. Cette décision est basée sur des facteurs de portabilité inhérents aux ensembles de caractères ANSI et Unicode.

Les contrôles ANSI, qui fonctionnent sur tous les systèmes d’exploitation Win32, permettent une portabilité maximale entre les différents systèmes d’exploitation Win32. Les contrôles Unicode fonctionnent uniquement sur Windows NT (version 3.51 ou plus tard), mais pas sur Windows 95 ou Windows 98. Si la portabilité est votre principale préoccupation, le navire ANSI contrôle. Si vos contrôles ne s’exécutent que sur Windows NT, vous pouvez expédier les commandes Unicode. Vous pouvez également choisir d’expédier les deux et faire installer votre application la version la plus appropriée pour le système d’exploitation de l’utilisateur.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Installation de contrôles ActiveX et DLLs redistributables

Le programme de configuration que vous fournissez avec vos commandes ActiveX doit créer une sous-direction spéciale de l’annuaire Windows et installer les contrôles ' . Fichiers OCX dedans.

> [!NOTE]
> Utilisez l’API Windows `GetWindowsDirectory` dans votre programme d’installation pour obtenir le nom de l’annuaire Windows. Vous pouvez tirer le nom sous-direction du nom de votre entreprise ou produit.

Le programme de configuration doit installer les fichiers DLL redistribuables nécessaires dans l’annuaire du système Windows. Si l’un des DLL sont déjà présents sur la machine de l’utilisateur, le programme de configuration doit comparer leurs versions avec les versions que vous installez. Réinstaller un fichier uniquement si son numéro de version est plus élevé que le fichier déjà installé.

Étant donné que les contrôles ActiveX ne peuvent être utilisés que dans les applications de conteneurs OLE, il n’est pas nécessaire de distribuer l’ensemble complet des DLL OLE avec vos commandes. Vous pouvez supposer que l’application contenant (ou le système d’exploitation lui-même) a installé les DLL OLE standard.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Enregistrement des contrôles

Avant qu’un contrôle puisse être utilisé, des entrées appropriées doivent être créées pour elle dans la base de données d’enregistrement Windows. Certains conteneurs de contrôle ActiveX fournissent un élément de menu pour les utilisateurs d’enregistrer de nouveaux contrôles, mais cette fonctionnalité peut ne pas être disponible dans tous les conteneurs. Par conséquent, vous pouvez vouloir que votre programme d’installation enregistre les commandes lorsqu’elles sont installées.

Si vous préférez, vous pouvez écrire votre programme d’installation pour enregistrer le contrôle directement à la place.

Utilisez `LoadLibrary` l’API Windows pour charger le contrôle DLL. Ensuite, `GetProcAddress` utilisez-le pour obtenir l’adresse de la fonction "DllRegisterServer". Enfin, appelez `DllRegisterServer` la fonction. L’échantillon de code suivant démontre `hLib` une méthode possible, où stocke la poignée de la bibliothèque de contrôle, et `lpDllEntryPoint` stocke l’adresse de la fonction "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

L’avantage d’enregistrer le contrôle directement est que vous n’avez pas besoin d’invoquer et de charger un processus distinct (à savoir, REGSVR32), réduisant le temps d’installation. En outre, parce que l’enregistrement est un processus interne, le programme d’installation peut gérer les erreurs et les situations imprévues mieux qu’un processus externe peut.

> [!NOTE]
> Avant que votre programme d’installation installe `OleInitialize`un contrôle ActiveX, il devrait appeler . Lorsque votre programme d’installation est terminé, appelez `OleUnitialize`. Cela garantit que les DLL système OLE sont dans le bon état pour enregistrer un contrôle ActiveX.

Vous devez enregistrer MFCx0.DLL.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
