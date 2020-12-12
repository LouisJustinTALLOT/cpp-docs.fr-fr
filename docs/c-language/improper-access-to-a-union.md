---
description: 'En savoir plus sur : accès inapproprié à une Union'
title: Accès inapproprié à une union
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: edff4d74e4e31b505e8c6b71555358fcd4b7e070
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182110"
---
# <a name="improper-access-to-a-union"></a>Accès inapproprié à une union

**ANSI 3.3.2.3** Un accès à un membre d'un objet d'union a lieu en utilisant un membre d'un type différent

Si une union de deux types est déclarée et qu'une valeur est enregistrée, mais que l'union est accessible par l'autre type, les résultats ne sont pas fiables.

Par exemple, une Union de **`float`** et **`int`** est déclarée. Une **`float`** valeur est stockée, mais le programme accède ultérieurement à la valeur en tant que **`int`** . Dans ce cas, la valeur dépend du stockage interne des **`float`** valeurs. La valeur entière n'est pas fiable.

## <a name="see-also"></a>Voir aussi

[Structures, unions, énumérations et champs de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)
