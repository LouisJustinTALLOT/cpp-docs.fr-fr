---
description: 'En savoir plus sur : erreur du compilateur C3869'
title: Erreur du compilateur C3869
ms.date: 11/04/2016
f1_keywords:
- C3869
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
ms.openlocfilehash: 8b5bcd59bfeb5407edcfbea6217212dfc44c6643
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222786"
---
# <a name="compiler-error-c3869"></a>Erreur du compilateur C3869

la contrainte gcnew ne contient pas de liste de paramètres vide' () '

La **`gcnew`** contrainte spéciale a été spécifiée sans la liste de paramètres vide. Pour plus d’informations, consultez [contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3869.

```cpp
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```
