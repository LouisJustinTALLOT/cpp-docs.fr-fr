---
title: __RTDynamicCast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- __RTDynamicCast
dev_langs:
- C++
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f94d60d4c6e804a9bd27293bb0eff67b29a1e8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092061"
---
# <a name="rtdynamiccast"></a>__RTDynamicCast

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
`true` si l’entrée est une référence ; `false` si l’entrée est un pointeur.

## <a name="return-value"></a>Valeur de retour

Pointeur vers le sous-objet approprié, en cas de réussite ; sinon, **NULL**.

## <a name="exceptions"></a>Exceptions

`bad_cast()` si l’entrée de `dynamic_cast<>` est une référence et que le cast échoue.

## <a name="remarks"></a>Notes

Convertit `inptr` en objet de type `TargetType`. Le type de `inptr` doit être un pointeur si `TargetType` est un pointeur ou une l-value si `TargetType` est une référence. `TargetType` doit être un pointeur ou une référence à un type de classe précédemment défini, ou un pointeur vers void.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|