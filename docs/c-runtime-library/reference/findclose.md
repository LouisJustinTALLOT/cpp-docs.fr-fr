---
title: _findclose
ms.date: 4/2/2020
api_name:
- _findclose
- _o__findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: dffe2ff71f1eecaec78c75867ebb7e34a963ee3a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911806"
---
# <a name="_findclose"></a>_findclose

Ferme le handle de recherche spécifié et libère les ressources associées.

## <a name="syntax"></a>Syntaxe

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Paramètres

*traitée*<br/>
Handle de recherche retourné par un appel précédent à **_findfirst**.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_findclose** retourne 0. Sinon, elle retourne-1 et affecte à **errno** la valeur **ENOENT**, ce qui indique qu’aucun autre fichier correspondant n’a été trouvé.

## <a name="remarks"></a>Notes 

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Appels système](../../c-runtime-library/system-calls.md)<br/>
[Fonctions de recherche de nom de fichier](../../c-runtime-library/filename-search-functions.md)<br/>
