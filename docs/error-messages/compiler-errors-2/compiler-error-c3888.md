---
description: 'En savoir plus sur : erreur du compilateur C3888'
title: Erreur du compilateur C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 5b47d78d0d6c75f4bdd266f95fff2ce4ab025d4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274318"
---
# <a name="compiler-error-c3888"></a>Erreur du compilateur C3888

'name' : l’expression const associée à cette donnée membre littérale n’est pas prise en charge par C++/CLI

La donnée membre *nom* déclarée avec le mot clé [literal](../../extensions/literal-cpp-component-extensions.md) est initialisée avec une valeur qui n’est pas prise en charge par le compilateur. Le compilateur prend en charge uniquement les types constant, integral, enum et string. Il est probable que l’erreur **C3888** soit causée par l’utilisation d’un tableau d’octets pour l’initialisation de la donnée membre.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que le type de la donnée membre littérale déclarée est pris en charge.

## <a name="see-also"></a>Voir aussi

[literal](../../extensions/literal-cpp-component-extensions.md)
