---
title: _set_error_mode
ms.date: 11/04/2016
apiname:
- _set_error_mode
apilocation:
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
apitype: DLLExport
f1_keywords:
- set_error_mode
- _set_error_mode
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
ms.openlocfilehash: 8c95ed45423b791a688f05ea30f48e188826a797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356646"
---
# <a name="seterrormode"></a>_set_error_mode

Modifie **__error_mode** pour déterminer un emplacement non défini par défaut dans lequel le runtime C écrit un message d’erreur pour une erreur qui peut mettre fin au programme.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Contrôle le récepteur de sortie d’erreur en définissant la valeur de **__error_mode**. Par exemple, vous pouvez diriger la sortie vers une erreur standard ou utiliser le **MessageBox** API.

Le *mode_val* paramètre peut être défini à une des valeurs suivantes.

|Paramètre|Description|
|---------------|-----------------|
|**_OUT_TO_DEFAULT**|L’intercepteur d’erreurs est déterminé par **__app_type**.|
|**_OUT_TO_STDERR**|L'intercepteur d'erreurs est une erreur standard.|
|**_OUT_TO_MSGBOX**|L'intercepteur d'erreurs est une boîte de message.|
|**_REPORT_ERRMODE**|Rapport actuel **__error_mode** valeur.|

Si la valeur transmise est différente de celles répertoriées, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_set_error_mode** définit **errno** à **EINVAL** et retourne -1.

Lorsqu’il est utilisé avec un [assert](assert-macro-assert-wassert.md), **_set_error_mode** affiche l’instruction en échec dans la boîte de dialogue et vous donne la possibilité de choisir le **ignorer** bouton afin que vous puissiez continuer à exécuter le programme.

## <a name="requirements"></a>Configuration requise

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

[assert (macro), _assert, _wassert](assert-macro-assert-wassert.md)<br/>
