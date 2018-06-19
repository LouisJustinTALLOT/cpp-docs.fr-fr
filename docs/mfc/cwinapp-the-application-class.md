---
title: 'CWinApp : Classe d’Application | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0c3641441554d73e0c7657dd220be86f0c0cab0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343003"
---
# <a name="cwinapp-the-application-class"></a>CWinApp : classe d'application
La classe d’application principale dans MFC encapsule l’initialisation, en cours d’exécution et d’arrêt d’une application pour le système d’exploitation Windows. Une application basée sur l’infrastructure doit avoir l’une et qu’un seul objet d’une classe dérivée de [CWinApp](../mfc/reference/cwinapp-class.md). Cet objet est construit avant la création de windows.  
  
 `CWinApp` est dérivé de `CWinThread`, qui représente le thread principal de l’exécution de votre application, ce qui peut avoir un ou plusieurs threads. Dans les versions récentes de MFC, la `InitInstance`, **exécuter**, `ExitInstance`, et `OnIdle` fonctions membres sont en réalité dans la classe `CWinThread`. Ces fonctions sont décrites ici comme si elles étaient `CWinApp` membres à la place, car la description concerne le rôle de l’objet en tant qu’objet de l’application plutôt qu’en tant que le thread principal.  
  
> [!NOTE]
>  La classe d’application constitue le thread principal de votre application d’exécution. À l’aide des fonctions API Win32, vous pouvez également créer des threads secondaires de l’exécution. Ces threads peuvent utiliser la bibliothèque MFC. Pour plus d’informations, consultez [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Comme n’importe quel programme pour le système d’exploitation Windows, votre infrastructure d’application possède un `WinMain` (fonction). Dans une application framework, toutefois, vous n’écrivez pas `WinMain`. Il est fourni par la bibliothèque de classes et est appelée au démarrage de l’application. `WinMain` exécute des services standard telles que l’inscription des classes de fenêtre. Il puis appelle les fonctions membres de l’objet application pour initialiser et exécuter l’application. (Vous pouvez personnaliser `WinMain` en remplaçant le `CWinApp` les fonctions membres `WinMain` appels.)  
  
 Pour initialiser l’application, `WinMain` appelle l’objet de votre application `InitApplication` et `InitInstance` fonctions membres. Pour exécuter la boucle de message de l’application, `WinMain` appelle la **exécuter** fonction membre. Lors d’un arrêt, `WinMain` appelle l’objet application `ExitInstance` fonction membre.  
  
> [!NOTE]
>  Noms indiqués dans **gras** dans cette documentation désignent des éléments fournis par la bibliothèque Microsoft Foundation Class et Visual C++. Noms indiqués dans `monospaced` type indiquent des éléments que vous créez ou remplacez.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)   
 [CWinApp et l’Assistant Application MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [Fonctions membres CWinApp remplaçables](../mfc/overridable-cwinapp-member-functions.md)   
 [Services CWinApp spéciaux](../mfc/special-cwinapp-services.md)

