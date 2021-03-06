---
description: 'En savoir plus sur : avertissement du compilateur C4687'
title: Avertissement du compilateur C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: ffa8e645aa82a8577d0cd39a4963b8008b6cf9a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180719"
---
# <a name="compiler-warning-c4687"></a>Avertissement du compilateur C4687

> '*classe*' : une classe abstraite sealed ne peut pas implémenter une interface'*interface*'

## <a name="remarks"></a>Notes

Un type abstrait sealed est généralement utile uniquement pour contenir des fonctions membres statiques.

Pour plus d’informations, consultez [abstract](../../extensions/abstract-cpp-component-extensions.md) et [sealed](../../extensions/sealed-cpp-component-extensions.md).

Par défaut, C4687 est émis en tant qu’erreur. Vous pouvez supprimer C4687 avec le pragma [Warning](../../preprocessor/warning.md) . Si vous êtes certain que vous souhaitez implémenter une interface dans un type abstrait sealed, vous pouvez supprimer C4687.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4687.

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
