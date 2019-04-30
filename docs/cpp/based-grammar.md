---
title: Syntaxe __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 8dec9b0bcc7db25e2ec4c39b9d907922691bfc05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393946"
---
# <a name="based-grammar"></a>Syntaxe __based

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

L'adressage est utile lorsque vous avez besoin d'exercer un contrôle précis sur le segment dans lequel les objets sont alloués (données statiques et dynamiques).

La seule forme d’adressage acceptable dans les compilations 32 bits et 64 bits est « basé sur un pointeur » qui définit un type contient un déplacement 32 bits ou 64 bits à une base 32 bits ou 64 bits ou basés sur **void**.

## <a name="grammar"></a>Grammaire

*based-range-modifier*: **__based(**  *base-expression*  **)**

*base-expression*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*variable en fonction*: *identificateur*

*based-abstract-declarator*: *abstract-declarator*

*type de base*: *type-name*

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Pointeurs based](../cpp/based-pointers-cpp.md)