---
description: 'En savoir plus sur les éléments suivants : glisser-déplacer des fichiers dans une fenêtre frame'
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
ms.openlocfilehash: dafbeca8b74ee07c80315c15ab93097977125d89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159945"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>Glisser-déplacer des fichiers dans une fenêtre frame

La fenêtre frame gère une relation avec l’Explorateur de fichiers ou le gestionnaire de fichiers.

En ajoutant quelques appels d’initialisation dans votre remplacement de la `CWinApp` fonction membre `InitInstance` , comme décrit dans [CWinApp : la classe d’application](cwinapp-the-application-class.md), vous pouvez faire en sorte que votre fenêtre frame ouvre indirectement les fichiers déplacés à partir de l’Explorateur de fichiers ou du gestionnaire de fichiers et déposés dans la fenêtre frame. Consultez [glisser-déplacer du gestionnaire de fichiers](special-cwinapp-services.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](using-frame-windows.md)
