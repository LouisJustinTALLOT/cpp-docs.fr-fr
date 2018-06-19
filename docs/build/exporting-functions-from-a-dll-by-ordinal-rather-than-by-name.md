---
title: Exportation de fonctions à partir d’une DLL par Ordinal plutôt que par nom | Documents Microsoft
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
ms.openlocfilehash: b05f3e429406b3c24c7a21ce9ee8e10fe19c14b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367691"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportation de fonctions à partir d'une DLL par ordinal plutôt que par nom
Pour exporter des fonctions à partir de votre DLL, le plus simple consiste à les exporter par nom. Il s’agit que se passe-t-il lorsque vous utilisez **__declspec (dllexport)**, par exemple. Mais vous pouvez exporter à la place des fonctions par ordinal. Avec cette technique, vous devez utiliser un fichier .def à la place de **__declspec (dllexport)**. Pour spécifier une valeur de la fonction ordinale, ajoutez son ordinal au nom de fonction dans le fichier .def. Pour plus d’informations sur la spécification des ordinaux, consultez [exportation à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md).  
  
> [!TIP]
>  Si vous souhaitez optimiser la taille du fichier de votre DLL, utilisez la **NONAME** attribut sur chaque fonction exportée. Avec la **NONAME** attribut, les ordinaux sont stockés dans la DLL d’exporte la table plutôt que les noms de fonctions. Cela peut être une économie considérable si vous exportez de nombreuses fonctions.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Utiliser un fichier .def afin de pouvoir effectuer une exportation par ordinal](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Utilisez __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)