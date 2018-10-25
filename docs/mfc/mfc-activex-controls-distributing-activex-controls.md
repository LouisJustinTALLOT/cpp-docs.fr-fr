---
title: 'Contrôles ActiveX MFC : Distribution de contrôles ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 734707256bb97e25452c45829fd99a1e0fb06fd0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060310"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Contrôles ActiveX MFC : distribution de contrôles ActiveX

Cet article décrit plusieurs problèmes liés à la redistribution de contrôles ActiveX :

- [ANSI ou Unicode du contrôle des Versions](#_core_ansi_or_unicode_control_versions)

- [Installation des contrôles ActiveX et DLL redistribuables](#_core_installing_activex_controls_and_redistributable_dlls)

- [Inscrire des contrôles](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).

##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI ou Unicode du contrôle des Versions

Vous devez décider s’il faut fournir une version ANSI ou Unicode du contrôle, ou les deux. Cette décision est basée sur des facteurs de portabilité inhérents aux jeux de caractères ANSI et Unicode.

Les contrôles ANSI, qui fonctionnent sur tous les systèmes d’exploitation de Win32, permettent une portabilité maximale entre les différents systèmes d’exploitation Win32. Les contrôles Unicode fonctionnent sur uniquement Windows NT (version 3.51 ou version ultérieure), mais pas sur Windows 95 ou Windows 98. Si la portabilité est votre préoccupation principale, fournissez des contrôles ANSI. Si vos contrôles seront exécutera uniquement sur Windows NT, vous pouvez expédier les contrôles Unicode. Vous pouvez également choisir de fournir les deux et que votre application à installer la version la plus appropriée pour le système d’exploitation de l’utilisateur.

##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Installation des contrôles ActiveX et DLL redistribuables

Le programme d’installation que vous fournissez à vos contrôles ActiveX doit créer un sous-répertoire du répertoire Windows spécial et installez les contrôles. OCX du contrôle.

> [!NOTE]
>  Utiliser le Windows `GetWindowsDirectory` API dans votre programme d’installation pour obtenir le nom du répertoire Windows. Voulez-vous dériver le nom du sous-répertoire du nom de votre société ou produit.

Le programme d’installation doit installer les fichiers DLL redistribuables nécessaires dans le répertoire de système de Windows. Si une DLL sont déjà présente sur l’ordinateur de l’utilisateur, le programme d’installation doit comparer leurs versions avec les versions que vous installez. Réinstallez un fichier uniquement si son numéro de version est supérieure à celle du fichier déjà installé.

Étant donné que les contrôles ActiveX peuvent être utilisés uniquement dans les applications de conteneur OLE, il est inutile de distribuer l’ensemble des DLL OLE avec vos contrôles. Vous pouvez supposer que l’application conteneur (ou le système d’exploitation lui-même) a la DLL OLE standard.

##  <a name="_core_registering_controls"></a> Inscrire des contrôles

Avant de pouvoir utiliser un contrôle, les entrées appropriées doivent être créées pour elle dans la base de données d’inscription Windows. Certains conteneurs de contrôles ActiveX fournissent un élément de menu pour les utilisateurs à inscrire de nouveaux contrôles, mais cette fonctionnalité n’est peut-être pas disponible dans tous les conteneurs. Par conséquent, vous devrez votre programme d’installation pour inscrire les contrôles quand elles sont installées.

Si vous préférez, vous pouvez écrire votre programme d’installation pour inscrire le contrôle directement à la place.

Utilisez le `LoadLibrary` API Windows pour charger la DLL du contrôle. Ensuite, utilisez `GetProcAddress` pour obtenir l’adresse de la fonction « DllRegisterServer ». Enfin, appelez le `DllRegisterServer` (fonction). L’exemple de code suivant montre une méthode possible, où `hLib` stocke le handle de la bibliothèque de contrôle, et `lpDllEntryPoint` stocke l’adresse de la fonction « DllRegisterServer ».

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

L’avantage de l’enregistrement du contrôle directement est qu’il est inutile appeler et charger un processus séparé (à savoir, REGSVR32), ce qui réduit le temps d’installation. En outre, étant donné que l’inscription est un processus interne, le programme d’installation peut gérer les erreurs et des situations imprévues mieux que d’un processus externe peuvent.

> [!NOTE]
>  Avant que votre programme d’installation installe un contrôle ActiveX, il doit appeler `OleInitialize`. Lorsque votre programme d’installation est terminé, appelez `OleUnitialize`. Cela garantit que les DLL système OLE sont dans l’état approprié pour l’inscription d’un contrôle ActiveX.

Vous devez enregistrer MFCx0.DLL.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

