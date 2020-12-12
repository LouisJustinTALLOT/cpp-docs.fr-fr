---
description: 'En savoir plus sur : longueur de chaîne maximale'
title: Longueur maximale de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: 1da7618a044be2427bd0b0f7f4931287ee4b8014
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243430"
---
# <a name="maximum-string-length"></a>Longueur maximale de chaîne

**Spécifique à Microsoft**

La compatibilité ANSI requiert un compilateur pour accepter jusqu'à 509 caractères dans un littéral de chaîne après concaténation. La longueur maximale d'un littéral de chaîne autorisé dans Microsoft C est d'environ 2 048 octets. Toutefois, si le littéral de chaîne comporte des parties placées entre guillemets, le préprocesseur concatène les parties dans une chaîne unique, et pour chaque ligne concaténée, il ajoute un octet supplémentaire au nombre total d'octets.

Par exemple, supposons qu'une chaîne se compose de 40 lignes avec 50 caractères par ligne (2 000 caractères), et une ligne avec 7 caractères, et que chaque ligne est placée entre guillemets doubles. Cela ajoute jusqu'à 2 007 octets plus un octet pour le caractère null de fin, pour un total de 2 008 octets. Sur la concaténation, un caractère supplémentaire est ajouté pour les 40 premières lignes. Cela donne un total de 2 048 octets. Notez, cependant, qui si les continuations de ligne (\\) sont utilisées au lieu des guillemets doubles, le préprocesseur n'ajoute pas de caractère supplémentaire pour chaque ligne.

Alors qu'une chaîne entre guillemets individuelle ne peut pas dépasser 2 048 octets, un littéral de chaîne d'environ 65 535 octets peut être construit en concaténant les chaînes.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
