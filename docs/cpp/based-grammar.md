---
description: 'En savoir plus sur : grammaire __based'
title: Syntaxe __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 9c449c45700c57d0c6f6018ca47e40d42c4b2ad0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304517"
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
