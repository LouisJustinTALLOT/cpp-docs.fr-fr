---
title: Longueur maximale de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: 650088249e4c6abd515c29b873a9f09dc1d2a60a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148307"
---
# <a name="maximum-string-length"></a>Longueur maximale de chaîne

**Section spécifique à Microsoft**

La compatibilité ANSI requiert un compilateur pour accepter jusqu'à 509 caractères dans un littéral de chaîne après concaténation. La longueur maximale d'un littéral de chaîne autorisé dans Microsoft C est d'environ 2 048 octets. Toutefois, si le littéral de chaîne comporte des parties placées entre guillemets, le préprocesseur concatène les parties dans une chaîne unique, et pour chaque ligne concaténée, il ajoute un octet supplémentaire au nombre total d'octets.

Par exemple, supposons qu'une chaîne se compose de 40 lignes avec 50 caractères par ligne (2 000 caractères), et une ligne avec 7 caractères, et que chaque ligne est placée entre guillemets doubles. Cela ajoute jusqu'à 2 007 octets plus un octet pour le caractère null de fin, pour un total de 2 008 octets. Sur la concaténation, un caractère supplémentaire est ajouté pour les 40 premières lignes. Cela donne un total de 2 048 octets. Notez, cependant, qui si les continuations de ligne (\\) sont utilisées au lieu des guillemets doubles, le préprocesseur n'ajoute pas de caractère supplémentaire pour chaque ligne.

Alors qu'une chaîne entre guillemets individuelle ne peut pas dépasser 2 048 octets, un littéral de chaîne d'environ 65 535 octets peut être construit en concaténant les chaînes.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
