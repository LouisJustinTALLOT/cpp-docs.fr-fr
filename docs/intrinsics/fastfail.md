---
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: 34198409c6a57eb494bfe819b367b71405a84e64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222194"
---
# <a name="__fastfail"></a>__fastfail

**Section spécifique à Microsoft**

Arrête immédiatement le processus appelant avec une surcharge minimale.

## <a name="syntax"></a>Syntaxe

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>Paramètres

*code*\
dans Constante `FAST_FAIL_<description>` symbolique de Winnt. h ou WDM. h qui indique la raison de l’arrêt du processus.

## <a name="return-value"></a>Valeur de retour

Le `__fastfail` intrinsèque ne retourne pas.

## <a name="remarks"></a>Notes

L' `__fastfail` intrinsèque fournit un mécanisme pour une demande de *basculement rapide* , ce qui permet à un processus potentiellement endommagé de demander un arrêt immédiat du processus. Les défaillances critiques qui ont peut-être endommagé l'état du programme et la pile au-delà de toute récupération ne peuvent pas être gérées par la fonctionnalité de gestion des exceptions ordinaire. Utilisez `__fastfail` pour arrêter le processus à l'aide d'une surcharge minimale.

En interne, `__fastfail` est implémentée à l'aide de plusieurs mécanismes spécifiques à l'architecture :

|Architecture|Instruction|Emplacement de l’argument de code|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|`ecx`|
|X64|int 0x29|`rcx`|
|ARM|Opcode 0xDEFB|`r0`|
|ARM64|Opcode 0xF003|`x0`|

Une demande de basculement rapide est autonome et son exécution ne nécessite généralement que deux instructions. Après l’exécution d’une demande de basculement rapide, le noyau prend l’action appropriée. Dans le code en mode utilisateur, il n'existe aucune dépendance de mémoire au-delà du pointeur d'instruction proprement dit quand un événement de basculement rapide est déclenché. Cela optimise sa fiabilité, même en cas d’altération importante de la mémoire.

L' `code` argument, l’une `FAST_FAIL_<description>` des constantes symboliques de Winnt. h ou WDM. h, décrit le type de condition d’échec. Il est intégré aux rapports d’échec d’une manière spécifique à l’environnement.

Les demandes de basculement rapide en mode utilisateur apparaissent en tant qu’exception non continuable de seconde chance avec code d’exception 0xC0000409 et avec au moins un paramètre d’exception. Le premier paramètre de l'exception est la valeur `code`. Ce code d’exception indique au Rapport d’erreurs Windows (WER) et à l’infrastructure de débogage que le processus est endommagé, et que des actions minimales en cours de traitement doivent être effectuées en réponse à l’échec. Les demandes de basculement rapide en mode noyau sont implémentées à l'aide d'un code de vérification d'erreur dédié, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). Dans les deux cas, aucun gestionnaire d'exceptions n'est appelé car le programme est censé être dans un état endommagé. Si un débogueur est présent, il a la possibilité d’examiner l’état du programme avant son arrêt.

La prise en charge du mécanisme de basculement rapide natif est apparue dans Windows 8. Les systèmes d’exploitation Windows qui ne prennent pas en charge l’instruction de basculement rapide en mode natif traitent généralement une demande de basculement rapide en cas de violation d’accès ou de `UNEXPECTED_KERNEL_MODE_TRAP` vérification de bogue. Dans ces cas-là, le programme est tout de même arrêté, mais pas nécessairement au rapidement.

`__fastfail` est uniquement disponible en tant qu'intrinsèque.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
