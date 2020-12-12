---
description: 'En savoir plus sur : longjmp'
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: bfcbac2ea54e167f65f0d303e08d6450e53ff0e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97299980"
---
# <a name="longjmp"></a>longjmp

Restaure l’environnement de la pile et les paramètres régionaux d’exécution définis par un `setjmp` appel.

## <a name="syntax"></a>Syntaxe

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Paramètres

*env*<br/>
Variable dans laquelle l’environnement est stocké.

*value*<br/>
Valeur à retourner à l’appel `setjmp`.

## <a name="remarks"></a>Notes

La fonction **longjmp** restaure un environnement de pile et les paramètres régionaux d’exécution précédemment enregistrés dans *env* by `setjmp` . `setjmp` et **longjmp** offrent un moyen d’exécuter un non local **`goto`** ; ils sont généralement utilisés pour passer le contrôle d’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel et de retour normales.

Un appel à `setjmp` entraîne l’enregistrement de l’environnement de pile actuel dans *env*. Un appel ultérieur à **longjmp** restaure l’environnement enregistré et retourne le contrôle au point qui suit immédiatement l' `setjmp` appel correspondant. L’exécution reprend comme si *value* avait simplement été retourné par l’appel `setjmp`. Les valeurs de toutes les variables (à l’exception des variables de registre) accessibles au contrôle de réception de routine contiennent les valeurs qu’elles avaient lors de l’appel de **longjmp** . Les valeurs des variables de Registre sont imprévisibles. La valeur retournée par `setjmp` doit être différente de zéro. Si *value* est passé en tant que 0, la valeur 1 est substituée dans le retour effectif.

**Spécifique à Microsoft**

Dans le code Microsoft C++ sur Windows, **longjmp** utilise la même sémantique de déroulement de pile que le code de gestion des exceptions. Il est possible d’utiliser en toute sécurité dans les mêmes emplacements que les exceptions C++ peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et est accompagnée de quelques avertissements importants.

Appelez **longjmp** uniquement avant la fonction qui a appelé `setjmp` retournée ; sinon, les résultats sont imprévisibles.

Respectez les restrictions suivantes lors de l’utilisation de **longjmp**:

- Ne partez pas du principe que les valeurs des variables de Registre restent les mêmes. Les valeurs des variables de Registre dans l’appel de routine `setjmp` ne peuvent pas être restaurées aux valeurs correctes après l’exécution de **longjmp** .

- N’utilisez pas **longjmp** pour transférer le contrôle hors d’une routine de gestion des interruptions, à moins que l’interruption soit provoquée par une exception à virgule flottante. Dans ce cas, un programme peut retourner un gestionnaire d’interruption via **longjmp** s’il réinitialise d’abord le package mathématique à virgule flottante en appelant [_fpreset](fpreset.md).

- N’utilisez pas **longjmp** pour transférer le contrôle à partir d’une routine de rappel appelée directement ou indirectement par le code Windows.

- Si le code est compilé à l’aide de **/EHS** ou **/EHsc** et que la fonction qui contient l’appel **longjmp** est **`noexcept`** , les objets locaux de cette fonction ne peuvent pas être détruits pendant le déroulement de la pile.

**FIN spécifique à Microsoft**

> [!NOTE]
> Dans le code C++ portable, vous ne pouvez pas supposer `setjmp` et `longjmp` prendre en charge la sémantique d’objet c++. Plus précisément, une `setjmp` / `longjmp` paire d’appels a un comportement indéfini en cas de remplacement de `setjmp` et de `longjmp` par **`catch`** et **`throw`** appelle un destructeur non trivial pour tous les objets automatiques. Dans les programmes C++, nous vous recommandons d’utiliser le mécanisme de gestion des exceptions C++.

Pour plus d’informations, consultez [Utilisation de setjmp et longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_fpreset](fpreset.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
