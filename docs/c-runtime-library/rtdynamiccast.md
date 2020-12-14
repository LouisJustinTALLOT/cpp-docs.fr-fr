---
description: 'En savoir plus sur : __RTDynamicCast'
title: __RTDynamicCast
ms.date: 11/04/2016
api_name:
- __RTDynamicCast
api_location:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __RTDynamicCast
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
ms.openlocfilehash: 8e9cb906468c02ac065601e8f093b0e97c1b70bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284484"
---
# <a name="__rtdynamiccast"></a>__RTDynamicCast

Implémentation du runtime de l’opérateur [dynamic_cast](../cpp/dynamic-cast-operator.md).

## <a name="syntax"></a>Syntaxe

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>Paramètres

*inptr*<br/>
Pointeur vers un objet polymorphe.

*VfDelta*<br/>
Décalage du pointeur de fonction virtuel dans l’objet.

*SrcType*<br/>
Type statique d’objet vers lequel pointe le paramètre `inptr`.

*TargetType*<br/>
Résultat prévu de cast.

*isReference*<br/>
**`true`** Si l’entrée est une référence ; **`false`** si l’entrée est un pointeur.

## <a name="return-value"></a>Valeur renvoyée

Pointeur vers le sous-objet approprié, en cas de réussite ; Sinon, **null**.

## <a name="exceptions"></a>Exceptions

`bad_cast()` si l’entrée de `dynamic_cast<>` est une référence et que le cast échoue.

## <a name="remarks"></a>Notes

Convertit `inptr` en objet de type `TargetType`. Le type de `inptr` doit être un pointeur si `TargetType` est un pointeur ou une l-value si `TargetType` est une référence. `TargetType` doit être un pointeur ou une référence à un type de classe précédemment défini, ou un pointeur vers void.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|
