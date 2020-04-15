---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 9791cff55ccd55c32d124ab89cc43ab54c0f9c69
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360970"
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
Valeur qui indique le type d’application. Les valeurs possibles sont les suivantes :

|Valeur|Description|
|----------------|-----------------|
|_crt_unknown_app|Type d’application inconnu.|
|_crt_console_app|Application console (ligne de commande).|
|_crt_gui_app|Application GUI (Windows).|

## <a name="remarks"></a>Notes

Normalement, il est inutile d’appeler cette fonction. Elle fait partie du code de démarrage du runtime C qui s’exécute avant que `main` ne soit appelé dans votre application.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_set_app_type|process.h|
