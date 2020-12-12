---
description: 'En savoir plus sur : CWinApp : la classe d’application'
title: "CWinApp : classe d'application"
ms.date: 11/04/2016
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
ms.openlocfilehash: 63979846ec5b4d5bb5452e98a3ac19474b4fcd0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301631"
---
# <a name="cwinapp-the-application-class"></a>CWinApp : classe d'application

La classe d’application principale dans MFC encapsule l’initialisation, l’exécution et l’arrêt d’une application pour le système d’exploitation Windows. Une application basée sur l’infrastructure doit avoir un seul objet d’une classe dérivée de [CWinApp](reference/cwinapp-class.md). Cet objet est construit avant la création de fenêtres.

`CWinApp` est dérivée de `CWinThread` , qui représente le thread d’exécution principal de votre application, qui peut avoir un ou plusieurs threads. Dans les versions récentes de MFC, les `InitInstance` fonctions membres **,,** `ExitInstance` et `OnIdle` sont en fait dans la classe `CWinThread` . Ces fonctions sont décrites ici comme si elles étaient `CWinApp` membres à la place, car la discussion concerne le rôle de l’objet en tant qu’objet d’application plutôt qu’en tant que thread principal.

> [!NOTE]
> Votre classe d’application constitue le thread principal d’exécution de votre application. À l’aide des fonctions API Win32, vous pouvez également créer des threads secondaires d’exécution. Ces threads peuvent utiliser la bibliothèque MFC. Pour plus d’informations, consultez [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Comme tout programme pour le système d’exploitation Windows, votre application de Framework a une `WinMain` fonction. Dans une application Framework, toutefois, vous n’écrivez pas `WinMain` . Elle est fournie par la bibliothèque de classes et est appelée au démarrage de l’application. `WinMain` exécute des services standard tels que l’inscription des classes de fenêtres. Il appelle ensuite les fonctions membres de l’objet application pour initialiser et exécuter l’application. (Vous pouvez personnaliser `WinMain` en substituant les `CWinApp` fonctions membres qui `WinMain` appellent.)

Pour initialiser l’application, `WinMain` appelle les `InitApplication` fonctions membres et de l’objet de votre application `InitInstance` . Pour exécuter la boucle de messages de l’application, `WinMain` appelle la fonction membre **Run** . À l’arrêt, `WinMain` appelle la fonction membre de l’objet d’application `ExitInstance` .

> [!NOTE]
> Les noms affichés en **gras** dans cette documentation indiquent les éléments fournis par le bibliothèque MFC (Microsoft Foundation Class) et Visual C++. Les noms indiqués dans `monospaced` type indiquent les éléments que vous créez ou substituez.

## <a name="see-also"></a>Voir aussi

[Rubriques générales sur MFC](general-mfc-topics.md)<br/>
[CWinApp et l’Assistant Application MFC](cwinapp-and-the-mfc-application-wizard.md)<br/>
[Fonctions membres CWinApp remplaçables](overridable-cwinapp-member-functions.md)<br/>
[Services CWinApp spéciaux](special-cwinapp-services.md)
