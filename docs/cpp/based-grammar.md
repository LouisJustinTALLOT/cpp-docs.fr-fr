---
title: Syntaxe __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: a8c923b5a111144c539b5bea1b2f47eb58dd1fbd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857643"
---
# <a name="__based-grammar"></a>Syntaxe __based

**Section spécifique de Microsoft**

L'adressage est utile lorsque vous avez besoin d'exercer un contrôle précis sur le segment dans lequel les objets sont alloués (données statiques et dynamiques).

La seule forme d’adressage de base acceptable dans les compilations 32 bits et 64 bits est « basée sur un pointeur » qui définit un type qui contient un déplacement de 32 bits ou de 64 bits vers une base de 32 bits ou 64 bits ou en fonction de **void**.

## <a name="grammar"></a>Grammaire

*modificateur de plage based*: **__based (**  *base-expression*  **)**

*base-expression*: based *-variablebased-abstract-declaratorsegment-namesegment-Cast*

*variable basée sur*: *identificateur*

*based-abstract-declarator*: *abstract-declarator*

*type de base*: *type-name*

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Pointeurs based](../cpp/based-pointers-cpp.md)