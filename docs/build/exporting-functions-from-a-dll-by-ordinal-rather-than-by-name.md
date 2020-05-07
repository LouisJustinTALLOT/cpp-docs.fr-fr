---
title: Exportation de fonctions à partir d'une DLL par ordinal plutôt que par nom
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328574"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportation de fonctions à partir d'une DLL par ordinal plutôt que par nom

La façon la plus simple d’exporter des fonctions à partir de votre DLL consiste à les exporter par nom. C’est ce qui se produit lorsque vous utilisez **__declspec (dllexport)**, par exemple. Toutefois, vous pouvez exporter des fonctions par ordinal. Avec cette technique, vous devez utiliser un fichier. def au lieu de **__declspec (dllexport)**. Pour spécifier la valeur ordinale d’une fonction, ajoutez son ordinal au nom de la fonction dans le fichier. def. Pour plus d’informations sur la spécification des ordinaux, consultez [exportation à partir d’une dll à l’aide de fichiers. def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Si vous souhaitez optimiser la taille du fichier de votre DLL, utilisez l’attribut **NoName** sur chaque fonction exportée. Avec l’attribut **NoName** , les ordinaux sont stockés dans la table d’exportation de la dll au lieu des noms de fonctions. Cela peut s’avérer une économie considérable si vous exportez de nombreuses fonctions.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Utiliser un fichier. def pour pouvoir exporter par ordinal](exporting-from-a-dll-using-def-files.md)

- [Utiliser __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
