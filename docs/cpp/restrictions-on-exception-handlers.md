---
title: Restrictions sur les gestionnaires d'exceptions
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 7d5bf20da61f4b9f5012b7f2aab932dfc904c302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573990"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions sur les gestionnaires d'exceptions

La principale limitation à l’utilisation de gestionnaires d’exceptions dans le code est que vous ne pouvez pas utiliser un **goto** pour sauter dans une **__try** bloc d’instructions. À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez sauter hors d’un **__try** instruction bloquer et imbriquer des gestionnaires d’exceptions que vous le souhaitez.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)