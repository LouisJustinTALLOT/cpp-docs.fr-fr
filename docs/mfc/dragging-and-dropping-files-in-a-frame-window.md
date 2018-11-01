---
title: Glisser-déposer des fichiers dans une fenêtre frame
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 34fb6ec6d57bcf8bc1cf51a3ac0c0db5203b3ffa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498829"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Glisser-déposer des fichiers dans une fenêtre frame

La fenêtre frame gère une relation avec l’Explorateur de fichiers ou le Gestionnaire de fichiers.

En ajoutant quelques initialisation appelle dans la substitution de la `CWinApp` fonction membre `InitInstance`, comme décrit dans [CWinApp : la classe d’Application](../mfc/cwinapp-the-application-class.md), vous pouvez ouvrir votre fenêtre frame indirectement les fichiers déplacés à partir du fichier Explorateur ou le Gestionnaire de fichier et supprimé dans la fenêtre frame. Consultez [fichier gestionnaire glisser -déplacer](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

