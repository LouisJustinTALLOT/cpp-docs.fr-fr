---
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
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
ms.openlocfilehash: f4cacb512cb9b5bb6ea22f4dc4014ac2a2eeebe6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747019"
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln, _tcmdln, _wcmdln

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

## <a name="remarks"></a>Remarques

Ces variables internes CRT stockent la ligne de commande entière. Si elles sont exposées dans les symboles exportées pour le CRT, elles ne sont pas destinées pour autant à être utilisées dans votre code. `_acmdln` stocke les données sous forme de chaîne de caractères. `_wcmdln` stocke les données sous forme de chaîne de caractères larges. `_tcmdln` peut être défini comme `_acmdln` ou `_wcmdln`, selon le cas.

## <a name="see-also"></a>Voir aussi

[Variables globales](../c-runtime-library/global-variables.md)
