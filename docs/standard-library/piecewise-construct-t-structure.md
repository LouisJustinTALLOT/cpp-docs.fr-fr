---
description: 'En savoir plus sur : structure piecewise_contruct_t'
title: Structure piecewise_contruct_t
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 7fefacff75b47c25cb9ae07cc894498eadb551df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340747"
---
# <a name="piecewise_contruct_t-structure"></a>Structure piecewise_contruct_t

Le struct `piecewise_construct_t` est un type de structure vide utilisé pour conserver une surcharge de constructeur et de fonction distincte. En particulier, `pair` a un constructeur avec `piecewise_construct_t` comme premier argument, suivi de deux `tuple` arguments.

## <a name="syntax"></a>Syntaxe

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
