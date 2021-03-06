---
description: 'En savoir plus sur : __getmainargs, __wgetmainargs'
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
api_name:
- __wgetmainargs
- __getmainargs
api_location:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 6f06f83a72d037df6a0973b24ac92ecade6c21eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181746"
---
# <a name="__getmainargs-__wgetmainargs"></a>__getmainargs, __wgetmainargs

Appelle l’analyse de ligne de commande et recopie les arguments de `main()` dans les pointeurs transmis.

## <a name="syntax"></a>Syntaxe

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char **_ _Env,
   int _DoWildCard,
_startupinfo _ _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t **__Env,
   int _DoWildCard,
   _startupinfo _ _StartInfo)
```

#### <a name="parameters"></a>Paramètres

`_Argc`<br/>
Entier qui contient le nombre d’arguments qui se suivent dans `argv`. Le paramètre `argc` est toujours supérieur ou égal à 1.

`_Argv`<br/>
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé, argv [1] est le premier argument de ligne de commande, et ainsi de suite, jusqu’à argv [argc], qui est toujours **null**. Le premier argument de ligne de commande est toujours `argv[1]` et le dernier `argv[argc - 1]`.

`_Env`<br/>
Tableau de chaînes représentant les variables définies dans l’environnement de l’utilisateur. Ce tableau se termine par une entrée **null** .

`_DoWildCard`<br/>
Entier qui, avec la valeur 1, développe les caractères génériques dans les arguments de ligne de commande, ou qui, avec la valeur 0, n’a aucun effet.

`_StartInfo`<br/>
Autres informations à transmettre à la DLL CRT.

## <a name="return-value"></a>Valeur renvoyée

0 en cas de réussite ; valeur négative en cas d’échec.

## <a name="remarks"></a>Notes

Utilisez `__getmainargs` sur les plateformes à caractères non larges et `__wgetmainargs` sur les plateformes à caractères larges (Unicode).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|
