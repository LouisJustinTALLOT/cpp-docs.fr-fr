---
description: 'En savoir plus sur les éléments suivants : _acmdln, _tcmdln _wcmdln'
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
api_name:
- _wcmdln
- _acmdln
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
ms.openlocfilehash: cc47e6e48e408ebd0a4edc02048d6c40ae638ecd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242689"
---
# <a name="_acmdln-_tcmdln-_wcmdln"></a>_acmdln, _tcmdln, _wcmdln

Variable globale CRT interne. Ligne de commande.

## <a name="syntax"></a>Syntaxe

```
char * _acmdln;
wchar_t * _wcmdln;

#ifdef WPRFLAG
   #define _tcmdln _wcmdln
#else
   #define _tcmdln _acmdln
```

## <a name="remarks"></a>Notes

Ces variables internes CRT stockent la ligne de commande entière. Si elles sont exposées dans les symboles exportées pour le CRT, elles ne sont pas destinées pour autant à être utilisées dans votre code. `_acmdln` stocke les données sous forme de chaîne de caractères. `_wcmdln` stocke les données sous forme de chaîne de caractères larges. `_tcmdln` peut être défini comme `_acmdln` ou `_wcmdln`, selon le cas.

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)
