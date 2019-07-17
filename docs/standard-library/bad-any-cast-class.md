---
title: bad_any_cast, classe
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5172281d1918a8b4ac33bcf412bf4be82b04ef56
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268681"
---
# <a name="badanycast-class"></a>bad_any_cast, classe

Objets levées par un échec `any_cast`.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>Fonctions membres

|||
|-|-|
|[what](#what)|Retourne le type.|

## <a name="what"></a> ce que

Retourne le type.

```cpp
const char* what() const noexcept override;
```
