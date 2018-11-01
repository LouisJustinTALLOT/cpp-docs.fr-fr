---
title: Restrictions relatives à la fonction main
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555733"
---
# <a name="main-function-restrictions"></a>Restrictions relatives à la fonction main

Plusieurs restrictions s’appliquent à la **principal** fonction qui ne s’appliquent pas à toutes les autres fonctions C++. Le **principal** fonction :

- Ne peut pas être surchargé (consultez [surcharge de fonction](function-overloading.md)).

- Ne peut pas être déclaré en tant que **inline**.

- Ne peut pas être déclaré en tant que **statique**.

- son adresse ne peut pas être prise.

- Ne peut pas être appelé.

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)