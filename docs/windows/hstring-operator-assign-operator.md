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
ms.openlocfilehash: 8e528bed14f3f6f3b35270975833bdd17fd777db
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422647"
---
# <a name="hstringoperator-operator"></a>HString::Operator=, opérateur

Déplace la valeur d’un autre **HString** objet actuel **HString** objet.

## <a name="syntax"></a>Syntaxe

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Paramètres

*other*<br/>
Un existant **HString** objet.

## <a name="remarks"></a>Notes

La valeur existants *autres* objet est copié dans le cours **HString** objet, puis le *autres* détruit.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)