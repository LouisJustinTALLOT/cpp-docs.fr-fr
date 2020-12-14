---
description: 'En savoir plus sur : avertissement du compilateur (niveaux 1 et 4) C4115'
title: Avertissement du compilateur (niveaux 1 et 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: f41dcdf16d541151384d50d004a55d6e1993ece0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234486"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Avertissement du compilateur (niveaux 1 et 4) C4115

'type' : définition d’un type nommé dans les parenthèses

Le symbole donné est utilisé pour définir une structure, une union ou un type énuméré dans une expression entre parenthèses. La portée de la définition peut être inattendue.

Dans un appel de fonction C, la définition a une portée globale. Dans un appel C++, la définition a la même portée que la fonction appelée.

Cet avertissement peut également être dû à des déclarateurs entre parenthèses (tels que des prototypes) qui ne sont pas des expressions entre parenthèses.

Il s’agit d’un avertissement de niveau 1 avec les programmes C++ et les programmes C compilés sous compatibilité ANSI (/Za). Sinon, il s’agit d’un avertissement de niveau 3.
