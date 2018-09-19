---
title: Erreur du compilateur C3888 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9292f54fee467a5f8d01202b6ed7ca991b52d43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096455"
---
# <a name="compiler-error-c3888"></a>Erreur du compilateur C3888

'name' : l’expression const associée à cette donnée membre littérale n’est pas prise en charge par C++/CLI

La donnée membre *nom* déclarée avec le mot clé [literal](../../windows/literal-cpp-component-extensions.md) est initialisée avec une valeur qui n’est pas prise en charge par le compilateur. Le compilateur prend en charge uniquement les types constant, integral, enum et string. Il est probable que l’erreur **C3888** soit causée par l’utilisation d’un tableau d’octets pour l’initialisation de la donnée membre.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que le type de la donnée membre littérale déclarée est pris en charge.

## <a name="see-also"></a>Voir aussi

[literal](../../windows/literal-cpp-component-extensions.md)