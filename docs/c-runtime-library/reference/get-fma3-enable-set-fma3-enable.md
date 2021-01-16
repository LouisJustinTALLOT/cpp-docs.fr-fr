---
description: 'En savoir plus sur : _get_FMA3_enable, _set_FMA3_enable'
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 1/14/2021
api_name:
- _get_FMA3_enable
- _set_FMA3_enable
api_location:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 48c70185b73c2f7bb05677fdb550c2c0535d8992
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243084"
---
# <a name="_get_fma3_enable-_set_fma3_enable"></a>_get_FMA3_enable, _set_FMA3_enable

Obtient ou définit un indicateur qui spécifie si les fonctions de bibliothèque à virgule flottante transcendant utilisent des instructions FMA3 dans le code compilé pour les plateformes x64.

## <a name="syntax"></a>Syntaxe

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Paramètres

*flag*<br/>
Affectez la valeur 1 pour activer les implémentations FMA3 des fonctions de la bibliothèque à virgule flottante transcendant mathématique sur les plateformes x64, ou sur 0 pour utiliser les implémentations qui n’utilisent pas d’instructions FMA3.

## <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si les implémentations FMA3 des fonctions de bibliothèque à virgule flottante transcendant sont activées. Sinon, zéro.

## <a name="remarks"></a>Remarques

Utilisez la fonction **_set_FMA3_enable** pour activer ou désactiver l’utilisation des instructions FMA3 dans les fonctions à virgule flottante transcendant mathématiques de la bibliothèque CRT. La valeur de retour reflète l’implémentation en cours d’utilisation après la modification. Si le processeur ne prend pas en charge les instructions FMA3, cette fonction ne peut pas les activer dans la bibliothèque, et la valeur de retour est zéro. Utilisez **_get_FMA3_enable** pour récupérer l’état actuel de la bibliothèque. Par défaut, sur les plateformes x64, le code de démarrage du CRT détecte si le processeur prend en charge les instructions FMA3, et active ou désactive les implémentations FMA3 dans la bibliothèque.

Étant donné que les implémentations de FMA3 utilisent des algorithmes différents, de légères différences dans le résultat des calculs peuvent être observables lorsque les implémentations de FMA3 sont activées ou désactivées, ou entre des ordinateurs qui ne prennent pas en charge FMA3. Pour plus d’informations, consultez [problèmes de migration à virgule flottante](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Configuration requise

Les fonctions **_set_FMA3_enable** et **_get_FMA3_enable** sont uniquement disponibles dans les versions x64 du CRT.

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| Secteur \<math.h><br />C++ : \<cmath> ou \<math.h>|

Les fonctions **_set_FMA3_enable** et **_get_FMA3_enable** sont spécifiques à Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Problèmes de migration de virgule flottante](../../porting/floating-point-migration-issues.md)<br/>
