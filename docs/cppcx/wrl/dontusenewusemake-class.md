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
ms.openlocfilehash: 02420f2657c7d7d6a7a0294f0321717a3bb2b5d7
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784273"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Notes

Empêche l’utilisation d’opérateur `new` dans `RuntimeClass`. Par conséquent, vous devez utiliser le [Make, fonction](make-function.md) à la place.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

Nom                                             | Description
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator new](#operator-new) | Surcharge d’opérateur `new` et empêche l’utilisation dans `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DontUseNewUseMake`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="operator-new"></a>DontUseNewUseMake::operator new

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

*placement*<br/>
Le type doit être allouée.

### <a name="return-value"></a>Valeur de retour

Fournit un moyen de passer des arguments supplémentaires si vous surchargez l’opérateur `new`.

### <a name="remarks"></a>Notes

Surcharge d’opérateur `new` et empêche l’utilisation dans `RuntimeClass`.
