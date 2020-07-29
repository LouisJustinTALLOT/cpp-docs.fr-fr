---
title: Restrictions sur les gestionnaires d’exceptions
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 1f80cb1574cbfef0783c7e55dcd198dfb822f566
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225902"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions sur les gestionnaires d’exceptions

La principale limitation à l’utilisation de gestionnaires d’exceptions dans le code est que vous ne pouvez pas utiliser une **`goto`** instruction pour accéder à un bloc d’instructions **__try** . À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez accéder à un bloc d’instructions **__try** et imbriquer des gestionnaires d’exceptions comme vous le souhaitez.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
