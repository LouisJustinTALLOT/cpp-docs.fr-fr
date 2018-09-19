---
title: __set_app_type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __set_app_type
- _set_app_type
apilocation:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __set_app_type
dev_langs:
- C++
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22d4c6da3b897d0158f790a0146e3f10f7aa385c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093119"
---
# <a name="setapptype"></a>__set_app_type

Définit le type d’application actuel.

## <a name="syntax"></a>Syntaxe

```cpp
void __set_app_type (
   int at
   )
```

#### <a name="parameters"></a>Paramètres

*at*<br/>
Valeur qui indique le type d’application. Les valeurs possibles sont :

|Value|Description|
|-----------|-----------------|
|_UNKNOWN_APP|Type d’application inconnu.|
|_CONSOLE_APP|Application console (ligne de commande).|
|_GUI_APP|Application GUI (Windows).|

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__set_app_type|internal.h|