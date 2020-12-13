---
description: 'En savoir plus sur : erreur du compilateur C2757'
title: Erreur du compilateur C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: e0be0f2a4c8dc5a5646400cbd0fa99e343ea82d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336185"
---
# <a name="compiler-error-c2757"></a>Erreur du compilateur C2757

'Symbol' : un symbole portant ce nom existe déjà et, par conséquent, ce nom ne peut pas être utilisé comme nom d’espace de noms

Un symbole utilisé dans la compilation actuelle en tant qu’identificateur d’espace de noms est déjà utilisé dans un assembly référencé.

L’exemple suivant génère l’C2757 :

```cpp
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

Puis,

```cpp
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
