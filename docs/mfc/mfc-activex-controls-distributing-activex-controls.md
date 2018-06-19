---
title: 'Contrôles ActiveX MFC : Distribution de contrôles ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7c6658c972b9d9cdeececd43a89ac424964d2289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358805"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Contrôles ActiveX MFC : distribution de contrôles ActiveX
Cet article présente plusieurs problèmes liés à la redistribution de contrôles ActiveX :  
  
-   [ANSI ou Unicode du contrôle des Versions](#_core_ansi_or_unicode_control_versions)  
  
-   [L’installation des contrôles ActiveX et les DLL redistribuables](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [Inscrire des contrôles](#_core_registering_controls)  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI ou Unicode du contrôle des Versions  
 Vous devez décider si vous souhaitez fournir une version ANSI ou Unicode du contrôle, ou les deux. Cette décision est basée sur des facteurs de portabilité inhérents aux jeux de caractères ANSI et Unicode.  
  
 Autorisent les contrôles ANSI, qui fonctionnent sur tous les systèmes d’exploitation de Win32, pour une portabilité maximale entre les différents systèmes d’exploitation Win32. Les contrôles Unicode fonctionnent sous Windows NT (version 3.51 ou version ultérieure) uniquement, mais pas sur Windows 95 ou Windows 98. Si la portabilité est votre souci principal, fournissez des contrôles ANSI. Si vos contrôles seront exécute uniquement sous Windows NT, vous pouvez expédier les contrôles Unicode. Vous pouvez également choisir d’expédier les deux et d’installer la version la plus appropriée pour le système d’exploitation de l’utilisateur de votre application.  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> L’installation des contrôles ActiveX et les DLL redistribuables  
 Le programme d’installation que vous fournissez à vos contrôles ActiveX doit créer un sous-répertoire spécial dans le répertoire Windows et installez les contrôles. OCX du contrôle.  
  
> [!NOTE]
>  Utiliser les fenêtres **GetWindowsDirectory** API dans votre programme d’installation pour obtenir le nom du répertoire Windows. Vous souhaiterez dériver le nom du sous-répertoire du nom de votre société ou produit.  
  
 Le programme d’installation doit installer les fichiers DLL redistribuables nécessaires dans le répertoire système Windows. Si une des DLL sont déjà présente sur l’ordinateur de l’utilisateur, le programme d’installation doit comparer leurs versions avec les versions que vous installez. Réinstallez un fichier uniquement si son numéro de version est supérieure à celle du fichier déjà installé.  
  
 Étant donné que les contrôles ActiveX peuvent être utilisés uniquement dans des applications conteneur OLE, il est inutile de distribuer le jeu complet de DLL OLE avec vos contrôles. Vous pouvez supposer que l’application conteneur (ou le système d’exploitation lui-même) a la DLL OLE standard.  
  
##  <a name="_core_registering_controls"></a> Inscrire des contrôles  
 Avant de pouvoir utiliser un contrôle, les entrées appropriées doivent être créées pour elle dans la base de données d’inscription de Windows. Certains conteneurs de contrôles ActiveX fournissent un élément de menu pour les utilisateurs à inscrire de nouveaux contrôles, mais cette fonctionnalité n’est peut-être pas disponible dans tous les conteneurs. Par conséquent, vous devrez votre programme d’installation pour inscrire les contrôles lorsqu’ils sont installés.  
  
 Si vous préférez, vous pouvez écrire votre programme d’installation pour inscrire le contrôle directement à la place.  
  
 Utilisez le **LoadLibrary** API Windows pour charger la DLL du contrôle. Ensuite, utilisez **GetProcAddress** pour obtenir l’adresse de la fonction « DllRegisterServer ». Enfin, appelez le `DllRegisterServer` (fonction). L’exemple de code suivant illustre une méthode possible, où `hLib` stocke le descripteur de la bibliothèque de contrôles, et `lpDllEntryPoint` stocke l’adresse de la fonction « DllRegisterServer ».  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 L’avantage de l’enregistrement du contrôle directement, que vous ne souhaitez pas appeler et de charger un processus séparé (à savoir, REGSVR32), ce qui réduit le temps d’installation. En outre, étant donné que l’enregistrement est un processus interne, le programme d’installation peut gérer les erreurs et situations imprévues meilleures que celles d’un processus externe peuvent.  
  
> [!NOTE]
>  Avant que votre programme d’installation installe un contrôle ActiveX, il doit appeler **OleInitialize**. Lorsque votre programme d’installation est terminée, appelez **OleUnitialize**. Cela garantit que les DLL système OLE sont dans un état approprié pour l’inscription d’un contrôle ActiveX.  
  
 Vous devez enregistrer MFCx0.DLL.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

