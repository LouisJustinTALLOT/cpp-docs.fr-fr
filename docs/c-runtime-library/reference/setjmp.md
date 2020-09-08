---
title: setjmp
description: Référence d’API pour setjmp ; qui enregistre l’état actuel du programme.
ms.date: 08/14/2018
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
ms.openlocfilehash: 3ea08e5379433e313e08870f735322b7d985aa64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555603"
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

## <a name="return-value"></a>Valeur renvoyée

Retourne la valeur 0 après l’enregistrement de l’environnement de pile. Si **setjmp** retourne à la suite d’un `longjmp` appel, elle retourne l’argument de *valeur* de `longjmp` , ou si l’argument de *valeur* de `longjmp` est 0, **setjmp** retourne 1. Il n’y a pas d’erreur de retour.

## <a name="remarks"></a>Notes

La fonction **setjmp** enregistre un environnement de pile, que vous pouvez restaurer par la suite, à l’aide de `longjmp` . En cas d’utilisation conjointe de, **setjmp** et `longjmp` offrent un moyen d’exécuter un non local **`goto`** . Elles sont généralement utilisées pour passer le contrôle d’exécution au code de gestion des erreurs ou au code de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel ou de retour normales.

Un appel à **setjmp** enregistre l’environnement de pile actuel dans *env*. Un appel ultérieur à `longjmp` restaure l’environnement enregistré et retourne le contrôle au point juste après l’appel **setjmp** correspondant. Toutes les variables (à l’exception des variables de Registre) accessibles à la routine recevant le contrôle contiennent les valeurs qu’elles possédaient au moment où `longjmp` a été appelé.

Il n’est pas possible d’utiliser **setjmp** pour passer du code natif au code managé.

**Spécifique à Microsoft**

Dans le code Microsoft C++ sur Windows, **longjmp** utilise la même sémantique de déroulement de pile que le code de gestion des exceptions. Il est possible d’utiliser en toute sécurité dans les mêmes emplacements que les exceptions C++ peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et est accompagnée de quelques avertissements importants. Pour plus d’informations, consultez [longjmp](longjmp.md).

**FIN spécifique à Microsoft**

> [!NOTE]
> Dans le code C++ portable, vous ne pouvez pas supposer `setjmp` et `longjmp` prendre en charge la sémantique d’objet c++. Plus précisément, une `setjmp` / `longjmp` paire d’appels a un comportement indéfini en cas de remplacement de `setjmp` et de `longjmp` par **`catch`** et **`throw`** appelle un destructeur non trivial pour tous les objets automatiques. Dans les programmes C++, nous vous recommandons d’utiliser le mécanisme de gestion des exceptions C++.

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
[longjmp](longjmp.md)
