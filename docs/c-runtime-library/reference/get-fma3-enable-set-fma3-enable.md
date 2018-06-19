---
title: _get_FMA3_enable, _set_FMA3_enable | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _get_FMA3_enable
- _set_FMA3_enable
ms.assetid: 4c1dc4bc-e86b-451b-9211-5a2ba6c98ee4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e9f3058f4b8ebc59ba58460ba122cab063a5059
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399194"
---
# <a name="getfma3enable-setfma3enable"></a>_get_FMA3_enable, _set_FMA3_enable

Obtient ou définit un indicateur qui spécifie si les fonctions de bibliothèque à virgule flottante mathématiques transcendantes utilisent des instructions FMA3 dans le code compilé pour X64 plateformes.

## <a name="syntax"></a>Syntaxe

```C
int _set_FMA3_enable(int flag);
int _get_FMA3_enable();
```

### <a name="parameters"></a>Paramètres

*flag*<br/>
La valeur 1 pour activer les implémentations des fonctions transcendantes mathématiques à virgule flottante de bibliothèque sur X64 FMA3 des plateformes, ou 0 pour utiliser les implémentations qui n’utilisent pas les instructions FMA3.

## <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si les implémentations FMA3 des fonctions transcendantes mathématiques à virgule flottante de bibliothèque sont activées. Sinon, zéro.

## <a name="remarks"></a>Notes

Utilisez le **_set_FMA3_enable** fonction pour activer ou désactiver l’utilisation des instructions FMA3 dans les fonctions à virgule flottante transcendantes mathématiques dans la bibliothèque CRT. La valeur de retour reflète l’implémentation en cours d’utilisation après la modification. Si l’UC ne prend pas en charge les instructions FMA3, cette fonction ne peut pas les activer dans la bibliothèque et la valeur de retour est égale à zéro. Utilisez **_get_FMA3_enable** pour obtenir l’état actuel de la bibliothèque. Par défaut, sur X64 plates-formes, le code de démarrage du CRT détecte si le processeur prend en charge les instructions de FMA3 et Active ou désactive les implémentations FMA3 dans la bibliothèque.

Étant donné que les implémentations FMA3 utilisent différents algorithmes, varient légèrement selon le résultat des calculs peut être observable lorsque les implémentations FMA3 sont activées ou désactivées, ou entre les ordinateurs qui ou ne prennent pas en charge FMA3. Pour plus d’informations, consultez [problèmes de migration à virgule flottante](../../porting/floating-point-migration-issues.md).

## <a name="requirements"></a>Spécifications

Le **_set_FMA3_enable** et **_get_FMA3_enable** fonctions sont disponibles uniquement dans le X64 les versions de la bibliothèque CRT.

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_FMA3_enable**, **_get_FMA3_enable**| C : \<math.h><br />C++ : \<cmath > ou \<math.h >|

Le **_set_FMA3_enable** et **_get_FMA3_enable** fonctions sont spécifiques de Microsoft. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge à virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Problèmes de migration de virgule flottante](../../porting/floating-point-migration-issues.md)<br/>
