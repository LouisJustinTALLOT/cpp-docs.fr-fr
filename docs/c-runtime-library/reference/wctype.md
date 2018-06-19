---
title: wctype | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wctype
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
- wctype
dev_langs:
- C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bb5003db02ed27c2906ebc3619313489e40e5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411898"
---
# <a name="wctype"></a>wctype

Détermine une règle de classification pour les codes à caractères larges.

## <a name="syntax"></a>Syntaxe

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Paramètres

*propriété*<br/>
Chaîne de propriété.

## <a name="return-value"></a>Valeur de retour

Si le **LC_CTYPE** catégorie de paramètres régionaux actuels ne définit pas une règle de classification dont le nom correspond à la chaîne de la propriété *propriété*, la fonction retourne zéro. Sinon, elle retourne une valeur différente de zéro qui peut être utilisée comme deuxième argument dans un appel ultérieur à [towctrans](towctrans.md).

## <a name="remarks"></a>Notes

La fonction détermine une règle de classification pour les codes à caractères larges. Les paires d’appels suivantes présentent le même comportement dans tous les paramètres régionaux (mais une implémentation peut définir des règles de classification supplémentaires même dans les paramètres régionaux « C ») :

|Fonction|Identique à|
|--------------|-------------|
|iswalnum(c)|iswctype (c, wctype ("à" alnum ""))|
|iswalpha(c)|iswctype (c, wctype (« alpha »))|
|iswcntrl(c)|iswctype (c, wctype (« contrôle »))|
|iswdigit(c)|iswctype (c, wctype (« chiffres »))|
|iswgraph(c)|iswctype (c, wctype (« graphique »))|
|iswlower(c)|iswctype (c, wctype (« inférieur »))|
|iswprint(c)|iswctype (c, wctype (« print »))|
|iswpunct(c)|iswctype (c, wctype (« punct »))|
|iswspace(c)|iswctype (c, wctype (« espace »))|
|iswupper(c)|iswctype (c, wctype (« supérieur »))|
|iswxdigit(c)|iswctype (c, wctype (« xdigit »))|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
