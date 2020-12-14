---
description: 'En savoir plus sur : contrôles ActiveX MFC : distribution de contrôles ActiveX'
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
ms.openlocfilehash: faf85bffd9911c38764aea19d1ddb682fd719be1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280714"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Contrôles ActiveX MFC : distribution de contrôles ActiveX

Cet article présente plusieurs problèmes liés à la redistribution des contrôles ActiveX :

- [Versions de contrôle ANSI ou Unicode](#_core_ansi_or_unicode_control_versions)

- [Installation des contrôles ActiveX et des dll redistribuables](#_core_installing_activex_controls_and_redistributable_dlls)

- [Inscrire des contrôles](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a> Versions de contrôle ANSI ou Unicode

Vous devez décider si vous souhaitez expédier une version ANSI ou Unicode du contrôle, ou les deux. Cette décision est basée sur les facteurs de portabilité inhérents aux jeux de caractères ANSI et Unicode.

Les contrôles ANSI, qui fonctionnent sur tous les systèmes d’exploitation Win32, permettent une portabilité maximale entre les différents systèmes d’exploitation Win32. Les contrôles Unicode fonctionnent uniquement sur Windows NT (version 3,51 ou ultérieure), mais pas sur Windows 95 ou Windows 98. Si la portabilité est votre préoccupation principale, expédiez les contrôles ANSI. Si vos contrôles s’exécutent uniquement sous Windows NT, vous pouvez expédier des contrôles Unicode. Vous pouvez également choisir d’expédier et de faire en sorte que votre application installe la version la plus appropriée pour le système d’exploitation de l’utilisateur.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Installation des contrôles ActiveX et des dll redistribuables

Le programme d’installation que vous fournissez avec vos contrôles ActiveX doit créer un sous-répertoire spécial du répertoire Windows et installer les contrôles. Fichiers OCX qu’il contient.

> [!NOTE]
> Utilisez l' `GetWindowsDirectory` API Windows dans votre programme d’installation pour obtenir le nom du répertoire Windows. Vous pouvez dériver le nom du sous-répertoire à partir du nom de votre société ou produit.

Le programme d’installation doit installer les fichiers DLL redistribuables nécessaires dans le répertoire système de Windows. Si l’une des dll est déjà présente sur l’ordinateur de l’utilisateur, le programme d’installation doit comparer ses versions avec les versions que vous installez. Réinstallez un fichier uniquement si son numéro de version est supérieur au fichier déjà installé.

Étant donné que les contrôles ActiveX ne peuvent être utilisés que dans les applications de conteneur OLE, il n’est pas nécessaire de distribuer l’ensemble complet des dll OLE avec vos contrôles. Vous pouvez supposer que la dll OLE standard est installée sur l’application conteneur (ou le système d’exploitation lui-même).

## <a name="registering-controls"></a><a name="_core_registering_controls"></a> Inscrire des contrôles

Avant de pouvoir utiliser un contrôle, vous devez créer des entrées appropriées pour celui-ci dans la base de données d’inscription de Windows. Certains conteneurs de contrôles ActiveX fournissent un élément de menu permettant aux utilisateurs d’inscrire de nouveaux contrôles, mais cette fonctionnalité n’est peut-être pas disponible dans tous les conteneurs. Par conséquent, vous souhaiterez peut-être que votre programme d’installation enregistre les contrôles lorsqu’ils sont installés.

Si vous préférez, vous pouvez écrire votre programme d’installation pour inscrire le contrôle directement à la place.

Utilisez l' `LoadLibrary` API Windows pour charger la dll de contrôle. Ensuite, utilisez `GetProcAddress` pour obtenir l’adresse de la fonction « DllRegisterServer ». Enfin, appelez la `DllRegisterServer` fonction. L’exemple de code suivant illustre une méthode possible, dans laquelle `hLib` stocke le descripteur de la bibliothèque de contrôles et `lpDllEntryPoint` stocke l’adresse de la fonction « DllRegisterServer ».

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

L’un des avantages de l’inscription directe du contrôle est que vous n’avez pas besoin d’appeler et de charger un processus distinct (à savoir, REGSVR32), ce qui réduit le temps d’installation. En outre, étant donné que l’inscription est un processus interne, le programme d’installation peut gérer les erreurs et les situations imprévues mieux qu’un processus externe.

> [!NOTE]
> Avant que votre programme d’installation installe un contrôle ActiveX, il doit appeler `OleInitialize` . Lorsque votre programme d’installation est terminé, appelez `OleUnitialize` . Cela permet de s’assurer que les DLL système OLE sont dans l’état approprié pour l’inscription d’un contrôle ActiveX.

Vous devez inscrire MFCx0.DLL.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
