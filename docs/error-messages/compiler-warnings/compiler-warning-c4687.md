---
title: Avertissement du compilateur C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 1978e1a35ba5b5d59b5961a21378d8af6921d145
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776312"
---
# <a name="compiler-warning-c4687"></a>Avertissement du compilateur C4687

'classe' : une classe abstraite sealed ne peut pas implémenter une interface 'interface'

Un type abstrait sealed n’est généralement utile de contenir des fonctions de membre statique.

Pour plus d’informations, consultez [abstraite](../../extensions/abstract-cpp-component-extensions.md)et [sealed](../../extensions/sealed-cpp-component-extensions.md).

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