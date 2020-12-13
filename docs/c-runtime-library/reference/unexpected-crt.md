---
description: 'En savoir plus sur : inattendu (CRT)'
title: unexpected (CRT)
ms.date: 11/04/2016
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 73c632c4dd5bfedbb1c3724e60786b348f77f0be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186634"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

Appelle **Terminate** ou Function que vous spécifiez à l’aide de **set_unexpected**.

## <a name="syntax"></a>Syntaxe

```C
void unexpected( void );
```

## <a name="remarks"></a>Notes

La routine **inattendue** n’est pas utilisée avec l’implémentation actuelle de la gestion des exceptions C++. les appels **inattendus** **se terminent** par défaut. Vous pouvez modifier ce comportement par défaut en écrivant une fonction d’arrêt personnalisée et en appelant **set_unexpected** avec le nom de votre fonction comme argument. appel **inattendu** de la dernière fonction donnée comme argument pour **set_unexpected**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**erreur**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[pire](terminate-crt.md)<br/>
