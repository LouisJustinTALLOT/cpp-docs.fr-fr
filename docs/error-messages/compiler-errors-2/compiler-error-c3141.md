---
description: 'En savoir plus sur : erreur du compilateur C3141'
title: Erreur du compilateur C3141
ms.date: 11/04/2016
f1_keywords:
- C3141
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
ms.openlocfilehash: bc5ebc1376d17cead4697987e35b4733e8ab0a22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304205"
---
# <a name="compiler-error-c3141"></a>Erreur du compilateur C3141

'interface_name' : les interfaces ne prennent en charge que l’héritage public

Les interfaces définies avec le mot clé [interface (ou __interface)](../../cpp/interface.md) prennent uniquement en charge l’héritage public.

L’exemple suivant génère l’C3141 :

```cpp
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```
