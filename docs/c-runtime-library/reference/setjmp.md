---
title: setjmp
ms.date: 08/14/2018
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 9f1a2b71a7b8fc7603c36938879348dca16288e2
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210508"
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

Retourne la valeur 0 après l’enregistrement de l’environnement de pile. Si **setjmp** retourne à la suite d’un `longjmp` appeler, elle retourne le *valeur* argument de `longjmp`, ou si le *valeur* argument de `longjmp` est 0, **setjmp** retourne 1. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **setjmp** fonction enregistre un environnement de pile, vous pouvez restaurer par la suite, à l’aide de `longjmp`. Utilisés ensemble, **setjmp** et `longjmp` fournissent un moyen d’exécuter non local **goto**. Elles sont généralement utilisées pour passer le contrôle d’exécution au code de gestion des erreurs ou au code de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel ou de retour normales.

Un appel à **setjmp** enregistre l’environnement de pile actuel dans *env*. Un appel ultérieur à `longjmp` restaure l’environnement enregistré et redonne le contrôle au point juste après le correspondantes **setjmp** appeler. Toutes les variables (à l’exception des variables de Registre) accessibles à la routine recevant le contrôle contiennent les valeurs qu’elles possédaient au moment où `longjmp` a été appelé.

Il n’est pas possible d’utiliser **setjmp** à passer du code natif au code managé.

**Section spécifique à Microsoft**

Dans le code C++ de Microsoft sur Windows, **longjmp** utilise la même sémantique de déroulement de pile en tant que code de gestion des exceptions. Il est sûr à utiliser dans les mêmes emplacements que les exceptions C++ peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et il est fourni avec quelques avertissements importants. Pour plus d’informations, consultez [longjmp](longjmp.md).

**FIN de la section spécifique à Microsoft**

> [!NOTE]
> Dans le code C++ portable, vous ne pouvez pas supposer `setjmp` et `longjmp` prennent en charge la sémantique d’objet C++. Plus précisément, un `setjmp` / `longjmp` appel paire a un comportement indéfini si en remplaçant le `setjmp` et `longjmp` par **catch** et **lever** appellerait tous les destructeurs non triviaux pour tous les objets automatiques. Dans les programmes C++, nous vous recommandons de qu'utiliser le mécanisme de gestion des exceptions C++.

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
