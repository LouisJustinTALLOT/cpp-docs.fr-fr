---
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
ms.openlocfilehash: b4527a29475f9e393dc5abf19b866d926bec2ccc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953139"
---
# <a name="longjmp"></a>longjmp

Restaure l’environnement de la pile et les paramètres régionaux d’exécution `setjmp` définis par un appel.

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

La fonction **longjmp** restaure un environnement de pile et les paramètres régionaux d’exécution précédemment enregistrés dans `setjmp` *env* by. `setjmp`et **longjmp** offrent un moyen d’exécuter une **instruction goto**non locale ; elles sont généralement utilisées pour passer le contrôle d’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans utiliser les conventions d’appel et de retour normales.

Un appel à `setjmp` entraîne l’enregistrement de l’environnement de pile actuel dans *env*. Un appel ultérieur à **longjmp** restaure l’environnement enregistré et retourne le contrôle au point qui suit immédiatement l’appel `setjmp` correspondant. L’exécution reprend comme si *value* avait simplement été retourné par l’appel `setjmp`. Les valeurs de toutes les variables (à l’exception des variables de registre) accessibles au contrôle de réception de routine contiennent les valeurs qu’elles avaient lors de l’appel de **longjmp** . Les valeurs des variables de Registre sont imprévisibles. La valeur retournée par `setjmp` doit être différente de zéro. Si *value* est passé en tant que 0, la valeur 1 est substituée dans le retour effectif.

**Section spécifique à Microsoft**

Dans Microsoft C++ code sur Windows, **longjmp** utilise la même sémantique de déroulement de pile que le code de gestion des exceptions. Il est possible d’utiliser en toute sécurité dans les C++ mêmes emplacements que les exceptions peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et est accompagnée de quelques avertissements importants.

Appelez **longjmp** uniquement avant la fonction qui a `setjmp` appelé retournée ; sinon, les résultats sont imprévisibles.

Respectez les restrictions suivantes lors de l’utilisation de **longjmp**:

- Ne partez pas du principe que les valeurs des variables de Registre restent les mêmes. Les valeurs des variables de Registre dans l’appel `setjmp` de routine ne peuvent pas être restaurées aux valeurs correctes après l’exécution de **longjmp** .

- N’utilisez pas **longjmp** pour transférer le contrôle hors d’une routine de gestion des interruptions, à moins que l’interruption soit provoquée par une exception à virgule flottante. Dans ce cas, un programme peut retourner un gestionnaire d’interruption par le biais de **longjmp** s’il réinitialise d’abord le package mathématique à virgule flottante en appelant [_fpreset](fpreset.md).

- N’utilisez pas **longjmp** pour transférer le contrôle à partir d’une routine de rappel appelée directement ou indirectement par le code Windows.

- Si le code est compilé à l’aide de **/EHS** ou **/EHsc** et que la fonction qui contient l’appel **longjmp** est **noexcept** , les objets locaux de cette fonction ne peuvent pas être détruits pendant le déroulement de la pile.

**FIN de la section spécifique à Microsoft**

> [!NOTE]
> Dans le C++ code portable, vous ne `setjmp` pouvez `longjmp` pas C++ supposer et prendre en charge la sémantique d’objet. Plus précisément, `setjmp` une paire d’appels a un / `longjmp` comportement indéfini si le `setjmp` remplacement `longjmp` de et par **catch** et **throw** appelle tous les destructeurs non triviales pour tous les objets automatiques. Dans C++ les programmes, nous vous recommandons d' C++ utiliser le mécanisme de gestion des exceptions.

Pour plus d’informations, consultez [Utilisation de setjmp et longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Consultez l’exemple relatif à [_fpreset](fpreset.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
