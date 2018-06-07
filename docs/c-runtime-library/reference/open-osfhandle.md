---
title: _open_osfhandle | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af3783420389dc008e39c818c39406f0b2af8af5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569834"
---
# <a name="openosfhandle"></a>_open_osfhandle

Associe un descripteur de fichier Runtime C à un descripteur de fichier de système d’exploitation existant.

## <a name="syntax"></a>Syntaxe

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Paramètres

*osfhandle*<br/>
Descripteur de fichier de système d’exploitation.

*flags*<br/>
Types d’opération autorisés.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **_open_osfhandle** retourne un descripteur de fichier Runtime C. Sinon, elle retourne -1.

## <a name="remarks"></a>Notes

Le **_open_osfhandle** fonction alloue un descripteur de fichier Runtime C et associe le handle de fichier du système d’exploitation spécifié par *osfhandle*. Pour éviter un avertissement du compilateur, effectuez un cast du *osfhandle* argument à partir de **gérer** à **intptr_t**. Le *indicateurs* argument est une expression d’entier formée à partir d’une ou plusieurs des constantes de manifeste définies dans \<fcntl.h >. Quand plusieurs constantes manifestes sont utilisées pour former le *indicateurs* argument, les constantes sont combinées avec l’opérateur OR au niveau du bit ( **&#124;** ).

Ces constantes manifestes sont définis dans \<fcntl.h > :

|||
|-|-|
**\_O\_APPEND**|Positionne un pointeur de fichier à la fin du fichier avant chaque opération d’écriture.
**\_O\_RDONLY**|Ouvre le fichier pour un accès en lecture uniquement.
**\_O\_TEXTE**|Ouvre le fichier en mode texte (traduit).
**\_O\_WTEXT**|Ouvre le fichier en mode Unicode (UTF-16 traduit).

Le **_open_osfhandle** appel transfère la propriété du handle de fichier Win32 pour le descripteur de fichier. Pour fermer un fichier ouvert avec **_open_osfhandle**, appelez [ \_fermer](close.md). Le handle de fichier du système d’exploitation sous-jacent est également fermé par un appel à **_close**, donc il n’est pas nécessaire d’appeler la fonction Win32 **CloseHandle** sur le handle d’origine. Si le descripteur de fichier est détenu par un **fichier &#42;**  flux, puis en appelant [fclose](fclose-fcloseall.md) sur qui **fichier &#42;**  flux ferme également les deux le descripteur de fichier et le handle sous-jacent. Dans ce cas, n’appelez pas **_close** sur le descripteur de fichier.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
