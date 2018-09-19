---
title: Compilateur avertissement (niveaux 1 et 4) C4115 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c22e3c33f9ef2409c02f0e651473d566b4d2a74
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022524"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Avertissement du compilateur (niveaux 1 et 4) C4115

'type' : définition d’un type nommé dans les parenthèses

Le symbole donné est utilisé pour définir une structure, une union ou un type énuméré dans une expression entre parenthèses. La portée de la définition peut être inattendue.

Dans un appel de fonction C, la définition a une portée globale. Dans un appel C++, la définition a la même portée que la fonction appelée.

Cet avertissement peut également être dû à des déclarateurs entre parenthèses (tels que des prototypes) qui ne sont pas des expressions entre parenthèses.

Il s’agit d’un avertissement de niveau 1 avec les programmes C++ et les programmes C compilés sous compatibilité ANSI (/Za). Sinon, il s’agit d’un avertissement de niveau 3.