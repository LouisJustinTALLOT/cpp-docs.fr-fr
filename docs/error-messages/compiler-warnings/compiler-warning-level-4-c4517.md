---
title: Compilateur avertissement (niveau 4) C4517 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4517
dev_langs:
- C++
helpviewer_keywords:
- C4517
ms.assetid: 87cc12b8-7331-4f3a-a863-d6a75d9599c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f71fca2804a6869fbb58073eb0c11a3ac1f18153
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098881"
---
# <a name="compiler-warning-level-4-c4517"></a>Avertissement du compilateur (niveau 4) C4517

déclarations d’accès sont déconseillées ; déclarations using de membres constituent un meilleur choix

Le comité C++ ANSI a déclaré des déclarations d’accès (modification d’accès d’un membre dans une classe dérivée sans le [à l’aide de](../../cpp/using-declaration.md) mot clé) à être obsolètes. Déclarations d’accès ne peuvent pas pris en charge par les versions futures de C++.