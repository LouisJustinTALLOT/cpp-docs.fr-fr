---
title: Paramètres de l'application, Assistant DLL MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.appset
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
ms.openlocfilehash: f021f2023af839413306c1e3d56dc741749cf216
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152044"
---
# <a name="application-settings-mfc-dll-wizard"></a>Paramètres de l'application, Assistant DLL MFC

Utilisez cette page de l’Assistant DLL MFC pour concevoir et ajouter des fonctionnalités de base à un nouveau projet de DLL MFC.

## <a name="dll-type"></a>Type de DLL

Sélectionnez le type de DLL que vous souhaitez créer.

- **DLL MFC normale à l’aide d’une DLL MFC partagée**

   Sélectionnez cette option pour lier la bibliothèque MFC à votre programme sous la forme d’une DLL partagée. À l’aide de cette option, vous ne pouvez pas partager des objets MFC entre votre DLL et l’application appelante. Votre programme effectue des appels à la bibliothèque MFC en cours d’exécution. Cette option réduit les besoins de mémoire et de disque de votre programme s’il est composé de plusieurs fichiers exécutables qui utilisent la bibliothèque MFC. Les programmes Win32 et MFC peuvent appeler des fonctions dans votre DLL. Vous devez redistribuer les DLL MFC avec ce type de projet.

- **DLL MFC normale avec MFC est statiquement lié**

   Sélectionnez cette option pour lier votre programme statiquement à la bibliothèque MFC au moment de la génération. Les programmes Win32 et MFC peuvent appeler des fonctions dans votre DLL. Bien que cette option augmente la taille de votre programme, il est inutile de redistribuer les DLL MFC avec ce type de projet. Vous ne pouvez pas partager des objets MFC entre votre DLL et l’application appelante.

- **DLL d’extension MFC**

   Sélectionnez cette option si vous souhaitez que votre programme pour effectuer des appels à la bibliothèque MFC en cours d’exécution, et si vous souhaitez partager les objets MFC entre votre DLL et l’application appelante. Cette option réduit les besoins de mémoire et de disque de votre programme, s’il est composé de plusieurs fichiers exécutables qui utilisent tous la bibliothèque MFC. Seuls les programmes MFC peuvent appeler des fonctions dans votre DLL. Vous devez redistribuer les DLL MFC avec ce type de projet.

## <a name="additional-features"></a>Fonctionnalités supplémentaires

Sélectionnez si votre DLL MFC prend en charge l’automation et si elle doit prendre en charge les sockets Windows.

- **Automation**

   Sélectionnez **Automation** pour permettre à votre programme manipuler des objets implémentés dans un autre programme. En sélectionnant **Automation** expose également votre programme à d’autres clients Automation. Consultez [Automation](../../mfc/automation.md) pour plus d’informations.

- **Sockets Windows**

   Sélectionnez cette option pour indiquer que votre programme prend en charge les sockets Windows. Les sockets Windows vous permettent d’écrire des programmes qui communiquent sur les réseaux TCP/IP.

   Lorsque votre DLL MFC avec Windows sockets prise en charge est créée, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) initialise prennent en charge pour les sockets et le fichier d’en-tête MFC StdAfx.h comprend AfxSock.h.

## <a name="see-also"></a>Voir aussi

[DLL MFC, Assistant](../../mfc/reference/mfc-dll-wizard.md)<br/>
[Création d’un projet DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md)
