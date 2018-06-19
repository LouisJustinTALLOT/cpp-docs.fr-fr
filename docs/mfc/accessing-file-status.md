---
title: Accès au statut de fichier | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d424502e991ea355a6e31bba8fedccb6d5ad2fcf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334293"
---
# <a name="accessing-file-status"></a>Accès au statut de fichier
`CFile` prend également en charge l’obtention d’état du fichier, y compris si le fichier existe, les dates de création et de modification et durées, taille logique et chemin d’accès.  
  
### <a name="to-get-file-status"></a>Pour obtenir le statut du fichier  
  
1.  Utilisez le [CFile](../mfc/reference/cfile-class.md) classe pour obtenir et définir les informations relatives à un fichier. Une application utile consiste à utiliser le `CFile` fonction membre statique **GetStatus** pour déterminer si un fichier existe. **GetStatus** retourne 0 si le fichier spécifié n’existe pas.  
  
 Par conséquent, vous pouvez utiliser le résultat de **GetStatus** pour déterminer s’il faut utiliser le **CFile::modeCreate** indicateur lors de l’ouverture d’un fichier, comme indiqué dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 Pour plus d’informations, consultez [sérialisation](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers](../mfc/files-in-mfc.md)

