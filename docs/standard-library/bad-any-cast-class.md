---
description: 'En savoir plus sur : classe bad_any_cast'
title: Classe bad_any_cast
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5b38405bf1fc826592995df4037c5853e88ad9eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321625"
---
# <a name="bad_any_cast-class"></a>Classe bad_any_cast

Objets levés par un échec `any_cast` .

## <a name="syntax"></a>Syntaxe

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>Fonctions Membre

|Nom|Description|
|-|-|
|[données](#what)|Retourne le type.|

## <a name="what"></a><a name="what"></a> données

Retourne le type.

```cpp
const char* what() const noexcept override;
```
