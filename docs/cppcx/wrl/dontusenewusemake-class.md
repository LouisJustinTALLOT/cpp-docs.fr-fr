---
description: 'En savoir plus sur : classe DontUseNewUseMake'
title: DontUseNewUseMake (classe)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: f6b6740e472123e59565e3bad16e4a535a4e17fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272901"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Notes

Empêche l’utilisation `new` de l’opérateur dans `RuntimeClass` . Par conséquent, vous devez utiliser la [fonction Make](make-function.md) à la place.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                             | Description
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake :: operator new](#operator-new) | Surcharge `new` l’opérateur et l’empêche d’être utilisé dans `RuntimeClass` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DontUseNewUseMake`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a> DontUseNewUseMake :: operator new

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Paramètres

*__unnamed0*<br/>
Paramètre sans nom qui spécifie le nombre d’octets de mémoire à allouer.

*importation*<br/>
Type à allouer.

### <a name="return-value"></a>Valeur renvoyée

Fournit un moyen de passer des arguments supplémentaires si vous surchargez l’opérateur `new` .

### <a name="remarks"></a>Notes

Surcharge `new` l’opérateur et l’empêche d’être utilisé dans `RuntimeClass` .
