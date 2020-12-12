---
description: 'En savoir plus sur : exceptions : exceptions dans les constructeurs'
title: 'Exceptions : exceptions dans les constructeurs'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 69393cc6a5cf709d359ccbdb572406e91c6788ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290594"
---
# <a name="exceptions-exceptions-in-constructors"></a>Exceptions : exceptions dans les constructeurs

Lors de la levée d’une exception dans un constructeur, nettoyez les objets et les allocations de mémoire que vous avez effectués avant de lever l’exception, comme expliqué dans [exceptions : levée d’exceptions à partir de vos propres fonctions](exceptions-throwing-exceptions-from-your-own-functions.md).

Lors de la levée d’une exception dans un constructeur, la mémoire de l’objet lui-même a déjà été allouée au moment de l’appel du constructeur. Par conséquent, le compilateur désalloue automatiquement la mémoire occupée par l’objet après la levée de l’exception.

Pour plus d’informations, consultez [exceptions : libération d’objets dans les exceptions](exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
