---
title: Avertissement RW4004 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182342"
---
# <a name="resource-compiler-warning-rw4004"></a>Avertissement RW4004 du compilateur de ressources

Caractère ASCII non équivalent au code de touche virtuelle

Vous avez utilisé un littéral de chaîne pour le code de touche virtuelle dans un accélérateur de type VIRTKEY.

Cet avertissement ne vous empêche pas de continuer, mais sachez que les touches accélérateur générées risquent de ne pas correspondre à la chaîne spécifiée. (Les VIRTKEY utilisent des codes de touches différents des accélérateurs ASCII.)

Bien que les littéraux de chaîne soient syntaxiquement valides, vous ne pouvez vous assurer que l’accélérateur souhaité est obtenu à l’aide de l' **VK_\* #define** valeurs dans Windows. h.
