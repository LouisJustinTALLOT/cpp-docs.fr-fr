---
title: Accès au statut de fichier
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 3e16f8b11d17cd911646c3c9206d1d7deb577ef9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629786"
---
# <a name="accessing-file-status"></a>Accès au statut de fichier

`CFile` prend également en charge l’obtention d’état du fichier, y compris si le fichier existe, création et modification de dates des heures, taille logique et chemin d’accès.

### <a name="to-get-file-status"></a>Pour obtenir le statut du fichier

1. Utilisez le [CFile](../mfc/reference/cfile-class.md) classe pour obtenir et définir les informations relatives à un fichier. Une application utile consiste à utiliser le `CFile` fonction membre statique **GetStatus** pour déterminer si un fichier existe. **GetStatus** retourne 0 si le fichier spécifié n’existe pas.

Par conséquent, vous pouvez utiliser le résultat de **GetStatus** pour déterminer s’il faut utiliser le **CFile::modeCreate** indicateur lors de l’ouverture d’un fichier, comme le montre l’exemple suivant :

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Pour plus d’informations, consultez [sérialisation](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Fichiers](../mfc/files-in-mfc.md)

