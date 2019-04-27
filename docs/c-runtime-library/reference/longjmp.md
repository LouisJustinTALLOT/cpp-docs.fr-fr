---
title: longjmp
ms.date: 08/14/2018
apiname:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: e5189ff7cb850acd9c9a1280f47fc9a1270f8b68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157403"
---
# <a name="longjmp"></a>longjmp

Restaure la pile environnement et l’exécution de paramètres régionaux définis un `setjmp` appeler.

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

Le **longjmp** fonction restaure la pile environnement et l’exécution de paramètres régionaux précédemment enregistré dans *env* par `setjmp`. `setjmp` et **longjmp** fournissent un moyen d’exécuter un non locaux **goto**; ils sont généralement utilisés pour passer le contrôle d’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans utiliser l’appel normal et conventions de retour.

Un appel à `setjmp` , l’environnement de pile actuel doit être enregistré dans *env*. Un appel ultérieur à **longjmp** restaure l’environnement enregistré et redonne le contrôle vers le point qui suit immédiatement le correspondantes `setjmp` appeler. L’exécution reprend comme si *value* avait simplement été retourné par l’appel `setjmp`. Les valeurs de toutes les variables (sauf les variables de Registre) qui sont accessibles à la routine recevant le contrôle contiennent les valeurs qu’elles avaient quand **longjmp** a été appelée. Les valeurs des variables de Registre sont imprévisibles. La valeur retournée par `setjmp` doit être différente de zéro. Si *value* est passé en tant que 0, la valeur 1 est substituée dans le retour effectif.

**Section spécifique à Microsoft**

Dans le code C++ de Microsoft sur Windows, **longjmp** utilise la même sémantique de déroulement de pile en tant que code de gestion des exceptions. Il est sûr à utiliser dans les mêmes emplacements que les exceptions C++ peuvent être déclenchées. Toutefois, cette utilisation n’est pas portable et il est fourni avec quelques avertissements importants.

Appelez uniquement **longjmp** avant que la fonction appelée `setjmp` retourne ; sinon, les résultats sont imprévisibles.

Respecter les restrictions suivantes lors de l’utilisation **longjmp**:

- Ne partez pas du principe que les valeurs des variables de Registre restent les mêmes. Les valeurs des variables de Registre dans la routine qui appelle `setjmp` ne peut pas être restaurées aux valeurs appropriées après **longjmp** est exécutée.

- N’utilisez pas **longjmp** pour transférer le contrôle en dehors d’une routine de gestion d’interruption, sauf si l’interruption est provoquée par une exception de virgule flottante. Dans ce cas, il peut retourner un programme à partir d’un gestionnaire d’interruption par le biais de **longjmp** si elle réinitialise tout d’abord le package mathématique à virgule flottante en appelant [_fpreset](fpreset.md).

- N’utilisez pas **longjmp** pour transférer le contrôle à partir d’une routine de rappel appelée directement ou indirectement par le code de Windows.

- Si le code est compilé à l’aide de **/EHs** ou **/EHsc** et la fonction qui contient le **longjmp** appel est **noexcept** objets avant le contenu local dans cette fonction ne peut pas être détruite pendant le déroulement de pile.

**FIN de la section spécifique à Microsoft**

> [!NOTE]
> Dans le code C++ portable, vous ne pouvez pas supposer `setjmp` et `longjmp` prennent en charge la sémantique d’objet C++. Plus précisément, un `setjmp` / `longjmp` appel paire a un comportement indéfini si en remplaçant le `setjmp` et `longjmp` par **catch** et **lever** appellerait tous les destructeurs non triviaux pour tous les objets automatiques. Dans les programmes C++, nous vous recommandons de qu'utiliser le mécanisme de gestion des exceptions C++.

Pour plus d’informations, consultez [Utilisation de setjmp et longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_fpreset](fpreset.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
