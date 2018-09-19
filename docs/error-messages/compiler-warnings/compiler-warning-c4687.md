---
title: Avertissement du compilateur C4687 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4687
dev_langs:
- C++
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d813ce6d666431cfc3f74d1409012a4a0aec897
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118711"
---
# <a name="compiler-warning-c4687"></a>Avertissement du compilateur C4687

'classe' : une classe abstraite sealed ne peut pas implémenter une interface 'interface'

Un type abstrait sealed n’est généralement utile de contenir des fonctions de membre statique.

Pour plus d’informations, consultez [abstraite](../../windows/abstract-cpp-component-extensions.md)et [sealed](../../windows/sealed-cpp-component-extensions.md).

Par défaut, C4687 est émis en tant qu’erreur. Vous pouvez supprimer l’erreur C4687 avec le [avertissement](../../preprocessor/warning.md) pragma. Si vous êtes certain que vous souhaitez implémenter une interface dans un type abstrait sealed, vous pouvez supprimer C4687.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4687.

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```