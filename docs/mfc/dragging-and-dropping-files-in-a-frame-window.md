---
title: Glisser -déplacer des fichiers dans une fenêtre Frame | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fc68923de531240a2d59336c79e54f6562b369c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380527"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Glisser-déposer des fichiers dans une fenêtre frame

La fenêtre frame gère une relation avec l’Explorateur de fichiers ou le Gestionnaire de fichiers.

En ajoutant quelques initialisation appelle dans la substitution de la `CWinApp` fonction membre `InitInstance`, comme décrit dans [CWinApp : la classe d’Application](../mfc/cwinapp-the-application-class.md), vous pouvez ouvrir votre fenêtre frame indirectement les fichiers déplacés à partir du fichier Explorateur ou le Gestionnaire de fichier et supprimé dans la fenêtre frame. Consultez [fichier gestionnaire glisser -déplacer](../mfc/special-cwinapp-services.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

