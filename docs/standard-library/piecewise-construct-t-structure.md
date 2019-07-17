---
title: piecewise_contruct_t Structure
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 6a9a6af97ca5c7751d64cd1fa70c9d9eba87da7c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268361"
---
# <a name="piecewisecontructt-structure"></a>piecewise_contruct_t Structure

Le struct `piecewise_construct_t` est un type de structure vide permet de garder le constructeur distinct et la surcharge de fonction. Plus précisément, `pair` a un constructeur avec `piecewise_construct_t` comme premier argument, suivies de deux `tuple` arguments.

## <a name="syntax"></a>Syntaxe

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
