---
description: 'En savoir plus sur : inattendu (CRT)'
title: unexpected (CRT)
ms.date: 1/14/2021
api_name:
- unexpected
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 098d686e7c33d17020990b1db168d95c327d5112
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242902"
---
# <a name="unexpected-crt"></a>`unexpected` Ecran

Appelle **`terminate`** ou la fonction que vous spécifiez à l’aide de **`set_unexpected`** .

## <a name="syntax"></a>Syntaxe

```C
void unexpected( void );
```

## <a name="remarks"></a>Notes

La **`unexpected`** routine n’est pas utilisée avec l’implémentation actuelle de la gestion des exceptions C++. **`unexpected`** appelle **`terminate`** par défaut. Vous pouvez modifier ce comportement par défaut en écrivant une fonction d’arrêt personnalisée. Appelez **`set_unexpected`** avec le nom de votre fonction comme argument. **`unexpected`** appelle la dernière fonction passée à **`set_unexpected`** .

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`unexpected`**|`<eh.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[pire](terminate-crt.md)<br/>
