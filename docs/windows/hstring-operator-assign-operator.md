---
title: HString::Operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9294650db7a1b18c2542603988952a80b3f1905d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598543"
---
# <a name="hstringoperator-operator"></a>HString::Operator=, opérateur

Déplace la valeur d’un autre **HString** objet actuel **HString** objet.

## <a name="syntax"></a>Syntaxe

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Paramètres

*other*  
Un existant **HString** objet.

## <a name="remarks"></a>Notes

La valeur existants *autres* objet est copié dans le cours **HString** objet, puis le *autres* détruit.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)