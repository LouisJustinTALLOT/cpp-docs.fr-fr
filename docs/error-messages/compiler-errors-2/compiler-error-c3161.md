---
title: Erreur du compilateur C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761814"
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
