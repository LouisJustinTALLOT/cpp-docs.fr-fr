---
title: __based, grammaire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e9074de25d8cb914432123478f5f338ff4ba1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103762"
---
# <a name="based-grammar"></a>Syntaxe __based

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

L'adressage est utile lorsque vous avez besoin d'exercer un contrôle précis sur le segment dans lequel les objets sont alloués (données statiques et dynamiques).

La seule forme d’adressage acceptable dans les compilations 32 bits et 64 bits est « basé sur un pointeur » qui définit un type contient un déplacement 32 bits ou 64 bits à une base 32 bits ou 64 bits ou basés sur **void**.

## <a name="grammar"></a>Grammaire

*en fonction de modificateur de plage*: **__based (***expression de base***)** 

*expression de base*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*variable en fonction*: *identificateur*

*en fonction-abstract-declarator*: *abstract-declarator*

*type de base*: *type-name*

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Pointeurs based](../cpp/based-pointers-cpp.md)