---
title: Hstring::Set, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
dev_langs:
- C++
ms.assetid: c9b3d613-95c4-48b0-999d-f5baf0804faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6eb2261ab973245c78ec8f5e0269663e5181a0ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590039"
---
# <a name="hstringset-method"></a>HString::Set, méthode

Définit la valeur de cours **HString** objet à la chaîne de caractères larges spécifiée ou **HString** paramètre.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Paramètres

*str*  
Une chaîne à caractères larges.

*Len*  
La longueur maximale de la *str* paramètre qui est affectée à l’actuel **HString** objet.

*HSTR*  
Un existant **HString** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HString, classe](../windows/hstring-class.md)