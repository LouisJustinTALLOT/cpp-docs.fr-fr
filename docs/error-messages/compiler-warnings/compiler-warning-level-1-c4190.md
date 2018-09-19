---
title: Compilateur Warning (level 1) C4190 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063734"
---
# <a name="compiler-warning-level-1-c4190"></a>Compilateur Warning (level 1) C4190

'identificateur1' a une liaison C spécifiée, mais retourne UDT 'identificateur2' qui est incompatible avec C

Une fonction ou un pointeur vers une fonction a un UDT (défini par l’utilisateur type, classe, structure, enum ou union) en tant que type de retour et `extern` une liaison « C ». Cela est légal si :

- Tous les appels à cette fonction se produisent à partir de C++.

- La définition de la fonction est en C++.

## <a name="example"></a>Exemple

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```