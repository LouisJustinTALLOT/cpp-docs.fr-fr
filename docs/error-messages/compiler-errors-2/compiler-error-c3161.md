---
description: 'En savoir plus sur : erreur du compilateur C3161'
title: Erreur du compilateur C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 4e45d64e1c1f318a126122148c2dd8e3ddb9c5af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203963"
---
# <a name="compiler-error-c3161"></a>Erreur du compilateur C3161

'interface' : l’imbrication d’une classe, d’une structure, d’une Union ou d’une interface dans une interface n’est pas conforme ; l’imbrication d’une interface dans une classe, une structure ou une Union n’est pas conforme

Un [__interface](../../cpp/interface.md) peut uniquement apparaître au niveau de la portée globale ou dans un espace de noms. Une classe, un struct ou une Union ne peut pas apparaître dans une interface.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3161.

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
