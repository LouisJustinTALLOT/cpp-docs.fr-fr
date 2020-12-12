---
description: 'En savoir plus sur : paramètres de l’application, Assistant DLL MFC'
title: Paramètres de l'application, Assistant DLL MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.appset
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
ms.openlocfilehash: da9579ef9a834fa0c2362b1569c2efa808132faa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322796"
---
# <a name="application-settings-mfc-dll-wizard"></a>Paramètres de l'application, Assistant DLL MFC

Utilisez cette page de l’Assistant DLL MFC pour concevoir et ajouter des fonctionnalités de base à un nouveau projet DLL MFC.

## <a name="dll-type"></a>Type de DLL

Sélectionnez le type de DLL que vous souhaitez créer.

- **DLL MFC normale utilisant une DLL MFC partagée**

   Sélectionnez cette option pour lier la bibliothèque MFC à votre programme en tant que DLL partagée. À l’aide de cette option, vous ne pouvez pas partager des objets MFC entre votre DLL et l’application appelante. Votre programme effectue des appels à la bibliothèque MFC au moment de l’exécution. Cette option réduit les besoins en disque et en mémoire de votre programme s’il est composé de plusieurs fichiers d’exécution qui utilisent la bibliothèque MFC. Les programmes Win32 et MFC peuvent appeler des fonctions dans votre DLL. Vous devez redistribuer la DLL MFC avec ce type de projet.

- **DLL MFC normale avec MFC lié de manière statique**

   Sélectionnez cette option pour lier votre programme de manière statique à la bibliothèque MFC au moment de la génération. Les programmes Win32 et MFC peuvent appeler des fonctions dans votre DLL. Bien que cette option augmente la taille de votre programme, vous n’avez pas besoin de redistribuer la DLL MFC avec ce type de projet. Vous ne pouvez pas partager des objets MFC entre votre DLL et l’application appelante.

- **DLL d’extension MFC**

   Sélectionnez cette option si vous souhaitez que votre programme effectue des appels à la bibliothèque MFC au moment de l’exécution et si vous souhaitez partager des objets MFC entre votre DLL et l’application appelante. Cette option réduit les besoins en disque et en mémoire de votre programme, s’il est composé de plusieurs fichiers exécutables qui utilisent tous la bibliothèque MFC. Seuls les programmes MFC peuvent appeler des fonctions dans votre DLL. Vous devez redistribuer la DLL MFC avec ce type de projet.

## <a name="additional-features"></a>Fonctionnalités supplémentaires

Indiquez si votre DLL MFC doit prendre en charge l’automatisation et s’il doit prendre en charge Windows Sockets.

- **Automation**

   Sélectionnez **Automation** pour permettre à votre programme de manipuler des objets implémentés dans un autre programme. La sélection de l' **automatisation** expose également votre programme à d’autres clients Automation. Pour plus d’informations, consultez [Automation](../../mfc/automation.md) .

- **Sockets Windows**

   Sélectionnez cette option pour indiquer que votre programme prend en charge Windows Sockets. Windows Sockets vous permet d’écrire des programmes qui communiquent sur des réseaux TCP/IP.

   Quand votre DLL MFC avec prise en charge de Windows Sockets est créée, [CWinApp :: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) initialise la prise en charge des sockets et le fichier d’en-tête MFC stdafx. h comprend AfxSock. h.

## <a name="see-also"></a>Voir aussi

[Assistant DLL MFC](../../mfc/reference/mfc-dll-wizard.md)<br/>
[Création d’un projet DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md)
