---
title: restrictions relatives à fonction main | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93f5cce15d4db9f7f6d4e3361d22028fccd676f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117359"
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