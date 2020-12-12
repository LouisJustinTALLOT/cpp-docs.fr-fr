---
description: 'En savoir plus sur : classe bad_function_call'
title: bad_function_call, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::bad_function_call
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
ms.openlocfilehash: 659630874f84ea9e7d164b560408b162f07e1f68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321597"
---
# <a name="bad_function_call-class"></a>bad_function_call, classe

Signale un appel de fonction incorrect.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_function_call : public std::exception {};
```

## <a name="remarks"></a>Notes

La classe décrit une exception levée pour indiquer qu’un appel à `operator()` sur une [classe function](../standard-library/function-class.md) est incorrect
