---
title: Restrictions sur les gestionnaires d’exceptions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29a462f83bff3bab158e9bcf9fa7947efb56a79b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074472"
---
# <a name="restrictions-on-exception-handlers"></a>Restrictions sur les gestionnaires d'exceptions

La principale limitation à l’utilisation de gestionnaires d’exceptions dans le code est que vous ne pouvez pas utiliser un **goto** pour sauter dans une **__try** bloc d’instructions. À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. Vous pouvez sauter hors d’un **__try** instruction bloquer et imbriquer des gestionnaires d’exceptions que vous le souhaitez.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)