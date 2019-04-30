---
title: 'Exceptions : Exceptions dans les constructeurs'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405870"
---
# <a name="exceptions-exceptions-in-constructors"></a>Exceptions : Exceptions dans les constructeurs

Lorsque vous levez une exception dans un constructeur, nettoyer toutes les allocations de mémoire et les objets que vous avez apportées, comme expliqué dans [Exceptions : Levée d’Exceptions à partir de vos propres fonctions](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Lorsque vous levez une exception dans un constructeur, la mémoire pour l’objet lui-même a déjà été allouée au moment où que le constructeur est appelé. Par conséquent, le compilateur automatiquement désalloue la mémoire occupée par l’objet une fois que l’exception est levée.

Pour plus d’informations, consultez [Exceptions : Libération d’objets dans les Exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
