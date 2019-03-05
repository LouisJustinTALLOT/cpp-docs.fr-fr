---
title: Glisser-déplacer des fichiers dans une fenêtre frame
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
ms.openlocfilehash: 0129b939e0fe2afd5dd29623bb44418bfd16c20d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260407"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Glisser-déplacer des fichiers dans une fenêtre frame

La fenêtre frame gère une relation avec l’Explorateur de fichiers ou le Gestionnaire de fichiers.

En ajoutant quelques initialisation appelle dans la substitution de la `CWinApp` fonction membre `InitInstance`, comme décrit dans [CWinApp : La classe Application](../mfc/cwinapp-the-application-class.md), vous pouvez avoir votre fenêtre frame indirectement ouvrir des fichiers à partir de l’Explorateur de fichiers ou le Gestionnaire de fichiers glisser -déplacer dans la fenêtre frame. Consultez [fichier gestionnaire glisser -déplacer](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)
