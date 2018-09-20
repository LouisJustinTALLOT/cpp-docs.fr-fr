---
title: SafeIntException, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a0eda94c370f978bd04d7c2de1dd3e06237e490
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437705"
---
# <a name="safeintexception-class"></a>SafeIntException, classe

Le `SafeInt` classe utilise **SafeIntException** pour identifier la raison pour laquelle une opération mathématique ne peut pas être effectuée.

## <a name="syntax"></a>Syntaxe

```cpp
class SafeIntException;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

[SafeIntException::SafeIntException](../windows/safeintexception-safeintexception.md)<br/>
Crée un **SafeIntException** objet.

## <a name="remarks"></a>Notes

Le [classe SafeInt](../windows/safeint-class.md) est la seule classe qui utilise le **SafeIntException** classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[SafeIntException Class](../windows/safeintexception-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** safeint.h

**Namespace :** msl::utilities

## <a name="see-also"></a>Voir aussi

[Bibliothèque SafeInt](../windows/safeint-library.md)<br/>
[SafeInt, classe](../windows/safeint-class.md)