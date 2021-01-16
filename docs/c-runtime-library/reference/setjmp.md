---
title: setjmp
description: Référence d’API pour setjmp ; qui enregistre l’état actuel du programme.
ms.date: 1/14/2021
api_name:
- setjmp
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 0830cf253553523747a815efc950d4cf75b36647
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242642"
---
# `setjmp`

Enregistre l’état actuel du programme.

## <a name="syntax"></a>Syntaxe

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Paramètres

*`env`*\
Variable dans laquelle l’environnement est stocké.

## <a name="return-value"></a>Valeur renvoyée

Retourne la valeur 0 après l’enregistrement de l’environnement de pile. Si **`setjmp`** retourne à la suite d’un `longjmp` appel, elle retourne l’argument de *valeur* de `longjmp` , ou si l’argument de *valeur* de `longjmp` est 0, **`setjmp`** retourne 1. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Remarques

La **`setjmp`** fonction enregistre un environnement de pile, que vous pouvez restaurer par la suite, à l’aide de `longjmp` . Lorsqu’ils sont utilisés ensemble, ils **`setjmp`** `longjmp` offrent un moyen d’exécuter un non local **`goto`** . Elles sont généralement utilisées pour passer le contrôle d’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel ou de retour normales.

Un appel à **`setjmp`** enregistre l’environnement de pile actuel dans *`env`* . Un appel ultérieur à `longjmp` restaure l’environnement enregistré et retourne le contrôle au point juste après l’appel correspondant **`setjmp`** . Toutes les variables (à l’exception des variables de Registre) accessibles à la routine recevant le contrôle contiennent les valeurs qu’elles possédaient au moment où `longjmp` a été appelé.

Il n’est pas possible d’utiliser **`setjmp`** pour passer du code natif au code managé.

**Spécifique à Microsoft**

Dans le code Microsoft C++ sur Windows, **`longjmp`** utilise la même sémantique de déroulement de pile que le code de gestion des exceptions. Il est possible d’utiliser en toute sécurité dans les mêmes emplacements que les exceptions C++ peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et est accompagnée de quelques inconvénients importants. Pour plus d’informations, consultez [`longjmp`](longjmp.md).

**FIN spécifique à Microsoft**

> [!NOTE]
> Dans le code C++ portable, vous ne pouvez pas supposer `setjmp` et `longjmp` prendre en charge la sémantique d’objet c++. Plus précisément, une `setjmp` / `longjmp` paire d’appels a un comportement indéfini en cas de remplacement de `setjmp` et de `longjmp` par **`catch`** et **`throw`** appelle un destructeur non trivial pour tous les objets automatiques. Dans les programmes C++, nous vous recommandons d’utiliser le mécanisme de gestion des exceptions C++.

Pour plus d’informations, [consultez `setjmp` utilisation `longjmp` de et ](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`setjmp`**|\<setjmp.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple pour [`_fpreset`](fpreset.md) .

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)\
[`longjmp`](longjmp.md)
