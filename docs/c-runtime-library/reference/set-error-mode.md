---
title: _set_error_mode
ms.date: 11/04/2016
api_name:
- _set_error_mode
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: c1bb617e0f3792f2ac41d59df13d184423d56a9e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562036"
---
# <a name="_set_error_mode"></a>_set_error_mode

Modifie **__error_mode** pour déterminer un emplacement autre que celui par défaut dans lequel le runtime C écrit un message d’erreur pour une erreur qui peut mettre fin au programme.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _set_error_mode(
   int mode_val
);
```

### <a name="parameters"></a>Paramètres

*mode_val*<br/>
Destination des messages d'erreur.

## <a name="return-value"></a>Valeur de retour

Retourne l'ancien paramètre ou -1 si une erreur se produit.

## <a name="remarks"></a>Notes

Contrôle le récepteur de sortie d’erreur en définissant la valeur de **__error_mode**. Par exemple, vous pouvez diriger la sortie vers une erreur standard ou utiliser l’API **MessageBox** .

Le paramètre *mode_val* peut être défini sur l’une des valeurs suivantes.

|Valeur|Description|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|Le récepteur d’erreurs est déterminé par **__app_type**.|
|**_OUT_TO_STDERR**|L'intercepteur d'erreurs est une erreur standard.|
|**_OUT_TO_MSGBOX**|L'intercepteur d'erreurs est une boîte de message.|
|**_REPORT_ERRMODE**|Signale la valeur de **__error_mode** actuelle.|

Si la valeur transmise est différente de celles répertoriées, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_set_error_mode** affecte à **errno** la valeur **EINVAL** et retourne-1.

Lorsqu’il est utilisé avec une [assertion](assert-macro-assert-wassert.md), **_set_error_mode** affiche l’instruction failed dans la boîte de dialogue et vous donne la possibilité de choisir le bouton **Ignorer** afin que vous puissiez continuer à exécuter le programme.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_error_mode**|\<stdlib.h>|

## <a name="example"></a>Exemple

```C
// crt_set_error_mode.c
// compile with: /c
#include <stdlib.h>
#include <assert.h>

int main()
{
   _set_error_mode(_OUT_TO_STDERR);
   assert(2+2==5);
}
```

```Output
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Voir aussi

[Macro Assert, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
