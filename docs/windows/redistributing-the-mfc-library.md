---
title: Redistribution de la bibliothèque MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: 7b38299bc39ce282769e40e915847b2220ec28ca
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965609"
---
# <a name="redistributing-the-mfc-library"></a>Redistribution de la bibliothèque MFC

Si vous liez dynamiquement votre application à la bibliothèque MFC, vous devez redistribuer la DLL MFC correspondante. Par exemple, si votre application MFC est conçue à l’aide de la version de MFC fournie avec Visual Studio 2015, vous devez redistribuer mfc140.dll ou mfc140u.dll, selon que votre application est compilée pour la prise en charge Unicode ou de caractères étroits.

> [!NOTE]
>  Les fichiers mfc140.dll ont été omis dans le répertoire des fichiers redistribuables dans Visual Studio 2015 RTM. Vous pouvez utiliser les versions installées par Visual Studio 2015 dans les répertoires Windows\system32 et Windows\syswow64 à la place.

Comme toutes les DLL MFC utilisent la version partagée de la bibliothèque Runtime C (CRT), vous devez également redistribuer le CRT. La version de MFC fournie avec Visual Studio 2015 utilise la bibliothèque CRT universelle, qui est distribuée dans le cadre de Windows 10. Pour exécuter une application MFC générée à l’aide de Visual Studio 2015 sur les versions antérieures de Windows, vous devez redistribuer le CRT universel. Pour plus d’informations sur la redistribution du CRT universel comme composant du système d’exploitation ou à l’aide d’un déploiement local, consultez [Présentation du CRT universel](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/). Pour télécharger le CRT universel pour le déploiement central sur les versions prises en charge de Windows, consultez [Windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234). Les versions redistribuables propres à une architecture de ucrtbase.dll pour le déploiement local se trouvent dans le SDK Windows. Par défaut, Visual Studio les installe dans C:\Program Files (x86) \Windows Kits\10\Redist\ucrt\DLLs\, dans un sous-répertoire propre à l’architecture.

Si votre application est générée à l’aide d’une version antérieure de la bibliothèque MFC, vous devez redistribuer la DLL CRT correspondante à partir du répertoire des fichiers redistribuables. Par exemple, si votre application MFC est générée à l’aide de l’ensemble d’outils Visual Studio 2013 (vc120), vous devez redistribuer le fichier msvcr120.dll. Vous devez également redistribuer le fichier correspondant mfc`<version>`u.dll ou mfc`<version>`.dll.

Si vous liez statiquement votre application à MFC (autrement dit, si vous spécifiez **Utiliser MFC dans une bibliothèque statique** sous l’onglet **Général** dans la boîte de dialogue **Pages de propriétés**), vous n’avez pas à redistribuer de DLL MFC. Toutefois, même si la liaison statique peut fonctionner pour le test et le déploiement interne d’applications, nous vous conseillons de ne pas l’utiliser pour redistribuer MFC. Pour plus d’informations sur les stratégies conseillées pour le déploiement des bibliothèques Visual C++, consultez [Choix d’une méthode de déploiement](choosing-a-deployment-method.md).

Si votre application utilise les classes MFC qui implémentent le contrôle WebBrowser (par exemple, la [classe CHtmlView](../mfc/reference/chtmlview-class.md) ou la [classe CHtmlEditView](../mfc/reference/chtmleditview-class.md)), nous vous recommandons d’installer aussi la version la plus récente de Microsoft Internet Explorer pour que l’ordinateur cible ait les derniers fichiers de contrôle commun. (Au minimum, Internet Explorer 4,0 est requis.) Des informations sur l’installation des composants d’Internet Explorer sont disponibles dans « article 185375 : procédure de création d’une installation exécutable unique d’Internet Explorer » sur le site Web Support Microsoft.

Si votre application utilise les classes de base de données MFC (par exemple, la [classe CRecordset](../mfc/reference/crecordset-class.md) et la [classe CRecordView](../mfc/reference/crecordview-class.md)), vous devez redistribuer ODBC et tous les pilotes ODBC utilisés par votre application.

Si votre application MFC utilise des contrôles Windows Forms, vous devez redistribuer mfcmifc80.dll avec votre application. Cette DLL est un assembly .NET signé avec un nom fort qui peut être redistribué avec une application dans son dossier local d’application ou en le déployant sur le Global Assembly Cache (GAC) à l’aide de [Gacutil.exe (outil Global Assembly Cache)](/dotnet/framework/tools/gacutil-exe-gac-tool).

Si vous redistribuez une DLL MFC, redistribuez la version commerciale et non la version debug. Les versions debug des DLL ne sont pas redistribuables. Les noms des versions debug des DLL MFC se terminent par un « d », par exemple, Mfc140d.dll.

Vous pouvez redistribuer MFC à l’aide de VCRedist_*architecture*.exe, les modules de fusion qui sont installés avec Visual Studio, ou en déployant la DLL MFC dans le même dossier que votre application. Pour plus d’informations sur la redistribution de MFC, consultez [Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md).

## <a name="installation-of-localized-mfc-components"></a>Installation des composants MFC localisés

Si vous décidez de localiser votre application en installant une DLL de localisation MFC, vous devez utiliser les fichiers de fusion redistribuables (.msm). Par exemple, si vous voulez localiser votre application sur un ordinateur x86, vous devez fusionner Microsoft_VC`<version>`_MFCLOC_x86.msm dans le package d’installation d’un ordinateur x86.

Les fichiers .msm redistribuables contiennent les DLL utilisées pour la localisation. À chaque langue prise en charge correspond une DLL. Le processus d’installation installe ces DLL dans le dossier %windir%\system32\ sur l’ordinateur cible.

Pour plus d’informations sur la localisation des applications MFC, consultez [TN057 : localisation des composants MFC](../mfc/tn057-localization-of-mfc-components.md).

Vous pouvez redistribuer les DLL de localisation MFC en déployant la DLL MFC dans le dossier local de votre application. Pour plus d’informations sur la redistribution des bibliothèques MFC, consultez [Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md).

## <a name="see-also"></a>Voir aussi

[Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md)
