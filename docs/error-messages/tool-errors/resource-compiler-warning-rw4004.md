---
description: 'En savoir plus sur : avertissement du compilateur de ressources RW4004'
title: 'Avertissement RW4004 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: 5609d49e242ba7d74025622c53c279ae1b0da854
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236995"
---
# <a name="resource-compiler-warning-rw4004"></a>Avertissement RW4004 du compilateur de ressources 

Caractère ASCII non équivalent au code de touche virtuelle

Vous avez utilisé un littéral de chaîne pour le code de touche virtuelle dans un accélérateur de type VIRTKEY.

Cet avertissement ne vous empêche pas de continuer, mais sachez que les touches accélérateur générées risquent de ne pas correspondre à la chaîne spécifiée. (Les VIRTKEY utilisent des codes de touches différents des accélérateurs ASCII.)

Bien que les littéraux de chaîne soient syntaxiquement valides, vous ne pouvez vous assurer que l’accélérateur souhaité est obtenu à l’aide de la **VK_ \* #define** les valeurs dans Windows. h.
