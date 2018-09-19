---
title: Erreur du compilateur C2919 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6ee01e32cd1855855fa6ac071af159be8bac0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106829"
---
# <a name="compiler-error-c2919"></a>Erreur du compilateur C2919

'type' : les opérateurs ne peuvent pas être utilisés sur la surface publiée d'un type WinRT

Le système de type Windows Runtime ne prend pas en charge les fonctions membres d'opérateur dans la surface publiée d'un type. Cela est dû au fait que tous les langages ne peuvent pas consommer les fonctions membres d'opérateur. Vous pouvez créer des fonctions membres d'opérateur privé ou interne qui peuvent être appelées à partir du code C++ dans la même unité de compilation ou de classe.

Pour résoudre ce problème, supprimez la fonction membre de l'opérateur à partir de l'interface publique, ou remplacez-la par une fonction membre nommée. Par exemple, à la place de `operator==`, nommez la fonction membre `Equals`.