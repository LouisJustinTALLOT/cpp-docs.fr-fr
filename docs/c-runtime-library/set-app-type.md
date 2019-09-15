---
title: _set_app_type
ms.date: 11/04/2016
api_name:
- _set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 7e04d88d9e9981e35b7d4c80c11d27c868219f65
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957920"
---
# <a name="_set_app_type"></a>_set_app_type

Fonction interne utilisée au démarrage pour indiquer à la bibliothèque CRT si l’application est une application console ou une application GUI.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>Paramètres

*appType*<br/>
Valeur qui indique le type d’application. Les valeurs possibles sont :

|Valeur|Description|
|----------------|-----------------|
|_crt_unknown_app|Type d’application inconnu.|
|_crt_console_app|Application console (ligne de commande).|
|_crt_gui_app|Application GUI (Windows).|

## <a name="remarks"></a>Notes

Normalement, il est inutile d’appeler cette fonction. Elle fait partie du code de démarrage du runtime C qui s’exécute avant que `main` ne soit appelé dans votre application.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|_set_app_type|process.h|
