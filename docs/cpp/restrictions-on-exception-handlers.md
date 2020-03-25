---
title: Restrictions applicables aux gestionnaires d'exceptions
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 54bf4a44d06eacd22dc4b9819d160d3c6a66c684
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179079"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions applicables aux gestionnaires d'exceptions

La principale limitation à l’utilisation de gestionnaires d’exceptions dans le code est que vous ne pouvez pas utiliser une instruction **goto** pour accéder à un bloc d’instructions **__try** . À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez accéder à un bloc d’instructions **__try** et imbriquer des gestionnaires d’exceptions comme vous le souhaitez.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
