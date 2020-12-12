---
description: 'En savoir plus sur : accès à l’état des fichiers'
title: Accès au statut de fichier
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: defff16ddfb8cb5321def898cad451f1e12f1f8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169526"
---
# <a name="accessing-file-status"></a>Accès au statut de fichier

`CFile` prend également en charge l’obtention de l’état du fichier, notamment si le fichier existe, les dates et heures de création et de modification, la taille logique et le chemin d’accès.

### <a name="to-get-file-status"></a>Pour récupérer l’état d’un fichier

1. Utilisez la classe [CFile](reference/cfile-class.md) pour obtenir et définir des informations sur un fichier. Une application utile consiste à utiliser la `CFile` fonction membre statique **GetStatus** pour déterminer si un fichier existe. **GetStatus** retourne 0 si le fichier spécifié n’existe pas.

Par conséquent, vous pouvez utiliser le résultat de **GetStatus** pour déterminer s’il faut utiliser l’indicateur **CFile :: modeCreate** lors de l’ouverture d’un fichier, comme indiqué dans l’exemple suivant :

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Pour obtenir des informations connexes, consultez [sérialisation](serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Fichiers](files-in-mfc.md)
