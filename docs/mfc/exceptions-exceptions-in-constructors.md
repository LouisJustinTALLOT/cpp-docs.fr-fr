---
title: 'Exceptions : exceptions dans les constructeurs'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 23d1f6a9a3c76cc9c0c1d4aebd5c0b0ea45c3154
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472266"
---
# <a name="exceptions-exceptions-in-constructors"></a>Exceptions : exceptions dans les constructeurs

Lorsque vous levez une exception dans un constructeur, nettoyer toutes les allocations de mémoire et les objets que vous avez apportées, comme expliqué dans [Exceptions : levée d’Exceptions à partir de vos propres fonctions](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Lorsque vous levez une exception dans un constructeur, la mémoire pour l’objet lui-même a déjà été allouée au moment où que le constructeur est appelé. Par conséquent, le compilateur automatiquement désalloue la mémoire occupée par l’objet une fois que l’exception est levée.

Pour plus d’informations, consultez [Exceptions : libération d’objets dans les Exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

