---
description: 'En savoir plus sur : exportation de fonctions à partir d’une DLL par ordinal plutôt que par nom'
title: Exportation de fonctions à partir d'une DLL par ordinal plutôt que par nom
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 84d200e2c37161d6bef3e64e72130204640088c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156500"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Exportation de fonctions à partir d'une DLL par ordinal plutôt que par nom

La façon la plus simple d’exporter des fonctions à partir de votre DLL consiste à les exporter par nom. C’est ce qui se produit lorsque vous utilisez **`__declspec(dllexport)`** , par exemple. Toutefois, vous pouvez exporter des fonctions par ordinal. Avec cette technique, vous devez utiliser un fichier. def au lieu de **`__declspec(dllexport)`** . Pour spécifier la valeur ordinale d’une fonction, ajoutez son ordinal au nom de la fonction dans le fichier. def. Pour plus d’informations sur la spécification des ordinaux, consultez [exportation à partir d’une dll à l’aide de fichiers. def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Si vous souhaitez optimiser la taille du fichier de votre DLL, utilisez l’attribut **NoName** sur chaque fonction exportée. Avec l’attribut **NoName** , les ordinaux sont stockés dans la table d’exportation de la dll au lieu des noms de fonctions. Cela peut s’avérer une économie considérable si vous exportez de nombreuses fonctions.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Utiliser un fichier. def pour pouvoir exporter par ordinal](exporting-from-a-dll-using-def-files.md)

- [Utiliser __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d'une DLL](exporting-from-a-dll.md)
