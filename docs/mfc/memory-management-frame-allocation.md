---
title: 'Gestion de la mémoire : Allocation le Frame | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1138a675d64561a2e8399accd93c4ebb5eff382d
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083858"
---
# <a name="memory-management-frame-allocation"></a>Gestion de la mémoire : allocation de frame

L'allocation dans le frame tient son nom du "frame de pile" installé lorsqu'une fonction est appelée. Le frame de pile est une zone de la mémoire contenant temporairement les arguments à la fonction, ainsi que toutes les variables qui sont définies comme étant locales à la fonction. Les variables de frame sont souvent appelées variables "automatiques" puisque le compilateur leur alloue de l'espace.

Il existe deux principales caractéristiques d'allocations de frame. D'abord, lorsque vous définissez une variable locale, suffisamment d'espace est alloué sur le frame de pile pour contenir la valeur entière, même s'il s'agit d'une grande table ou structure de données. Ensuite, les variables du frame sont automatiquement supprimées lorsqu'elles sont hors de portée :

[!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

Pour les variables de fonction locale, cette transition de portée se produit lorsque la fonction existe, mais l'étendue d'une variable de frame peut être inférieure à la fonction si les accolades imbriquées sont utilisées. La suppression automatique des variables de frame est très importante. Dans le cas des types primitifs simples (telles que **int** ou **octets**), tableaux ou structures de données, la suppression automatique libère simplement la mémoire utilisée par la variable. Dans la mesure où la variable est sortie de l'étendue, elle est de toute façon inaccessible. Dans le cas des objets C++, toutefois, le processus de suppression automatique est un peu plus compliqué.

Lorsqu'un objet est défini comme variable de frame, le constructeur est appelé automatiquement au point où la définition est produite. Lorsque l'objet sort de l'étendue, le destructeur est automatiquement appelé avant que la mémoire de l'objet soit diffusée. Ces constructions et destructions automatiques peuvent être très pratiques, mais vous devez connaître les appels automatiques, notamment le destructeur.

Le principal avantage d'allouer des objets dans le frame est qu'ils sont automatiquement supprimés. Lorsque vous allouez vos objets dans le frame, vous n'avez pas à vous soucier des objets oubliés provoquant des fuites de mémoire. (Pour plus d’informations sur les fuites de mémoire, consultez l’article [détection des fuites de mémoire dans les MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476).) L'inconvénient lié à l'allocation de frame est que les variables du frame ne peuvent pas être utilisées hors de portée. Un autre facteur en choisissant l'allocation de frame par rapport à l'allocation des segments est que pour les structures et les objets, il est souvent préférable d'utiliser le segment au lieu de la pile de stockage, l'espace de pile est généralement limité.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire](../mfc/memory-management.md)

