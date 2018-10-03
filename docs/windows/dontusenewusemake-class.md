---
title: DontUseNewUseMake (classe) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1f3a57401a3ab2efd45cab2dace127010c24e6
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235280"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Notes

Empêche l’utilisation d’opérateur `new` dans `RuntimeClass`. Par conséquent, vous devez utiliser le [Make, fonction](../windows/make-function.md) à la place.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                             | Description
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator nouveau](#operator-new) | Surcharge d’opérateur `new` et empêche l’utilisation dans `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DontUseNewUseMake`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="operator-new"></a>DontUseNewUseMake::operator nouveau

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Paramètres

*__unnamed0*<br/>
Un paramètre sans nom qui spécifie le nombre d’octets de mémoire à allouer.

*sélection élective*<br/>
Le type doit être allouée.

### <a name="return-value"></a>Valeur de retour

Fournit un moyen de passer des arguments supplémentaires si vous surchargez l’opérateur `new`.

### <a name="remarks"></a>Notes

Surcharge d’opérateur `new` et empêche l’utilisation dans `RuntimeClass`.
