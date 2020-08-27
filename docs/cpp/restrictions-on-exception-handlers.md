---
title: Restrictions sur les gestionnaires d’exceptions
description: Décrit les restrictions relatives au saut des blocs de gestion structurée des exceptions.
ms.date: 08/24/2020
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: c4182f065789533bf7599621d8d2829b2d52d6ed
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898444"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions sur les gestionnaires d’exceptions

La principale limitation à l’utilisation de gestionnaires d’exceptions dans le code est que vous ne pouvez pas utiliser une **`goto`** instruction pour accéder à un **`__try`** bloc d’instructions. À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez sortir d’un **`__try`** bloc d’instructions et imbriquer des gestionnaires d’exceptions comme vous le souhaitez.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
