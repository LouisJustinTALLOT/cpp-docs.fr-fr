---
title: setjmp
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
ms.openlocfilehash: 4a88467f5b94ceae4281a35f1486380a877be2e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948246"
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

Retourne la valeur 0 après l’enregistrement de l’environnement de pile. Si **setjmp** retourne à la suite d’un `longjmp` appel, elle retourne l’argument de *valeur* `longjmp`de, ou si l’argument de `longjmp` *valeur* de est 0, **setjmp** retourne 1. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

La fonction **setjmp** enregistre un environnement de pile, que vous pouvez restaurer par la `longjmp`suite, à l’aide de. En cas d’utilisation conjointe de `longjmp` , setjmp et offrent un moyen d’exécuter une **instruction goto**non locale. Elles sont généralement utilisées pour passer le contrôle d’exécution au code de gestion des erreurs ou au code de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel ou de retour normales.

Un appel à **setjmp** enregistre l’environnement de pile actuel dans *env*. Un appel ultérieur à `longjmp` restaure l’environnement enregistré et retourne le contrôle au point juste après l’appel **setjmp** correspondant. Toutes les variables (à l’exception des variables de Registre) accessibles à la routine recevant le contrôle contiennent les valeurs qu’elles possédaient au moment où `longjmp` a été appelé.

Il n’est pas possible d’utiliser **setjmp** pour passer du code natif au code managé.

**Section spécifique à Microsoft**

Dans Microsoft C++ code sur Windows, **longjmp** utilise la même sémantique de déroulement de pile que le code de gestion des exceptions. Il est possible d’utiliser en toute sécurité dans les C++ mêmes emplacements que les exceptions peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et est accompagnée de quelques avertissements importants. Pour plus d’informations, consultez [longjmp](longjmp.md).

**FIN de la section spécifique à Microsoft**

> [!NOTE]
> Dans le C++ code portable, vous ne `setjmp` pouvez `longjmp` pas C++ supposer et prendre en charge la sémantique d’objet. Plus précisément, `setjmp` une paire d’appels a un / `longjmp` comportement indéfini si le `setjmp` remplacement `longjmp` de et par **catch** et **throw** appelle tous les destructeurs non triviales pour tous les objets automatiques. Dans C++ les programmes, nous vous recommandons d' C++ utiliser le mécanisme de gestion des exceptions.

Pour plus d’informations, consultez [Utilisation de setjmp et longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Consultez l’exemple relatif à [_fpreset](fpreset.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
