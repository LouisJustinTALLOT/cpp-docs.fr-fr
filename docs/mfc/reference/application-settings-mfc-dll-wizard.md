---
title: Paramètres d’application, Assistant DLL MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a243b790881452a983c43fb92d8ebea18c26bcc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348678"
---
# <a name="application-settings-mfc-dll-wizard"></a>Paramètres de l'application, Assistant DLL MFC
Utilisez cette page de l’Assistant DLL MFC pour concevoir et ajouter des fonctionnalités de base à un nouveau projet de DLL MFC.  
  
## <a name="dll-type"></a>Type de DLL  
 Sélectionnez le type de DLL que vous souhaitez créer.  
  
 **DLL MFC normale utilisant une DLL MFC partagée**  
 Sélectionnez cette option pour lier la bibliothèque MFC à votre programme en tant que DLL partagé. À l’aide de cette option, vous ne pouvez pas partager les objets MFC entre votre DLL et l’application appelante. Votre programme effectue des appels à la bibliothèque MFC au moment de l’exécution. Cette option réduit les besoins en mémoire et espace disque de votre programme s’il est composé de plusieurs fichiers de l’exécution qui utilisent la bibliothèque MFC. Les programmes Win32 et MFC peuvent appeler des fonctions dans votre DLL. Vous devez redistribuer les DLL MFC avec ce type de projet.  
  
 **Liées de façon régulière DLL MFC avec MFC**  
 Sélectionnez cette option pour lier votre programme statiquement à la bibliothèque MFC au moment de la génération. Les programmes Win32 et MFC peuvent appeler des fonctions dans votre DLL. Alors que cette option augmente la taille de votre programme, vous n’avez pas besoin de redistribuer les DLL MFC avec ce type de projet. Vous ne pouvez pas partager les objets MFC entre votre DLL et l’application appelante.  
  
 **DLL d’extension MFC**  
 Sélectionnez cette option si vous souhaitez que votre programme afin d’effectuer des appels à la bibliothèque MFC au moment de l’exécution, et si vous souhaitez partager les objets MFC entre votre DLL et l’application appelante. Cette option réduit les besoins en mémoire et espace disque de votre programme, s’il est composé de plusieurs fichiers exécutables qui utilisent tous la bibliothèque MFC. Seuls les programmes MFC peuvent appeler des fonctions dans votre DLL. Vous devez redistribuer les DLL MFC avec ce type de projet.  
  
## <a name="additional-features"></a>Fonctionnalités supplémentaires  
 Sélectionnez si votre DLL MFC prend en charge l’automation et si elle doit prendre en charge Windows sockets.  
  
 **Automation**  
 Sélectionnez **Automation** pour permettre à votre programme manipuler des objets implémentés dans un autre programme. En sélectionnant **Automation** expose également votre programme à d’autres clients Automation. Consultez [Automation](../../mfc/automation.md) pour plus d’informations.  
  
 **Sockets Windows**  
 Sélectionnez cette option pour indiquer que votre programme prend en charge Windows sockets. Les sockets Windows vous permettent d’écrire des programmes qui communiquent sur les réseaux TCP/IP.  
  
 Lorsque votre DLL MFC avec Windows sockets prise en charge est créée, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) initialise prend en charge pour les sockets et le fichier d’en-tête MFC StdAfx.h comprend AfxSock.h.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant DLL MFC](../../mfc/reference/mfc-dll-wizard.md)   
 [Création d’un projet DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md)

