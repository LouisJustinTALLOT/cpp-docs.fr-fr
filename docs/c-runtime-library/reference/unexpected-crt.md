---
title: unexpected (CRT)
ms.date: 11/04/2016
apiname:
- unexpected
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
apitype: DLLExport
f1_keywords:
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 78538c0a10e183e72c742b041b297275c0859a03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155483"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

Appels **Terminer** ou fonction que vous spécifiez à l’aide de **set_unexpected**.

## <a name="syntax"></a>Syntaxe

```C
void unexpected( void );
```

## <a name="remarks"></a>Notes

Le **inattendue** routine n’est pas utilisée avec l’implémentation actuelle de gestion des exceptions C++. **inattendue** appels **Terminer** par défaut. Vous pouvez modifier ce comportement par défaut en écrivant une fonction d’arrêt personnalisée et en appelant **set_unexpected** avec le nom de votre fonction comme argument. **inattendue** appelle la dernière fonction donnée comme argument à **set_unexpected**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
