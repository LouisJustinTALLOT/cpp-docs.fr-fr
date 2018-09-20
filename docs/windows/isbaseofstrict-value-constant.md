---
title: Isbaseofstrict::value, constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: 4a0cdab0-ba03-482b-babf-eeec519ba687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65b69c974e74ff68a1af2e17ff1fc8f03e03e3af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439287"
---
# <a name="isbaseofstrictvalue-constant"></a>IsBaseOfStrict::value, constante

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
static const bool value = __is_base_of(Base, Derived);
```

## <a name="remarks"></a>Notes

Indique si un type est la base d’un autre.

**valeur** est **true** si type `Base` est une classe de base du type `Derived`, sinon il est **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[IsBaseOfStrict, structure](../windows/isbaseofstrict-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)