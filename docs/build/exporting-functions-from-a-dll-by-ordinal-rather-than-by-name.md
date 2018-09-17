---
title: Exportation de fonctions à partir d’une DLL par Ordinal plutôt que par nom | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- NONAME
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d894df971dd0c50556a420eafa2909474ee6912
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714257"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportation de fonctions à partir d'une DLL par ordinal plutôt que par nom

Pour exporter des fonctions à partir de votre DLL, le plus simple consiste à les exporter par nom. Il s’agit que se passe-t-il lorsque vous utilisez **__declspec (dllexport)**, par exemple. Mais vous pouvez exporter à la place des fonctions par ordinal. Avec cette technique, vous devez utiliser un fichier .def à la place de **__declspec (dllexport)**. Pour spécifier la valeur ordinale d’une fonction, ajoutez son ordinal au nom de fonction dans le fichier .def. Pour plus d’informations sur la spécification des ordinaux, consultez [exportation à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Si vous souhaitez optimiser la taille de fichier de votre DLL, utilisez le **NONAME** attribut sur chaque fonction exportée. Avec le **NONAME** attribut, les ordinaux sont stockés dans la DLL d’exporte la table plutôt que les noms des fonctions. Cela peut être une économie considérable si vous exportez de nombreuses fonctions.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Utiliser un fichier .def afin de pouvoir effectuer une exportation par ordinal](../build/exporting-from-a-dll-using-def-files.md)

- [Utilisez __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)