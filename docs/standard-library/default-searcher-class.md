---
title: default_searcher, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 19643d0ab6f8e5e829b2e33cd5e3c479b1fcd0fb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268821"
---
# <a name="defaultsearcher-class"></a>default_searcher, classe

## <a name="syntax"></a>Syntaxe

```cpp
template <class ForwardIterator1, class BinaryPredicate = equal_to<>>
class default_searcher {
    default_searcher(ForwardIterator1 pat_first, ForwardIterator1 pat_last,
        BinaryPredicate pred = BinaryPredicate());
    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2>
        operator()(ForwardIterator2 first, ForwardIterator2 last) const;
};
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[default_searcher]()||

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator()]()||