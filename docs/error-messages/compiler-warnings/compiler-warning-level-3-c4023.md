---
title: Compilateur avertissement (niveau 3) C4023 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe457f9a6181fa11b34dd615ad4d5b9637c8bddc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045170"
---
# <a name="compiler-warning-level-3-c4023"></a>Avertissement du compilateur (niveau 3) C4023

'symbole' : pointeur based passé à une fonction non prototypée : paramètre nombre

Passer un pointeur based à une fonction non prototypée entraîne la normalisation du pointeur, avec des résultats imprévisibles.

Vous pouvez résoudre cet avertissement en utilisant des fonctions prototypées auxquelles sont passées des pointeurs based.