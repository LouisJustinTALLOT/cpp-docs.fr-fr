---
title: char, type
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: c0524d30e19f8b54f577216a3160f721cbd2f0e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551058"
---
# <a name="type-char"></a>char, type

Le type `char` est utilisé pour stocker la valeur entière d'un membre du jeu de caractères qui peut être représenté. Cette valeur est le code ASCII correspondant au caractère spécifié.

**Section spécifique à Microsoft**

Les valeurs de caractère de type `unsigned char` ont une plage de 0 à 0xFF hexadécimal. La valeur **signed char** a une plage de 0x80 à 0x7F. En valeur décimale, ces plages s’étendent de 0 à 255 et de -128 à +127, respectivement. L’option /J du compilateur modifie le paramètre par défaut en remplaçant **signed** par `unsigned`.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Stockage de types de base](../c-language/storage-of-basic-types.md)