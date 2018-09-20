---
title: Hstring::hstring, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59ec7c1635b825cc300e28e5c02e2a3864a6c123
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442251"
---
# <a name="hstringhstring-constructor"></a>HString::HString, constructeur

Initialise une nouvelle instance de la **HString** classe.

## <a name="syntax"></a>Syntaxe

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>Paramètres

*HSTR*<br/>
Un handle HSTRING.

*other*<br/>
Un existant **HString** objet.

## <a name="remarks"></a>Notes

Le premier constructeur initialise un nouveau **HString** objet est vide.

Le deuxième constructeur initialise un nouveau **HString** objet à la valeur existants *autres* paramètre et détruit le *autres* paramètre.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)