---
title: 'Avertissement RW4004 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485642"
---
# <a name="resource-compiler-warning-rw4004"></a>Avertissement RW4004 du compilateur de ressources 

Caractère ASCII non équivalent au code de touche virtuelle

Vous avez utilisé un littéral de chaîne pour le code de touche virtuelle dans un accélérateur de type VIRTKEY.

Cet avertissement ne vous empêche pas de continuer, mais sachez que les touches accélérateur générées risquent de ne pas correspondre à la chaîne spécifiée. (Les VIRTKEY utilisent des codes de touches différents des accélérateurs ASCII.)

Tandis que les littéraux de chaîne sont valides, vous pouvez uniquement vous assurer que vous obtenez l’accélérateur souhaité à l’aide de la **VK_\* #define** valeurs dans WINDOWS.h.