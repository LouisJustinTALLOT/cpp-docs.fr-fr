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
ms.openlocfilehash: 42f21e2441f8ba3d2c6a13503c928880fe100f04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623154"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Glisser-déplacer des fichiers dans une fenêtre frame

La fenêtre frame gère une relation avec l’Explorateur de fichiers ou le gestionnaire de fichiers.

En ajoutant quelques appels d’initialisation dans votre remplacement de la `CWinApp` fonction membre `InitInstance` , comme décrit dans [CWinApp : la classe d’application](cwinapp-the-application-class.md), vous pouvez faire en sorte que votre fenêtre frame ouvre indirectement les fichiers déplacés à partir de l’Explorateur de fichiers ou du gestionnaire de fichiers et déposés dans la fenêtre frame. Consultez [glisser-déplacer du gestionnaire de fichiers](special-cwinapp-services.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
