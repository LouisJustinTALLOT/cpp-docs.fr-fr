---
title: Syntaxe __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 539ccef65477bafe2c46ce328bdaf65f52aff1b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229153"
---
# <a name="__based-grammar"></a>Syntaxe __based

**Spécifique à Microsoft**

L'adressage est utile lorsque vous avez besoin d'exercer un contrôle précis sur le segment dans lequel les objets sont alloués (données statiques et dynamiques).

La seule forme d’adressage basé acceptable dans les compilations 32 bits et 64 bits est « basée sur un pointeur » qui définit un type qui contient un déplacement de 32 bits ou 64 bits vers une base de 32 bits ou 64 bits ou basé sur **`void`** .

## <a name="grammar"></a>Grammaire

*modificateur de plage based*: **__based (**  *base-expression*  **)**

*base-expression*: based *-variablebased-abstract-declaratorsegment-namesegment-Cast*

*variable basée sur*: *identificateur*

*based-abstract-declarator*: *abstract-declarator*

*type de base*: *type-name*

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Pointeurs based](../cpp/based-pointers-cpp.md)
