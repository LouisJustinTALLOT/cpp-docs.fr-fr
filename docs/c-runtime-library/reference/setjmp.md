---
title: setjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc4673485577f5a12024d31e94063c82a8c7b8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407250"
---
# <a name="setjmp"></a>setjmp

Enregistre l’état actuel du programme.

## <a name="syntax"></a>Syntaxe

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Paramètres

*env*<br/>
Variable dans laquelle l’environnement est stocké.

## <a name="return-value"></a>Valeur de retour

Retourne la valeur 0 après l’enregistrement de l’environnement de pile. Si **setjmp** retourne à la suite d’un **longjmp** appeler, elle retourne le **valeur** argument de **longjmp**, ou si le **valeur**  argument de **longjmp** est 0, **setjmp** renvoie la valeur 1. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **setjmp** fonction enregistre un environnement de la pile, vous pouvez restaurer par la suite, à l’aide de **longjmp**. Utilisés conjointement, **setjmp** et **longjmp** fournissent un moyen d’exécuter non local **goto**. Elles sont généralement utilisées pour passer le contrôle d’exécution au code de gestion des erreurs ou au code de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel ou de retour normales.

Un appel à **setjmp** enregistre l’environnement actuel de la pile dans *env*. Un appel ultérieur à **longjmp** restaure l’environnement enregistré et retourne le contrôle au point juste après le correspondant **setjmp** appeler. Toutes les variables (à l’exception des variables de Registre) accessibles à la routine de réception contrôle contiennent les valeurs qu’elles avaient lorsque **longjmp** a été appelée.

Il n’est pas possible d’utiliser **setjmp** pour accéder à partir de code natif au code managé.

**Remarque** **setjmp** et **longjmp** ne prennent pas en charge la sémantique d’objet C++. Dans les programmes C++, utilisez le mécanisme de gestion des exceptions C++.

Pour plus d’informations, consultez [Utilisation de setjmp et longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_fpreset](fpreset.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)<br/>
[_setjmp3](../../c-runtime-library/setjmp3.md)<br/>
