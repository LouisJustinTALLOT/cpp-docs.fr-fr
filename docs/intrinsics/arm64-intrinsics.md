---
title: Intrinsèques ARM64
description: Une liste des intrinsèques ARM64 prises en charge par le compilateur Microsoft C.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 196518439445824ddf5a7a841b30eb816251ba60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368212"
---
# <a name="arm64-intrinsics"></a>Intrinsèques ARM64

Le compilateur Microsoft CMD (MSVC) met les intrinsèques suivants disponibles sur l’architecture ARM64. Pour plus d’informations sur ARM, consultez les sections Architecture et Software Development Tools du site [Web d’ARM Developer Documentation.](https://developer.arm.com/docs)

## <a name="neon"></a><a name="top"></a>Néon

Les extensions d’instructions vectorielles NEON pour ARM64 fournissent des capacités de données multiples (SIMD) à instruction unique. Ils ressemblent à ceux des ensembles d’instructions vectorielles MMX et SSE qui sont communs aux processeurs d’architecture x86 et x64.

Les intrinsèques neON sont prises en charge, comme le fournit le fichier d’en-tête *arm64_neon.h*. Le support MSVC pour NEON intrinsèque ressemble à celui du compilateur ARM64, qui est documenté dans la [référence intrinsèque ARM NEON](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) sur le site Web d’ARM Infocenter.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>Liste intrinsèque spécifique ARM64

|Nom de fonction|Instruction|Prototype de fonction|
|-------------------|-----------------|------------------------|
|__break|Brk|vide __break (int)|
|__addx18byte||vide __addx18byte (char non signé long et non signé)|
|__addx18word||vide __addx18word (non signé long, court non signé)|
|__addx18dword||vide __addx18dword (non signé long, non signé long)|
|__addx18qword||vide __addx18qword (__int64 non signés longs et non signés)|
|__cas8|CASB|__cas8 de __int8 non signés (_Target volatils __int8 non signés, _Comp non signés __int8, __int8 _Value non signés|
|__cas16|Argent|__cas16 de __int16 non signés (__int16 _Target volatils non signés, _Comp non signés __int16, __int16 _Value non signés|
|__cas32|CAS|__int32 non signés __cas32 (__int32 _Target volatils non signés, _Comp __int32 non signés, _Value __int32 non signés|
|__cas64|CAS|__int64 non signés __cas64 (__int64 _Target volatils non signés, _Comp __int64 non signés, _Value __int64 non signés|
|__casa8|CASAB|__int8 non signés __casa8 (__int8 _Target volatils non signés, _Comp __int8 non signés, __int8 _Value non signés|
|__casa16|CasAH CASAH|__int16 non signés __casa16 (__int16 _Target volatils non signés, _Comp non signés __int16, __int16 non signés _Value)|
|__casa32|Casa|__casa32 de __int32 non signés (_Target volatils __int32 non signés, __int32 _Comp non signés, _Value __int32 non signés|
|__casa64|Casa|__int64 non signés __casa64 (__int64 _Target volatils non signés, _Comp __int64 non signés, __int64 _Value non signés|
|__casl8|CASLB|__int8 non signés __casl8 (__int8 _Target volatils non signés, _Comp __int8 non signés, _Value __int8 non signés|
|__casl16|CASLH|__casl16 de __int16 non signés (__int16 _Target volatils, _Comp non signés __int16, __int16 non signés _Value)|
|__casl32|CASL|__int32 non signés __casl32 (__int32 _Target volatils non signés, _Comp __int32 non signés, __int32 non signés __int32 _Value)|
|__casl64|CASL|__int64 non signés __casl64 (__int64 _Target volatils non signés, _Comp __int64 non signés, __int64 non signés _Value)|
|__casal8|CASALB (CASALB)|__int8 non signés __casal8 (_Target volatils __int8 non signés, _Comp __int8 non signés, _Value __int8 non signés|
|__casal16|CASALH CASALH|__int16 non signés __casal16 (__int16 _Target volatils non signés, _Comp non signés __int16, __int16 _Value non signés|
|__casal32|Casal|__casal32 de __int32 non signés (__int32 _Target volatils non signés, _Comp __int32 non signés _Comp, __int32 _Value non signés)|
|__casal64|Casal|__int64 non signés __casal64 (_Target volatils __int64 non signés, _Comp __int64 non signés, _Value __int64 non signés|
|__crc32b|CRC32B|__int32 non signés __crc32b (__int32 non signé, __int32 non signés)|
|__crc32h|CRC32H|__int32 non signés __crc32h (__int32 non signées, __int32 non signées)|
|__crc32w|CRC32W|__int32 non signés __crc32w (__int32 non signées, __int32 non signés)|
|__crc32d|CRC32X|__int32 non signés __crc32d (__int32 non signées, __int64 non signées)|
|__crc32cb|CRC32CB|__crc32cb non signés __int32 (__int32 non signés, __int32 non signés)|
|__crc32ch|CRC32CH|__int32 non signés __crc32ch (__int32 non signées, __int32 non signées)|
|__crc32cw|CRC32CW|__int32 non signés __crc32cw (__int32 non signée, __int32 non signées)|
|__crc32cd|CRC32CX|__int32 non signés __crc32cd (__int32 non signée, __int64 non signés)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> Insère une opération de barrière de mémoire dans le flux d'instructions. Le paramètre `_Type` spécifie le type de restriction que la barrière applique.<br /><br /> Pour plus d’informations sur les types de restrictions qui peuvent être appliquées, voir [restrictions barrière mémoire](#BarrierRestrictions).|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> Insère une opération de barrière de mémoire dans le flux d'instructions. Le paramètre `_Type` spécifie le type de restriction que la barrière applique.<br /><br /> Pour plus d’informations sur les types de restrictions qui peuvent être appliquées, voir [restrictions barrière mémoire](#BarrierRestrictions).|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> Insère une opération de barrière de mémoire dans le flux d'instructions. Le paramètre `_Type` spécifie le type de restriction que la barrière applique.<br /><br /> Pour plus d’informations sur les types de restrictions qui peuvent être appliquées, voir [restrictions barrière mémoire](#BarrierRestrictions).|
|__getReg||__int64 non signé __getReg (int)|
|__getRegFp||double __getRegFp (int)|
|__getCallerReg||__int64 non signé __getCallerReg (int)|
|__getCallerRegFp||double __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|Mission|int __hlt (int non signé, ...)|
|__incx18byte||vide __incx18byte (non signé longtemps)|
|__incx18word||vide __incx18word (non signé longtemps)|
|__incx18dword||vide __incx18dword (non signé longtemps)|
|__incx18qword||vide __incx18qword (non signé longtemps)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \__int16 ) \*<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatile \__int32 ) \*<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \__int64 ) \*<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 ) \*<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_store16||__iso_volatile_store16 vides (_int16 \_ \*volatils , \__int16)<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_store32||__iso_volatile_store32 vide (_int32 \_volatil \*, \__int32)<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_store64||__iso_volatile_store64 vides (_int64 \_ \*volatils , \__int64)<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__iso_volatile_store8||__iso_volatile_store8 vides (_int8 \_ \*volatils , \__int8)<br /><br /> Pour plus d’informations, voir [__iso_volatile_load/magasin intrinsèques](#IsoVolatileLoadStore).|
|__ldar8|LDARB (LDARB)|__ldar8 de __int8 non signé (__int8 _Target volatils non signés)|
|__ldar16|LDARH LDARH|__int16 non signés __ldar16 (_Target volatils __int16 non signés)|
|__ldar32|LDAR LDAR|__int32 non signés __ldar32 (__int32 volatils non signés _Target)|
|__ldar64|LDAR LDAR|__int64 non signés __ldar64 (__int64 volatils non signés _Target)|
|__ldapr8|LDAPRB|__ldapr8 de __int8 non signé (__int8 _Target volatils non signés)|
|__ldapr16|LDAPRH (LDAPRH)|__int16 non signés __ldapr16 (__int16 volatils non signés _Target)|
|__ldapr32|LDAPR (LDAPR)|__int32 non signés __ldapr32 (__int32 volatils non signés _Target)|
|__ldapr64|LDAPR (LDAPR)|__ldapr64 de __int64 non signés (__int64 _Target volatils non signés)|
|__mulh||\__int64 __mulh (\__int64, \__int64)|
|__prefetch|PRFM (EN)|vide __cdecl \__prefetch (const void \*)<br /><br /> Fournit `PRFM` un indice de mémoire `PLDL1KEEP` avec l’opération de préfède au système que la mémoire à ou près de l’adresse spécifiée peut être consultée bientôt. Certains systèmes peuvent choisir d’effectuer une optimisation selon ce modèle d’accès mémoire, pour augmenter les performances d’exécution. Cependant, du point de vue du langage C++, la fonction n'a aucun effet observable et peut ne rien faire du tout.|
|__prefetch2|PRFM (EN)|vide __cdecl \__prefetch (const void \*, uint8_t prfop)<br /><br /> Fournit `PRFM` un indice de mémoire avec l’opération préfetch fournie au système que la mémoire à ou près de l’adresse spécifiée peut être consultée bientôt. Certains systèmes peuvent choisir d’effectuer une optimisation selon ce modèle d’accès mémoire, pour augmenter les performances d’exécution. Cependant, du point de vue du langage C++, la fonction n'a aucun effet observable et peut ne rien faire du tout.|
|__readx18byte||char non signé __readx18byte (non signé longtemps)|
|__readx18word||__readx18word court non signé (non signé depuis longtemps)|
|__readx18dword||longtemps non signé __readx18dword (non signés longtemps)|
|__readx18qword||__int64 non signé __readx18qword (non signés longtemps)|
|__setReg||vide __setReg (int, __int64 non signé)|
|__setRegFp||vide __setRegFp (int, double)|
|__setCallerReg||vide __setCallerReg (int, __int64 non signé)|
|__setCallerRegFp||vide __setCallerRegFp (int, double)|
|__sev|SEV|void __sev(void)|
|__static_assert||vide __static_assert (int, const \*char )|
|__stlr8|STLRB (en anglais)|__stlr8 nul (__int8 volatil non signé _Target, _Value __int8 non signés|
|__stlr16|STLRH (STLRH)|__stlr16 nul (__int16 _Target volatil __int16 _Value, __int16 non signés)|
|__stlr32|STLR (STLR)|__stlr32 nul (__int32 volatil non signé _Target, _Value __int32 non signés|
|__stlr64|STLR (STLR)|__stlr64 nul (__int64 volatil non signé _Target, _Value __int64 non signés|
|__swp8|SWPB SWPB|__swp8 de __int8 non signé (__int8 _Target volatils et non signés __int8 _Value)|
|__swp16|SWPH|__int16 non signés __swp16 (__int16 _Target volatils non signés, __int16 _Value)|
|__swp32|Swp|__swp32 de __int32 non signés (__int32 _Target volatils et non signés __int32 _Value)|
|__swp64|Swp|__int64 non signés __swp64 (__int64 _Target volatils non signés, __int64 non signés _Value)|
|__swpa8|SWPAB (SWPAB)|__int8 non signés __swpa8 (__int8 volatils non signés, _Target __int8 _Value)|
|__swpa16|SWPAH (SWPAH)|__int16 non signés __swpa16 (_Target volatils __int16 non signés, _Value non signés __int16)|
|__swpa32|SWPA (SWPA)|__int32 non signés __swpa32 (__int32 _Target volatils et non signés __int32 _Value)|
|__swpa64|SWPA (SWPA)|__int64 non signés __swpa64 (_Target volatils __int64 non signés, __int64 non signés _Value)|
|__swpl8|SWPLB (en anglais)|__int8 non signés __swpl8 (__int8 volatils non signés, _Target, _Value __int8 non signés|
|__swpl16|SWPLH (SWPLH)|__int16 non signés __swpl16 (__int16 volatils non signés, _Target _Value __int16 non signés)|
|__swpl32|SWPL (SWPL)|__int32 non signés __swpl32 (__int32 _Target volatils non signés, __int32 _Value non signés|
|__swpl64|SWPL (SWPL)|__int64 non signés __swpl64 (__int64 _Target volatils non signés, __int64 _Value non signés|
|__swpal8|SWPALB (SWPALB)|__int8 non signés __swpal8 (_Target volatils __int8 non signés, __int8 non signés _Value)|
|__swpal16|SWPALH SWPALH|__int16 non signés __swpal16 (__int16 _Target volatils et __int16 _Value non signés)|
|__swpal32|SWPAL SWPAL|__int32 non signés __swpal32 (__int32 _Target volatils et non signés __int32 _Value)|
|__swpal64|SWPAL SWPAL|__int64 non signés __swpal64 (__int64 _Target volatils non signés, __int64 non signés _Value)|
|__sys|Sys|int __sys non signé (int, __int64)|
|__svc|SVC|int __svc non signé (int non signé, ...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||vide __writex18byte (char non signé long et non signé)|
|__writex18word||vide __writex18word (non signé long, court non signé)|
|__writex18dword||vide __writex18dword (non signé long, non signé long)|
|__writex18qword||__writex18qword vide (__int64 non signés longs et non signés)|
|__umulh||\__int64 non signés __umulh \_(_int64 non signés, \__int64 non signés)|
|_CopyDoubleFromInt64||double _CopyDoubleFromInt64 (_int64)\_|
|_CopyFloatFromInt32||flotteur _CopyFloatFromInt32\_(_int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||int _CountLeadingOnes64 non signé \_(_int64 non signé)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||int _CountLeadingSigns64 non signé (_int64)\_|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||int _CountLeadingZeros64 non signé \_(_int64 non signé)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|MSR|vide _WriteStatusReg (int, \__int64)|

[[Retour au sommet](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>Restrictions de barrière de mémoire

Les fonctions `__dmb` intrinsèques (barrière de mémoire des `__dsb` `__isb` données), (barrière de synchronisation des données) et (barrière de synchronisation d’instruction) utilisent les valeurs prédéfinie suivantes pour spécifier la restriction de barrière de mémoire en termes de domaine de partage et le type d’accès qui est affecté par l’opération.

|Valeur de restriction|Description|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Système complet, lectures et écritures.|
|_ARM64_BARRIER_ST|Système complet, écritures uniquement.|
|_ARM64_BARRIER_LD|Système complet, lu seulement.|
|_ARM64_BARRIER_ISH|Interne partageable, lectures et écritures.|
|_ARM64_BARRIER_ISHST|Interne partageable, écritures uniquement.|
|_ARM64_BARRIER_ISHLD|Intérieur sharable, lu seulement.|
|_ARM64_BARRIER_NSH|Non partageable, lectures et écritures.|
|_ARM64_BARRIER_NSHST|Non partageable, écritures uniquement.|
|_ARM64_BARRIER_NSHLD|Non-sharable, lu seulement.|
|_ARM64_BARRIER_OSH|Externe partageable, lectures et écritures.|
|_ARM64_BARRIER_OSHST|Externe partageable, écritures uniquement.|
|_ARM64_BARRIER_OSHLD|Extérieure sharable, lu seulement.|

Pour `__isb` l’intrinsèque, la seule restriction qui est actuellement valable est _ARM64_BARRIER_SY; toutes les autres valeurs sont réservées par l’architecture.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/magasin intrinsèques

Ces fonctions intrinsèques effectuent explicitement des charges et des magasins qui ne sont pas soumis à des optimisations compilateur.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>Paramètres

*Emplacement*\
L'adresse d'un emplacement mémoire où lire ou dans lequel écrire.

*Valeur*\
La valeur d’écrire à l’emplacement de mémoire spécifié (magasin intrinsèque uniquement).

#### <a name="return-value-load-intrinsics-only"></a>Valeur de retour (charge intrinsèque seulement)

La valeur de l’emplacement de la mémoire qui est spécifiée par *emplacement*.

#### <a name="remarks"></a>Notes

Vous pouvez `__iso_volatile_load8/16/32/64` utiliser `__iso_volatile_store8/16/32/64` les et les intrinsèques pour effectuer explicitement des accès à la mémoire qui ne sont pas soumis à des optimisations compilateur. Le compilateur ne peut pas enlever, synthétiser ou modifier l’ordre relatif de ces opérations. Cependant, il ne génère pas de barrières implicites de mémoire matérielle. Par conséquent, le matériel peut toujours réorganiser les accès mémoire observables entre plusieurs threads. Plus précisément, ces intrinsèques sont équivalents aux expressions suivantes telles qu’compilées sous **/volatile:iso**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Notez que les intrinsèques prennent des pointeurs volatiles de façon à pouvoir traiter des variables volatiles. Cependant, il n’y a aucune exigence ou recommandation d’utiliser des pointeurs volatils comme arguments. La sémantique de ces opérations est exactement la même si un type régulier et non volatil est utilisé.

Pour plus d’informations sur l’argument **/volatile:iso** commande-ligne, voir [/ volatile (interprétation volatile mot clé)](../build/reference/volatile-volatile-keyword-interpretation.md).

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM64 support pour les intrinsèques d’autres architectures

Le tableau suivant énumère les intrinsèques d’autres architectures qui sont prises en charge sur les plates-formes ARM64. Lorsque le comportement d’un intrinsèque sur ARM64 diffère de son comportement sur d’autres architectures matérielles, des détails supplémentaires sont notés.

|Nom de fonction|Prototype de fonction|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|vide __code_seg (const \*char )|
|__debugbreak|\_vide __cdecl _debugbreak (vide)|
|__fastfail|__declspec (noreturn) vide \__fastfail (int non signé)|
|__nop|void __nop(void)|
|__yield|vide __yield (vide) **Note:** Sur les plates-formes ARM64, cette fonction génère l’instruction YIELD. Cette instruction indique que le thread effectue une tâche qui peut être temporairement suspendue à l’exécution, par exemple, un spinlock, sans nuire au programme. Il permet au processeur d’exécuter d’autres tâches pendant les cycles d’exécution qui seraient autrement gaspillés.|
|_AddressOfReturnAddress|_AddressOfReturnAddress \* vide (vide)|
|_BitScanForward|char non signé _BitScanForward (_Index non \* signé, _Mask longtemps non signé)|
|_BitScanForward64|char _BitScanForward64 non signé \* (_Index non signé, __int64 non signé _Mask)|
|_BitScanReverse|char non signé _BitScanReverse (_Index non signé, \* _Mask longtemps non signé)|
|_BitScanReverse64|_BitScanReverse64 d’omble non signé \* (_Index non signé, __int64 non signé _Mask)|
|_bittest|char non signé _bittest (long const \*, long)|
|_bittest64|char non signé _bittest64 (__int64 const \*, __int64)|
|_bittestandcomplement|char non signé _bittestandcomplement (long, \*long)|
|_bittestandcomplement64|char _bittestandcomplement64 non signé (__int64 \*, __int64)|
|_bittestandreset|char non signé _bittestandreset (long, \*long)|
|_bittestandreset64|char _bittestandreset64 non signé (__int64 \*, __int64)|
|_bittestandset|char non signé _bittestandset (long, \*long)|
|_bittestandset64|char _bittestandset64 non signé (__int64 \*, __int64)|
|_byteswap_uint64|_int64 \_non signés __int64 _byteswap_uint64 _cdecl \_(_int64 non signés)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|vide __cdecl _disable (vide) **Note:** Sur les plates-formes ARM64, `MSR DAIFCLR,#2`cette fonction génère l’instruction ; il n’est disponible qu’en tant qu’intrinsèque.|
|_enable|vide __cdecl _enable (vide) **Note:** Sur les plates-formes ARM64, `MSR DAIFSET,#2`cette fonction génère l’instruction ; il n’est disponible qu’en tant qu’intrinsèque.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|vide \* _ReturnAddress (vide)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|__int64 non signé \__rotl64 _cdecl \_(_int64 non signée _Value, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|__int64 non signé \__cdecl _rotr64 \_(_int64 non signé _Value, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Retour au sommet](#top)]

## <a name="interlocked-intrinsics"></a>Intrinsèques imbriqués

Les intrinsèques à blocage sont un ensemble d'intrinsèques qui sont utilisées pour effectuer des opérations de lecture-modification-écriture atomiques. Certaines d'entre elles sont communes à toutes les plateformes. Ils sont répertoriés séparément ici parce qu’il y en a un grand nombre. Parce que leurs définitions sont pour la plupart redondantes, il est plus facile d’y penser en termes généraux. Leurs noms peuvent être utilisés pour en dériver les comportements exacts.

Le tableau suivant résume le support ARM64 des intrinsèques imbriqués non bittestés. Chaque cellule du tableau correspond à un nom qui est constitué en ajoutant le nom de l'opération dans la cellule la plus à gauche de la ligne et le nom de type dans la cellule la plus en haut de la colonne à `_Interlocked`. Par exemple, la cellule à `Xor` l’intersection de la rangée et de la `8` colonne correspond et `_InterlockedXor8` est entièrement prise en charge. La plupart des fonctions prises en charge peuvent comporter ces suffixes facultatifs : `_acq`, `_rel` et `_nf`. Le suffixe `_acq` indique une sémantique correspondant à « acquérir » et le suffixe `_rel` indique une sémantique correspondant à « libérer ». Le `_nf` suffixe ou « sans clôture » est unique à ARM et ARM64 et est discuté dans la section suivante.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Ajouter|None|None|Complète|Complète|None|None|
|and|Complète|Complète|Complète|Complète|None|None|
|CompareExchange|Complète|Complète|Complète|Complète|Complète|Complète|
|Décrémentation|None|Complète|Complète|Complète|None|None|
|Exchange|Complète|Complète|Complète|Complète|None|Complète|
|ExchangeAdd|Complète|Complète|Complète|Complète|None|None|
|Incrément|None|Complète|Complète|Complète|None|None|
|ou|Complète|Complète|Complète|Complète|None|None|
|Xor|Complète|Complète|Complète|Complète|None|None|

Clé :

- **Plein**: supports `_acq` `_rel`simples, `_nf` , , et formes.

- **Aucun**: Non pris en charge

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>suffixe _nf (sans clôture)

Le `_nf` suffixe ou « sans clôture » indique que l’opération ne se comporte pas comme `_acq`n’importe quel type de barrière de mémoire, contrairement aux trois autres formes (plaine, , et `_rel`), qui se comportent toutes comme une sorte de barrière. Une utilisation possible `_nf` des formulaires est de maintenir un compteur de statistiques qui est mis à jour par plusieurs threads en même temps, mais dont la valeur n’est pas autrement utilisée pendant l’exécution de plusieurs threads.

### <a name="list-of-interlocked-intrinsics"></a>Liste des intrinsèques imbriqués

|Nom de fonction|Prototype de fonction|
|-------------------|------------------------|
|_InterlockedAdd|long _InterlockedAdd (long _volatile \*, long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 (_int64\_volatil \*, \__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq (_int64\_volatil \*, \__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (_int64\_volatil \*, \__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (_int64\_volatil \*, \__int64)|
|_InterlockedAdd_acq|long _InterlockedAdd_acq (longtemps volatil, \*long)|
|_InterlockedAdd_nf|long _InterlockedAdd_nf (longtemps volatil, \*long)|
|_InterlockedAdd_rel|long _InterlockedAdd_rel (longtemps volatil, \*long)|
|_InterlockedAnd|long _InterlockedAnd (longtemps volatil, \*long)|
|_InterlockedAnd16|_InterlockedAnd16 courte (courte volatile, \*courte)|
|_InterlockedAnd16_acq|_InterlockedAnd16_acq courte (courte volatile, \*courte)|
|_InterlockedAnd16_nf|_InterlockedAnd16_nf courte (courte \*volatile, courte)|
|_InterlockedAnd16_rel|_InterlockedAnd16_rel courte (courte \*volatile, courte)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 (_int64\_volatil \*, \__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq (_int64\_volatil \*, \__int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (_int64\_volatil \*, \__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (_int64\_volatil, \* \__int64)|
|_InterlockedAnd8|char _InterlockedAnd8 (char volatile, \*char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (char volatile, \*char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char volatile, \*char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (char volatile, \*char)|
|_InterlockedAnd_acq|long _InterlockedAnd_acq (longtemps volatil, \*long)|
|_InterlockedAnd_nf|long _InterlockedAnd_nf (longtemps volatil, \*long)|
|_InterlockedAnd_rel|long _InterlockedAnd_rel (longtemps volatil, \*long)|
|_InterlockedCompareExchange|long __cdecl _InterlockedCompareExchange (longtemps volatil, \*long, long)|
|_InterlockedCompareExchange_acq|long _InterlockedCompareExchange_acq (longtemps volatil, \*long, long)|
|_InterlockedCompareExchange_nf|long _InterlockedCompareExchange_nf (longtemps volatil, \*long, long)|
|_InterlockedCompareExchange_rel|long _InterlockedCompareExchange_rel (longtemps volatil, \*long, long)|
|_InterlockedCompareExchange16|_InterlockedCompareExchange16 courte (courte volatile, \*courte, courte)|
|_InterlockedCompareExchange16_acq|_InterlockedCompareExchange16_acq courte (courte \*volatile, courte, courte)|
|_InterlockedCompareExchange16_nf|_InterlockedCompareExchange16_nf courtes (courte volatile, \*courte, courte)|
|_InterlockedCompareExchange16_rel|_InterlockedCompareExchange16_rel courtes (courte volatile, \*courte, courte)|
|_InterlockedCompareExchange64|\___int64 _InterlockedCompareExchange64 (_int64 volatil, \* \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|\___int64 _InterlockedCompareExchange64_acq (_int64 volatil, \* \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|\___int64 _InterlockedCompareExchange64_nf (_int64 volatil \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|\___int64 _InterlockedCompareExchange64_rel (_int64 volatil \*, \__int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char volatile, \*char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char volatile, \*char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (char volatile \*, char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (char volatile, \*char, char)|
|_InterlockedCompareExchangePointer|vide \* _InterlockedCompareExchangePointer (vide \* \*volatile \*, \*vide , vide )|
|_InterlockedCompareExchangePointer_acq|vide \* _InterlockedCompareExchangePointer_acq (vide \* \*volatile \*, \*vide , vide )|
|_InterlockedCompareExchangePointer_nf|vide \* \* _InterlockedCompareExchangePointer_nf (vide volatile \*, \*vide \*, vide )|
|_InterlockedCompareExchangePointer_rel|vide \* \* _InterlockedCompareExchangePointer_rel (vide volatile \*, \*vide \*, vide )|
|_InterlockedCompareExchange128|_InterlockedCompareExchange128 d’omble non signé\_(_int64 _Destination \* volatil, \__int64 \__ExchangeHigh, _int64 _ExchangeLow, \_ \* _int64 _ComparandResult)|
|_InterlockedCompareExchange128_acq|_InterlockedCompareExchange128_acq d’omble non signé\_(_Destination volatil \* _int64, \__ExchangeHigh _int64, \__ExchangeLow _int64, \_ \* _int64 _ComparandResult)|
|_InterlockedCompareExchange128_nf|_InterlockedCompareExchange128_nf d’omble non signé\_(_Destination volatil \* _int64, \__int64 _ExchangeHigh, \__ExchangeLow _int64, \_ \* _ComparandResult _int64)|
|_InterlockedCompareExchange128_rel|_InterlockedCompareExchange128_rel d’omble non signé\_(_int64 \* _Destination volatil, \__ExchangeHigh _int64, \__ExchangeLow _int64, \_ \* _ComparandResult _int64)|
|_InterlockedDecrement|long __cdecl _InterlockedDecrement (longtemps volatil \*)|
|_InterlockedDecrement16|_InterlockedDecrement16 courte (courte volatile \*)|
|_InterlockedDecrement16_acq|_InterlockedDecrement16_acq courte (courte volatile \*)|
|_InterlockedDecrement16_nf|_InterlockedDecrement16_nf courte (courte \*volatile )|
|_InterlockedDecrement16_rel|_InterlockedDecrement16_rel courte (courte volatile \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 volatil) \*|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq (\__int64 volatil) \*|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\__int64 volatil) \*|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 volatil) \*|
|_InterlockedDecrement_acq|long _InterlockedDecrement_acq (longtemps volatil \*)|
|_InterlockedDecrement_nf|long _InterlockedDecrement_nf (longtemps \*volatil )|
|_InterlockedDecrement_rel|long _InterlockedDecrement_rel (longtemps \*volatil )|
|_InterlockedExchange|long __cdecl _InterlockedExchange (long _Target \* volatil, long)|
|_InterlockedExchange_acq|long _InterlockedExchange_acq (long \* _Target volatil, long)|
|_InterlockedExchange_nf|long _InterlockedExchange_nf (long \* _Target volatil, long)|
|_InterlockedExchange_rel|long _InterlockedExchange_rel (long _Target \* volatil, long)|
|_InterlockedExchange16|_InterlockedExchange16 courte (_Target volatile \* courte, courte)|
|_InterlockedExchange16_acq|_InterlockedExchange16_acq courte (_Target volatile \* courte, courte)|
|_InterlockedExchange16_nf|_InterlockedExchange16_nf courte (_Target volatile \* courte, courte)|
|_InterlockedExchange16_rel|_InterlockedExchange16_rel courte (_Target volatile \* courte, courte)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 (_Target\__int64 volatil, \* \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (_int64\__Target volatil, \* \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (_Target\__int64 volatil, \* \__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (_Target\__int64 volatil, \* \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char \* volatile _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char \* volatile _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char volatile \* _Target, char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char \* volatile _Target, char)|
|_InterlockedExchangeAdd|long __cdecl _InterlockedExchangeAdd (longtemps volatil, \*long)|
|_InterlockedExchangeAdd16|_InterlockedExchangeAdd16 courte (courte volatile, \*courte)|
|_InterlockedExchangeAdd16_acq|_InterlockedExchangeAdd16_acq courte (courte volatile, \*courte)|
|_InterlockedExchangeAdd16_nf|_InterlockedExchangeAdd16_nf courte (courte \*volatile, courte)|
|_InterlockedExchangeAdd16_rel|_InterlockedExchangeAdd16_rel courte (courte \*volatile, courte)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (_int64\_volatil, \* \__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq (_int64\_volatil \*, \__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (_int64\_volatil \*, \__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (_int64\_volatil \*, \__int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (char volatile, \*char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (char volatile, \*char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (char \*volatile, char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (char volatile, \*char)|
|_InterlockedExchangeAdd_acq|long _InterlockedExchangeAdd_acq (longtemps volatil, \*long)|
|_InterlockedExchangeAdd_nf|long _InterlockedExchangeAdd_nf (longtemps volatil, \*long)|
|_InterlockedExchangeAdd_rel|long _InterlockedExchangeAdd_rel (longtemps volatil, \*long)|
|_InterlockedExchangePointer|vide \* _InterlockedExchangePointer (vide \* \* volatile _Target, \*vide )|
|_InterlockedExchangePointer_acq|vide \* _InterlockedExchangePointer_acq (vide \* volatile \* _Target, vide \*)|
|_InterlockedExchangePointer_nf|vide \* _InterlockedExchangePointer_nf (vide \* volatile \* _Target, vide \*)|
|_InterlockedExchangePointer_rel|_InterlockedExchangePointer_rel \* vide (vide \* volatile \* _Target, vide \*)|
|_InterlockedIncrement|long __cdecl _InterlockedIncrement (longtemps volatil \*)|
|_InterlockedIncrement16|_InterlockedIncrement16 courte (courte volatile \*)|
|_InterlockedIncrement16_acq|_InterlockedIncrement16_acq courte (courte volatile \*)|
|_InterlockedIncrement16_nf|_InterlockedIncrement16_nf courte (courte \*volatile )|
|_InterlockedIncrement16_rel|_InterlockedIncrement16_rel courte (courte volatile \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\__int64 volatil) \*|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq (\__int64 volatil) \*|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf (\__int64 volatil) \*|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\__int64 volatil) \*|
|_InterlockedIncrement_acq|long _InterlockedIncrement_acq (longtemps volatil \*)|
|_InterlockedIncrement_nf|long _InterlockedIncrement_nf (longtemps \*volatil )|
|_InterlockedIncrement_rel|long _InterlockedIncrement_rel (longtemps volatil \*)|
|_InterlockedOr|long _InterlockedOr (longtemps volatil, \*long)|
|_InterlockedOr16|_InterlockedOr16 courte (courte \*volatile, courte)|
|_InterlockedOr16_acq|_InterlockedOr16_acq courte (courte volatile, \*courte)|
|_InterlockedOr16_nf|_InterlockedOr16_nf courte (courte volatile, \*courte)|
|_InterlockedOr16_rel|_InterlockedOr16_rel courte (courte volatile, \*courte)|
|_InterlockedOr64|__int64 _InterlockedOr64 (_int64\_volatil, \* \__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq (_int64\_volatil \*, \__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (_int64\_volatil \*, \__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (_int64\_volatil \*, \__int64)|
|_InterlockedOr8|char _InterlockedOr8 (char \*volatile, char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char volatile, \*char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char volatile, \*char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel (char volatile, \*char)|
|_InterlockedOr_acq|long _InterlockedOr_acq (longtemps volatil, \*long)|
|_InterlockedOr_nf|long _InterlockedOr_nf (longtemps volatil, \*long)|
|_InterlockedOr_rel|long _InterlockedOr_rel (longtemps volatil, \*long)|
|_InterlockedXor|long _InterlockedXor (longtemps \*volatil, long)|
|_InterlockedXor16|_InterlockedXor16 courte (courte volatile, \*courte)|
|_InterlockedXor16_acq|_InterlockedXor16_acq courte (courte \*volatile, courte)|
|_InterlockedXor16_nf|_InterlockedXor16_nf courte (courte volatile, \*courte)|
|_InterlockedXor16_rel|_InterlockedXor16_rel courte (courte \*volatile, courte)|
|_InterlockedXor64|__int64 _InterlockedXor64 (_int64\_volatil \*, \__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (_int64\_volatil \*, \__int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (_int64\_volatil \*, \__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (_int64\_volatil \*, \__int64)|
|_InterlockedXor8|char _InterlockedXor8 (char volatile, \*char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq (char \*volatile, char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf (char \*volatile, char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel (char \*volatile, char)|
|_InterlockedXor_acq|long _InterlockedXor_acq (longtemps volatil, \*long)|
|_InterlockedXor_nf|long _InterlockedXor_nf (longtemps \*volatil, long)|
|_InterlockedXor_rel|long _InterlockedXor_rel (longtemps volatil, \*long)|

[[Retour au sommet](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest intrinsèques

Les éléments intrinsèques de test de bits imbriqués sont communs à toutes les plates-formes. ARM64 `_acq`ajoute `_rel`, `_nf` , et les variantes, qui viennent de modifier la sémantique barrière d’une opération, comme décrit dans [_nf (pas de clôture) Suffix](#nf_suffix) plus tôt dans cet article.

|Nom de fonction|Prototype de fonction|
|-------------------|------------------------|
|_interlockedbittestandreset|char non signé _interlockedbittestandreset (longtemps volatile, \*long)|
|_interlockedbittestandreset_acq|char non signé _interlockedbittestandreset_acq (longtemps volatile, \*long)|
|_interlockedbittestandreset_nf|char non signé _interlockedbittestandreset_nf (longtemps volatile, \*long)|
|_interlockedbittestandreset_rel|char non signé _interlockedbittestandreset_rel (longtemps volatile, \*long)|
|_interlockedbittestandreset64|char non signé _interlockedbittestandreset64 (__int64 volatile, \*__int64)|
|_interlockedbittestandreset64_acq|char _interlockedbittestandreset64_acq non signé (__int64 volatile, \*__int64)|
|_interlockedbittestandreset64_nf|char _interlockedbittestandreset64_nf non signé (__int64 volatile, \*__int64)|
|_interlockedbittestandreset64_rel|char _interlockedbittestandreset64_rel non signé (__int64 volatile, \*__int64)|
|_interlockedbittestandset|char non signé _interlockedbittestandset (longtemps volatile, \*long)|
|_interlockedbittestandset_acq|char non signé _interlockedbittestandset_acq (longtemps volatile, \*long)|
|_interlockedbittestandset_nf|char non signé _interlockedbittestandset_nf (longtemps volatile, \*long)|
|_interlockedbittestandset_rel|char non signé _interlockedbittestandset_rel (longtemps volatile, \*long)|
|_interlockedbittestandset64|char non signé _interlockedbittestandset64 (__int64 volatile, \*__int64)|
|_interlockedbittestandset64_acq|char non signé _interlockedbittestandset64_acq (__int64 volatile, \*__int64)|
|_interlockedbittestandset64_nf|char non signé _interlockedbittestandset64_nf (__int64 volatile, \*__int64)|
|_interlockedbittestandset64_rel|char non signé _interlockedbittestandset64_rel (__int64 volatile, \*__int64)|

[[Retour au sommet](#top)]

## <a name="see-also"></a>Voir aussi

[Compilateur intrinsèque](../intrinsics/compiler-intrinsics.md)\
[ARM intrinsèques](arm-intrinsics.md)\
[Référence d’assembleur ARM](../assembler/arm/arm-assembler-reference.md)\
[Référence linguistique de CMD](../cpp/cpp-language-reference.md)
