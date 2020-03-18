---
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
ms.openlocfilehash: 8518e21a9fa6bcf5ac640cff25b17c5028046b06
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447020"
---
# <a name="cwinapp-the-application-class"></a>CWinApp : classe d'application

La classe d’application principale dans MFC encapsule l’initialisation, l’exécution et l’arrêt d’une application pour le système d’exploitation Windows. Une application basée sur l’infrastructure doit avoir un seul objet d’une classe dérivée de [CWinApp](../mfc/reference/cwinapp-class.md). Cet objet est construit avant la création de fenêtres.

`CWinApp` est dérivée de `CWinThread`, qui représente le principal thread d’exécution de votre application, qui peut avoir un ou plusieurs threads. Dans les versions récentes de MFC, les fonctions membres `InitInstance`, **Run**, `ExitInstance`et `OnIdle` sont en fait dans la classe `CWinThread`. Ces fonctions sont présentées ici comme si elles étaient `CWinApp` membres, car la discussion concerne le rôle de l’objet en tant qu’objet d’application plutôt qu’en tant que thread principal.

> [!NOTE]
>  Votre classe d’application constitue le thread principal d’exécution de votre application. À l’aide des fonctions API Win32, vous pouvez également créer des threads secondaires d’exécution. Ces threads peuvent utiliser la bibliothèque MFC. Pour plus d’informations, consultez [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Comme n’importe quel programme pour le système d’exploitation Windows, votre application de Framework a une fonction de `WinMain`. Toutefois, dans une application Framework, vous n’écrivez pas `WinMain`. Elle est fournie par la bibliothèque de classes et est appelée au démarrage de l’application. `WinMain` effectue des services standard tels que l’inscription des classes de fenêtres. Il appelle ensuite les fonctions membres de l’objet application pour initialiser et exécuter l’application. (Vous pouvez personnaliser `WinMain` en substituant les fonctions membres `CWinApp` que `WinMain` appelle.)

Pour initialiser l’application, `WinMain` appelle les fonctions membres `InitApplication` et `InitInstance` de votre objet application. Pour exécuter la boucle de messages de l’application, `WinMain` appelle la fonction membre **Run** . À l’arrêt, `WinMain` appelle la fonction membre `ExitInstance` de l’objet d’application.

> [!NOTE]
>  Les noms affichés en **gras** dans cette documentation indiquent les éléments fournis par le bibliothèque MFC (Microsoft Foundation Class) C++et l’élément visuel. Les noms indiqués dans `monospaced` type indiquent les éléments que vous créez ou substituez.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CWinApp et l’Assistant Application MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Fonctions membres CWinApp remplaçables](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Services CWinApp spéciaux](../mfc/special-cwinapp-services.md)
