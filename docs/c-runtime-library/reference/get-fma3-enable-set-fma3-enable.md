---
title: _get_FMA3_enable, _set_FMA3_enable
ms.date: 04/05/2018
apiname:
- _get_FMA3_enable
- _set_FMA3_enable
apilocation:
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
- math/_get_FMA3_enable
- math/_set_FMA3_enable
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
ms.openlocfilehash: 19eabc3b5a11246d5b0056bdafbb169e2a7de9f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544363"
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable, _set_FMA3_enable

Obtient ou définit un indicateur qui spécifie si les fonctions de bibliothèque à virgule flottante mathématiques transcendant utilisent des instructions FMA3 dans le code compilé pour X64 plateformes.

## <a name="syntax"></a>Syntaxe

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Paramètres

*flag*<br/>
La valeur 1 pour activer les implémentations FMA3 des fonctions de bibliothèque à virgule flottante transcendant mathématiques sur X64 plateformes, ou 0 pour utiliser les implémentations qui n’utilisent pas d’instructions FMA3.

## <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si les implémentations FMA3 des fonctions de bibliothèque à virgule flottante transcendant mathématiques sont activées. Sinon, zéro.

## <a name="remarks"></a>Notes

Utiliser le **_set_FMA3_enable** (fonction) pour activer ou désactiver l’utilisation des instructions FMA3 dans les fonctions à virgule flottante transcendant mathématiques dans la bibliothèque CRT. La valeur de retour reflète l’implémentation en cours d’utilisation après la modification. Si le processeur ne prend pas en charge les instructions FMA3, cette fonction ne peut pas les activer dans la bibliothèque, et la valeur de retour est égale à zéro. Utilisez **_get_FMA3_enable** pour obtenir l’état actuel de la bibliothèque. Par défaut, sur X64 plates-formes, le code de démarrage du CRT détecte si le processeur prend en charge des instructions FMA3 et Active ou désactive les implémentations FMA3 dans la bibliothèque.

Étant donné que les implémentations FMA3 utilisent différents algorithmes, présentent de légères différences dans le résultat des calculs peuvent être observable lorsque les implémentations FMA3 sont activées ou désactivées, ou entre les ordinateurs qui ou ne prennent pas en charge FMA3. Pour plus d’informations, consultez [les problèmes de migration de virgule flottante](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Configuration requise

Le **_set_FMA3_enable** et **_get_FMA3_enable** fonctions sont uniquement disponibles dans le X64 versions du CRT.

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C : \<math.h><br />C++ : \<cmath > ou \<math.h >|

Le **_set_FMA3_enable** et **_get_FMA3_enable** fonctions sont propres à Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge à virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Problèmes de migration de virgule flottante](../../porting/floating-point-migration-issues.md)<br/>
