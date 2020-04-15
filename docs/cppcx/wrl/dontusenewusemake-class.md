---
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
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371552"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Notes

Empêche l’utilisation de l’opérateur `new` dans `RuntimeClass`. Par conséquent, vous devez utiliser la [fonction Make](make-function.md) à la place.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                             | Description
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::opérateur nouveau](#operator-new) | Surcharge l’opérateur `new` et l’empêche `RuntimeClass`d’être utilisé dans .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DontUseNewUseMake`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>DontUseNewUseMake::opérateur nouveau

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Paramètres

*__unnamed0*<br/>
Un paramètre anonyme qui spécifie le nombre d’octets de mémoire à allouer.

*Placement*<br/>
Le type à attribuer.

### <a name="return-value"></a>Valeur de retour

Fournit un moyen de passer des arguments `new`supplémentaires si vous surchargez l’opérateur .

### <a name="remarks"></a>Notes

Surcharge l’opérateur `new` et l’empêche `RuntimeClass`d’être utilisé dans .
