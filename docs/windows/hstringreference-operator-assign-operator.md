---
title: HStringReference::Operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 933d332ce2653fd8ea907a5fafda524ae0220906
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408997"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator=, opérateur

Déplace la valeur d’un autre **HStringReference** objet actuel **HStringReference** objet.

## <a name="syntax"></a>Syntaxe

```cpp
HStringReference& operator=(HStringReference&& other) throw()  
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Un existant **HStringReference** objet.

## <a name="remarks"></a>Notes

La valeur existants *autres* objet est copié dans le cours **HStringReference** objet, puis le *autres* détruit.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HStringReference, classe](../windows/hstringreference-class.md)