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
ms.openlocfilehash: 007a4e53fd9b3eae612947cd76ee352776572d4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373525"
---
# <a name="cwinapp-the-application-class"></a>CWinApp : classe d'application

La principale classe d’applications de MFC résume l’initialisation, l’exécution et la résiliation d’une application pour le système d’exploitation Windows. Une application construite sur le cadre doit avoir un seul et unique objet d’une classe dérivée de [CWinApp](../mfc/reference/cwinapp-class.md). Cet objet est construit avant la création des fenêtres.

`CWinApp`est dérivé `CWinThread`de , qui représente le fil principal de l’exécution de votre application, qui pourrait avoir un ou plusieurs threads. Dans les versions récentes `InitInstance`de MFC, `OnIdle` le , **Run** `CWinThread`, `ExitInstance`et les fonctions des membres sont en fait en classe . Ces fonctions sont discutées `CWinApp` ici comme si elles étaient membres à la place, parce que la discussion concerne le rôle de l’objet comme objet d’application plutôt que comme fil principal.

> [!NOTE]
> Votre classe de demande constitue le fil d’exécution principal de votre application. En utilisant les fonctions Win32 API, vous pouvez également créer des fils secondaires d’exécution. Ces fils peuvent utiliser la bibliothèque MFC. Pour plus d’informations, voir [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Comme tout programme pour le système d’exploitation Windows, votre application-cadre a une `WinMain` fonction. Dans une application-cadre, cependant, `WinMain`vous n’écrivez pas . Il est fourni par la bibliothèque de classe et est appelé lorsque l’application démarre. `WinMain`effectue des services standard tels que l’enregistrement des classes de fenêtre. Il appelle ensuite les fonctions des membres de l’objet d’application pour initialiser et exécuter l’application. (Vous pouvez `WinMain` personnaliser en remplaçant `CWinApp` les fonctions du membre qui `WinMain` appellent.)

Pour initialiser l’application, `WinMain` appelle `InitApplication` les `InitInstance` fonctions de votre objet et de votre membre. Pour exécuter la boucle de `WinMain` message de l’application, appelle la fonction membre **Run.** Lors de `WinMain` la résiliation, appelle la fonction de membre de l’objet d’application. `ExitInstance`

> [!NOTE]
> Les noms **affichés** en gras dans cette documentation indiquent des éléments fournis par la Microsoft Foundation Class Library et Visual C. Les noms `monospaced` de type indiquent les éléments que vous créez ou remplacez.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)<br/>
[CWinApp et l’Assistant Application MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Fonctions de membre CWinApp primordiales](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Services CWinApp spéciaux](../mfc/special-cwinapp-services.md)
