---
title: 'Exceptions : exceptions dans les constructeurs'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 4089f4d44f03c7de3432f137b5d28f74189e1cb9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624614"
---
# <a name="exceptions-exceptions-in-constructors"></a>Exceptions : exceptions dans les constructeurs

Lors de la levée d’une exception dans un constructeur, nettoyez les objets et les allocations de mémoire que vous avez effectués avant de lever l’exception, comme expliqué dans [exceptions : levée d’exceptions à partir de vos propres fonctions](exceptions-throwing-exceptions-from-your-own-functions.md).

Lors de la levée d’une exception dans un constructeur, la mémoire de l’objet lui-même a déjà été allouée au moment de l’appel du constructeur. Par conséquent, le compilateur désalloue automatiquement la mémoire occupée par l’objet après la levée de l’exception.

Pour plus d’informations, consultez [exceptions : libération d’objets dans les exceptions](exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
