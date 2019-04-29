---
title: bad_function_call, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::bad_function_call
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
ms.openlocfilehash: 6d0a3f5f5b6ac48d23b937b04b4521799ba31502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376391"
---
# <a name="badfunctioncall-class"></a>bad_function_call, classe

Signale un appel de fonction incorrect.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_function_call : public std::exception {};
```

## <a name="remarks"></a>Notes

La classe décrit une exception levée pour indiquer qu’un appel à `operator()` sur une [classe function](../standard-library/function-class.md) est incorrect
