---
title: __writeeflags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writeeflags
dev_langs:
- C++
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 875945c4116f99a0a7e8ef53666f432987ba0deb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424538"
---
# <a name="writeeflags"></a>__writeeflags

Écrit la valeur spécifiée dans le programme inscrivent d’état et contrôle (EFLAGS).

## <a name="syntax"></a>Syntaxe

```
void __writeeflags(unsigned Value);
void __writeeflags(unsigned __int64 Value);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Valeur*|[in] La valeur à écrire dans le Registre EFLAGS. Le `Value` paramètre est 32 bits de long pour une plateforme 32 bits et 64 bits long pour une plateforme 64 bits.|

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement sous forme de fonctions intrinsèques.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__readeflags](../intrinsics/readeflags.md)