---
title: longjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6c26cae9a3fe83012387c93e31c4005d5614d97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401719"
---
# <a name="longjmp"></a>longjmp

Restaure l’environnement de la pile et les paramètres régionaux d’exécution.

## <a name="syntax"></a>Syntaxe

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Paramètres

*Env* Variable dans l’environnement dans lequel est stocké.

*valeur* valeur à retourner à **setjmp** appeler.

## <a name="remarks"></a>Notes

Le **longjmp** fonction restaure la pile environnement et l’exécution de paramètres régionaux précédemment enregistrée dans *env* par **setjmp**. **setjmp** et **longjmp** fournissent un moyen d’exécuter un non locaux **goto**; ils sont généralement utilisés pour passer le contrôle de l’exécution au code de gestion des erreurs ou de récupération dans une routine appelée précédemment sans à l’aide de l’appel normal et les conventions de retournées.

Un appel à **setjmp** provoque l’environnement actuel de la pile doit être enregistré dans *env*. Un appel ultérieur à **longjmp** restaure l’environnement enregistré et retourne le contrôle au point immédiatement après le correspondant **setjmp** appeler. L’exécution reprend comme si *valeur* a simplement été retourné par le **setjmp** appeler. Les valeurs de toutes les variables (à l’exception des variables de Registre) qui sont accessibles à la routine de réception contrôle contiennent les valeurs qu’elles avaient lorsque **longjmp** a été appelée. Les valeurs des variables de Registre sont imprévisibles. La valeur retournée par **setjmp** doit être différente de zéro. Si *value* est passé en tant que 0, la valeur 1 est substituée dans le retour effectif.

Appelez **longjmp** avant la fonction appelée **setjmp** retourne ; sinon, les résultats sont imprévisibles.

Respecter les restrictions suivantes lors de l’utilisation **longjmp**:

- Ne partez pas du principe que les valeurs des variables de Registre restent les mêmes. Les valeurs des variables de Registre dans l’appel de routine **setjmp** ne peut pas être restaurés sur les valeurs appropriées après **longjmp** est exécutée.

- N’utilisez pas **longjmp** pour transférer le contrôle en dehors d’une routine de gestion de l’interruption, sauf si l’interruption soit provoquée par une exception à virgule flottante. Dans ce cas, il peut retourner un programme à partir d’un gestionnaire d’interruption via **longjmp** si elle réinitialise tout d’abord le package mathématique à virgule flottante en appelant **_fpreset**.

     **Remarque** soyez prudent lorsque vous utilisez **setjmp** et **longjmp** dans les programmes C++. Étant donné que ces fonctions ne prennent pas en charge la sémantique d’objet C++, il est préférable d’utiliser le mécanisme de gestion des exceptions C++.

Pour plus d’informations, consultez [Utilisation de setjmp et longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_fpreset](fpreset.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)<br/>
