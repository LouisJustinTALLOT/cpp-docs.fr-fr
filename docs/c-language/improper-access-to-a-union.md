---
title: Accès inapproprié à une union
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 5a804ed80c8f1ac2f5dd9a24f12c67e96e199b6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227827"
---
# <a name="improper-access-to-a-union"></a>Accès inapproprié à une union

**ANSI 3.3.2.3** Un accès à un membre d'un objet d'union a lieu en utilisant un membre d'un type différent

Si une union de deux types est déclarée et qu'une valeur est enregistrée, mais que l'union est accessible par l'autre type, les résultats ne sont pas fiables.

Par exemple, une Union de **`float`** et **`int`** est déclarée. Une **`float`** valeur est stockée, mais le programme accède ultérieurement à la valeur en tant que **`int`** . Dans ce cas, la valeur dépend du stockage interne des **`float`** valeurs. La valeur entière n'est pas fiable.

## <a name="see-also"></a>Voir aussi

[Structures, unions, énumérations et champs de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)
