---
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 6e2bf21f2ac50d3486af56f9581ff6c8d0e0c309
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523336"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs

Appelle l’analyse de ligne de commande et recopie les arguments de `main()` dans les pointeurs transmis.

## <a name="syntax"></a>Syntaxe

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char *** _Env,
   int _DoWildCard,
_startupinfo * _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t ***_Env,
   int _DoWildCard,
   _startupinfo * _StartInfo)
```

#### <a name="parameters"></a>Paramètres

`_Argc`<br/>
Entier qui contient le nombre d’arguments qui se suivent dans `argv`. Le paramètre `argc` est toujours supérieur ou égal à 1.

`_Argv`<br/>
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par convention, `argv[0]` est la commande avec laquelle le programme est appelé, argv[1] est le premier argument de ligne de commande, et ainsi de suite, jusqu’à argv[argc], qui est toujours **NULL**. Le premier argument de ligne de commande est toujours `argv[1]` et le dernier `argv[argc - 1]`.

`_Env`<br/>
Tableau de chaînes représentant les variables définies dans l’environnement de l’utilisateur. Ce tableau se termine par une entrée **NULL**.

`_DoWildCard`<br/>
Entier qui, avec la valeur 1, développe les caractères génériques dans les arguments de ligne de commande, ou qui, avec la valeur 0, n’a aucun effet.

`_StartInfo`<br/>
Autres informations à transmettre à la DLL CRT.

## <a name="return-value"></a>Valeur de retour

0 en cas de réussite ; valeur négative en cas d’échec.

## <a name="remarks"></a>Notes

Utilisez `__getmainargs` sur les plateformes à caractères non larges et `__wgetmainargs` sur les plateformes à caractères larges (Unicode).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|