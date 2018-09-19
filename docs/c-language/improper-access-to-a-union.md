---
title: Accès inapproprié à une union | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac723ed80eaebc4b3f245ef56b761600007cd2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028374"
---
# <a name="improper-access-to-a-union"></a>Accès inapproprié à une union

**ANSI 3.3.2.3** Un accès à un membre d'un objet d'union a lieu en utilisant un membre d'un type différent

Si une union de deux types est déclarée et qu'une valeur est enregistrée, mais que l'union est accessible par l'autre type, les résultats ne sont pas fiables.

Par exemple, une union de type **float** et `int` est déclarée. Une valeur de type **float** est stockée, mais le programme y accède ultérieurement en tant que `int`. Dans ce cas, la valeur dépend du stockage interne des valeurs **float**. La valeur entière n'est pas fiable.

## <a name="see-also"></a>Voir aussi

[Structures, unions, énumérations et champs de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)