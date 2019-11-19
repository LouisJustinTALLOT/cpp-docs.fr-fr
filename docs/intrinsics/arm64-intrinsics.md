---
title: ARM64 intrinsèques
description: Liste des intrinsèques ARM64 pris en charge par le compilateur C++ Microsoft.
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
ms.openlocfilehash: 30881c2b45714f91bf9035819b11ae41322b7086
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163670"
---
# <a name="arm64-intrinsics"></a>ARM64 intrinsèques

Le compilateur C++ Microsoft (MSVC) rend les intrinsèques suivantes disponibles sur l’architecture ARM64. Pour plus d’informations sur ARM, consultez les sections architecture et outils de développement logiciel du site Web de [documentation pour développeurs ARM](https://developer.arm.com/docs) .

## <a name="top"></a>ÉCLAT

Les extensions de jeu d’instructions de vecteur néon pour ARM64 fournissent des fonctionnalités Single Instruction Multiple Data (SIMD). Elles ressemblent à celles des jeux d’instructions vectorielles MMX et SSE qui sont communes aux processeurs d’architecture x86 et x64.

Les intrinsèques néon sont pris en charge, comme indiqué dans le fichier d’en-tête *arm64_neon. h*. La prise en charge par MSVC des intrinsèques néon ressemble à celle du compilateur ARM64, qui est documenté dans la [référence intrinsèque ARM ARM](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) sur le site Web du centre d’informations ARM.

##  <a name="A"></a>Liste des intrinsèques spécifiques à ARM64

|Nom de la fonction|Instruction|Prototype de fonction|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int)|
|__addx18byte||void __addx18byte (unsigned long, unsigned char)|
|__addx18word||void __addx18word (unsigned long, unsigned short)|
|__addx18dword||void __addx18dword (unsigned long, unsigned long)|
|__addx18qword||void __addx18qword (unsigned long, unsigned __int64)|
|__cas8|CASB|unsigned __int8 __cas8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__cas16|CAISSES|unsigned __int16 __cas16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__cas32|CAS|unsigned __int32 __cas32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__cas64|CAS|unsigned __int64 __cas64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casa8|CASAB|unsigned __int8 __casa8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casa16|CASAH|unsigned __int16 __casa16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casa32|CASA|unsigned __int32 __casa32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casa64|CASA|unsigned __int64 __casa64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casl8|CASLB|unsigned __int8 __casl8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casl16|CASLH|unsigned __int16 __casl16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casl32|CASL|unsigned __int32 __casl32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casl64|CASL|unsigned __int64 __casl64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casal8|CASALB|unsigned __int8 __casal8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casal16|CASALH|unsigned __int16 __casal16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casal32|CASAL|unsigned __int32 __casal32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casal64|CASAL|unsigned __int64 __casal64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__crc32b|CRC32B|unsigned __int32 __crc32b (unsigned __int32, unsigned __int32)|
|__crc32h|CRC32H|unsigned __int32 __crc32h (unsigned __int32, unsigned __int32)|
|__crc32w|CRC32W|unsigned __int32 __crc32w (unsigned __int32, unsigned __int32)|
|__crc32d|CRC32X|unsigned __int32 __crc32d (unsigned __int32, unsigned __int64)|
|__crc32cb|CRC32CB|unsigned __int32 __crc32cb (unsigned __int32, unsigned __int32)|
|__crc32ch|CRC32CH|unsigned __int32 __crc32ch (unsigned __int32, unsigned __int32)|
|__crc32cw|CRC32CW|unsigned __int32 __crc32cw (unsigned __int32, unsigned __int32)|
|__crc32cd|CRC32CX|unsigned __int32 __crc32cd (unsigned __int32, unsigned __int64)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> Insère une opération de barrière de mémoire dans le flux d'instructions. Le paramètre `_Type` spécifie le type de restriction que la barrière applique.<br /><br /> Pour plus d’informations sur les types de restrictions qui peuvent être appliqués, consultez [restrictions relatives](#BarrierRestrictions)à la barrière de mémoire.|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> Insère une opération de barrière de mémoire dans le flux d'instructions. Le paramètre `_Type` spécifie le type de restriction que la barrière applique.<br /><br /> Pour plus d’informations sur les types de restrictions qui peuvent être appliqués, consultez [restrictions relatives](#BarrierRestrictions)à la barrière de mémoire.|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> Insère une opération de barrière de mémoire dans le flux d'instructions. Le paramètre `_Type` spécifie le type de restriction que la barrière applique.<br /><br /> Pour plus d’informations sur les types de restrictions qui peuvent être appliqués, consultez [restrictions relatives](#BarrierRestrictions)à la barrière de mémoire.|
|__getReg||__getReg de __int64 non signé (int)|
|__getRegFp||double __getRegFp (int)|
|__getCallerReg||__getCallerReg de __int64 non signé (int)|
|__getCallerRegFp||double __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt (unsigned int,...)|
|__incx18byte||void __incx18byte (unsigned long)|
|__incx18word||void __incx18word (unsigned long)|
|__incx18dword||void __incx18dword (unsigned long)|
|__incx18qword||void __incx18qword (unsigned long)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \__int16 \*)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatile \__int32 \*)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \__int64 \*)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 \*)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store16||void __iso_volatile_store16 (volatile \__int16 \*, \__int16)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store32||void __iso_volatile_store32 (volatile \__int32 \*, \__int32)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store64||void __iso_volatile_store64 (volatile \__int64 \*, \__int64)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__iso_volatile_store8||void __iso_volatile_store8 (volatile \__int8 \*, \__int8)<br /><br /> Pour plus d’informations, consultez [__iso_volatile_load intrinsèques/Store](#IsoVolatileLoadStore).|
|__ldar8|LDARB|unsigned __int8 __ldar8 (unsigned __int8 volatile * _Target)|
|__ldar16|LDARH|unsigned __int16 __ldar16 (unsigned __int16 volatile * _Target)|
|__ldar32|LDAR|unsigned __int32 __ldar32 (unsigned __int32 volatile * _Target)|
|__ldar64|LDAR|unsigned __int64 __ldar64 (unsigned __int64 volatile * _Target)|
|__ldapr8|LDAPRB|unsigned __int8 __ldapr8 (unsigned __int8 volatile * _Target)|
|__ldapr16|LDAPRH|unsigned __int16 __ldapr16 (unsigned __int16 volatile * _Target)|
|__ldapr32|LDAP|unsigned __int32 __ldapr32 (unsigned __int32 volatile * _Target)|
|__ldapr64|LDAP|unsigned __int64 __ldapr64 (unsigned __int64 volatile * _Target)|
|__mulh||\__int64 __mulh (\__int64, \__int64)|
|__prefetch|PRFM|void __cdecl \__prefetch (const void \*)<br /><br /> Fournit un indicateur de mémoire `PRFM` avec l’opération de prérécupération `PLDL1KEEP` au système qu’il est possible d’accéder bientôt à la mémoire à l’adresse spécifiée ou à proximité de celle-ci. Certains systèmes peuvent choisir d’effectuer une optimisation selon ce modèle d’accès mémoire, pour augmenter les performances d’exécution. Cependant, du point de vue du langage C++, la fonction n'a aucun effet observable et peut ne rien faire du tout.|
|__prefetch2|PRFM|void __cdecl \__prefetch (const void \*, uint8_t prfop)<br /><br /> Fournit un indicateur de mémoire `PRFM` avec l’opération de prérécupération fournie au système qui permet d’accéder bientôt à la mémoire à l’adresse spécifiée ou à proximité de celle-ci. Certains systèmes peuvent choisir d’effectuer une optimisation selon ce modèle d’accès mémoire, pour augmenter les performances d’exécution. Cependant, du point de vue du langage C++, la fonction n'a aucun effet observable et peut ne rien faire du tout.|
|__readx18byte||unsigned char __readx18byte (unsigned long)|
|__readx18word||unsigned short __readx18word (unsigned long)|
|__readx18dword||unsigned long __readx18dword (unsigned long)|
|__readx18qword||__readx18qword __int64 non signé (unsigned long)|
|__setReg||void __setReg (int, unsigned __int64)|
|__setRegFp||void __setRegFp (int, double)|
|__setCallerReg||void __setCallerReg (int, unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, double)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert (int, const char \*)|
|__stlr8|STLRB|void __stlr8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__stlr16|STLRH|void __stlr16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__stlr32|STLR|void __stlr32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__stlr64|STLR|void __stlr64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swp8|SWPB|unsigned __int8 __swp8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swp16|SWPH|unsigned __int16 __swp16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swp32|SWP|unsigned __int32 __swp32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swp64|SWP|unsigned __int64 __swp64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpa8|SWPAB|unsigned __int8 __swpa8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpa16|SWPAH|unsigned __int16 __swpa16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpa32|SWPA|unsigned __int32 __swpa32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpa64|SWPA|unsigned __int64 __swpa64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpl8|SWPLB|unsigned __int8 __swpl8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpl16|SWPLH|unsigned __int16 __swpl16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpl32|SWPL|unsigned __int32 __swpl32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpl64|SWPL|unsigned __int64 __swpl64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpal8|SWPALB|unsigned __int8 __swpal8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpal16|SWPALH|unsigned __int16 __swpal16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpal32|SWPAL|unsigned __int32 __swpal32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpal64|SWPAL|unsigned __int64 __swpal64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__sys|TABLE|unsigned int __sys (int, __int64)|
|__svc|SVC|unsigned int __svc (unsigned int,...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte (unsigned long, unsigned char)|
|__writex18word||void __writex18word (unsigned long, unsigned short)|
|__writex18dword||void __writex18dword (unsigned long, unsigned long)|
|__writex18qword||void __writex18qword (unsigned long, unsigned __int64)|
|__umulh||unsigned \__int64 __umulh (unsigned \__int64, unsigned \__int64)|
|_CopyDoubleFromInt64||double _CopyDoubleFromInt64 (\__int64)|
|_CopyFloatFromInt32||float _CopyFloatFromInt32 (\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||unsigned int _CountLeadingOnes64 (unsigned \__int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||unsigned int _CountLeadingSigns64 (\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||unsigned int _CountLeadingZeros64 (unsigned \__int64)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \__int64)|

[[Retour en haut](#top)]

###  <a name="BarrierRestrictions"></a>Restrictions de barrière de mémoire

Les fonctions intrinsèques `__dmb` (barrière de mémoire de données), les `__dsb` (barrière de synchronisation de données) et les `__isb` (barrière de synchronisation d’instruction) utilisent les valeurs prédéfinies suivantes pour spécifier la restriction de barrière de mémoire en termes de domaine de partage et le type d’accès affecté par l’opération.

|Valeur de restriction|Description|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|Système complet, lectures et écritures.|
|_ARM64_BARRIER_ST|Système complet, écritures uniquement.|
|_ARM64_BARRIER_LD|Système complet, en lecture seule.|
|_ARM64_BARRIER_ISH|Interne partageable, lectures et écritures.|
|_ARM64_BARRIER_ISHST|Interne partageable, écritures uniquement.|
|_ARM64_BARRIER_ISHLD|Interne partageable, en lecture seule.|
|_ARM64_BARRIER_NSH|Non partageable, lectures et écritures.|
|_ARM64_BARRIER_NSHST|Non partageable, écritures uniquement.|
|_ARM64_BARRIER_NSHLD|Non partageable, en lecture seule.|
|_ARM64_BARRIER_OSH|Externe partageable, lectures et écritures.|
|_ARM64_BARRIER_OSHST|Externe partageable, écritures uniquement.|
|_ARM64_BARRIER_OSHLD|Externe partageable, en lecture seule.|

Pour le `__isb` intrinsèque, la seule restriction actuellement valide est _ARM64_BARRIER_SY ; toutes les autres valeurs sont réservées par l’architecture.

###  <a name="IsoVolatileLoadStore"></a>__iso_volatile_load intrinsèques/Store

Ces fonctions intrinsèques effectuent explicitement des chargements et des magasins qui ne sont pas soumis aux optimisations du compilateur.

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
Valeur à écrire dans l’emplacement de mémoire spécifié (fonctions intrinsèques de magasin uniquement).

#### <a name="return-value-load-intrinsics-only"></a>Valeur de retour (fonctions intrinsèques de chargement uniquement)

Valeur de l’emplacement de mémoire spécifié par l' *emplacement*.

#### <a name="remarks"></a>Notes

Vous pouvez utiliser les intrinsèques `__iso_volatile_load8/16/32/64` et `__iso_volatile_store8/16/32/64` pour effectuer explicitement des accès à la mémoire qui ne sont pas soumis aux optimisations du compilateur. Le compilateur ne peut pas supprimer, synthétiser ou modifier l’ordre relatif de ces opérations. Toutefois, il ne génère pas de barrières de mémoire matérielle implicites. Par conséquent, le matériel peut toujours réorganiser les accès mémoire observables entre plusieurs threads. Plus précisément, ces fonctions intrinsèques sont équivalentes aux expressions suivantes, telles qu’elles sont compilées sous **/volatile : ISO**.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

Notez que les intrinsèques prennent des pointeurs volatiles de façon à pouvoir traiter des variables volatiles. Toutefois, il n’existe pas d’exigence ou de recommandation pour utiliser des pointeurs volatiles comme arguments. La sémantique de ces opérations est exactement la même si un type régulier non volatile est utilisé.

Pour plus d’informations sur l’argument de ligne de commande **/volatile : ISO** , consultez [/volatile (interprétation de mot clé volatile)](../build/reference/volatile-volatile-keyword-interpretation.md).

##  <a name="I"></a>Prise en charge ARM64 pour les fonctions intrinsèques d’autres architectures

Le tableau suivant répertorie les intrinsèques d’autres architectures prises en charge sur les plateformes ARM64. Si le comportement d’un intrinsèque sur ARM64 diffère de son comportement sur d’autres architectures matérielles, des informations supplémentaires sont indiquées.

|Nom de la fonction|Prototype de fonction|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|void __cdecl \__debugbreak (void)|
|__fastfail|__declspec (noreturn) void \__fastfail (unsigned int)|
|__nop|void __nop(void)|
|__yield|void __yield (void) **Remarque :** sur les plateformes ARM64, cette fonction génère l’instruction yield. Cette instruction indique que le thread effectue une tâche qui peut être temporairement suspendue de l’exécution (par exemple, un spinlock) sans affecter le programme de manière négative. Il permet à l’UC d’exécuter d’autres tâches pendant les cycles d’exécution qui, sans cela, seraient gaspillés.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|unsigned char _BitScanForward (unsigned long \* _Index, unsigned long _Mask)|
|_BitScanForward64|unsigned char _BitScanForward64 (unsigned long \* _Index, unsigned __int64 _Mask)|
|_BitScanReverse|unsigned char _BitScanReverse (unsigned long \* _Index, unsigned long _Mask)|
|_BitScanReverse64|unsigned char _BitScanReverse64 (unsigned long \* _Index, unsigned __int64 _Mask)|
|_bittest|unsigned char _bittest (long const \*, long)|
|_bittest64|unsigned char _bittest64 (__int64 const \*, __int64)|
|_bittestandcomplement|unsigned char _bittestandcomplement (long \*, long)|
|_bittestandcomplement64|unsigned char _bittestandcomplement64 (__int64 \*, __int64)|
|_bittestandreset|unsigned char _bittestandreset (long \*, long)|
|_bittestandreset64|unsigned char _bittestandreset64 (__int64 \*, __int64)|
|_bittestandset|unsigned char _bittestandset (long \*, long)|
|_bittestandset64|unsigned char _bittestandset64 (__int64 \*, __int64)|
|_byteswap_uint64|unsigned __int64 \__cdecl _byteswap_uint64 (unsigned \__int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable (void) **Remarque :** sur les plateformes ARM64, cette fonction génère l’instruction `MSR DAIFCLR,#2`; elle est uniquement disponible en tant qu’intrinsèque.|
|_enable|void __cdecl _enable (void) **Remarque :** sur les plateformes ARM64, cette fonction génère l’instruction `MSR DAIFSET,#2`; elle est uniquement disponible en tant qu’intrinsèque.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|unsigned __int64 \__cdecl _rotl64 (unsigned \__int64 _Value, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|unsigned __int64 \__cdecl _rotr64 (unsigned \__int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[Retour en haut](#top)]

## <a name="interlocked-intrinsics"></a>Intrinsèques verrouillés

Les intrinsèques à blocage sont un ensemble d'intrinsèques qui sont utilisées pour effectuer des opérations de lecture-modification-écriture atomiques. Certaines d'entre elles sont communes à toutes les plateformes. Elles sont répertoriées séparément ici, car il en existe un grand nombre. Étant donné que leurs définitions sont principalement redondantes, il est plus facile de les réfléchir en termes généraux. Leurs noms peuvent être utilisés pour en dériver les comportements exacts.

Le tableau suivant résume la prise en charge par ARM64 des intrinsèques non-dilockd non-BitTest. Chaque cellule du tableau correspond à un nom qui est constitué en ajoutant le nom de l'opération dans la cellule la plus à gauche de la ligne et le nom de type dans la cellule la plus en haut de la colonne à `_Interlocked`. Par exemple, la cellule à l’intersection de la ligne de `Xor` et de la colonne `8` correspond à `_InterlockedXor8` et est entièrement pris en charge. La plupart des fonctions prises en charge peuvent comporter ces suffixes facultatifs : `_acq`, `_rel` et `_nf`. Le suffixe `_acq` indique une sémantique correspondant à « acquérir » et le suffixe `_rel` indique une sémantique correspondant à « libérer ». Le suffixe `_nf` ou « no CLOTURE » est unique pour ARM et ARM64 et est abordé dans la section suivante.

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|Ajouter|aucune.|aucune.|Complète|Complète|aucune.|aucune.|
|and|Complète|Complète|Complète|Complète|aucune.|aucune.|
|CompareExchange|Complète|Complète|Complète|Complète|Complète|Complète|
|Décrémentation|aucune.|Complète|Complète|Complète|aucune.|aucune.|
|Exchange|Complète|Complète|Complète|Complète|aucune.|Complète|
|ExchangeAdd|Complète|Complète|Complète|Complète|aucune.|aucune.|
|Incrémentation|aucune.|Complète|Complète|Complète|aucune.|aucune.|
|Ou|Complète|Complète|Complète|Complète|aucune.|aucune.|
|Xor|Complète|Complète|Complète|Complète|aucune.|aucune.|

Clé :

- **Full**: prend en charge les formulaires plain, `_acq`, `_rel`et `_nf`.

- **None**: non pris en charge

###  <a name="nf_suffix"></a>suffixe _nf (aucune limite)

Le suffixe `_nf` ou « no barrière » indique que l’opération ne se comporte pas comme n’importe quel type de barrière de mémoire, contrairement aux trois formes (Plain, `_acq`et `_rel`) qui se comportent toutes comme un type de cloisonnement. Une utilisation possible du `_nf` Forms consiste à conserver un compteur des statistiques mis à jour par plusieurs threads en même temps, mais dont la valeur n’est pas utilisée autrement pendant l’exécution de plusieurs threads.

### <a name="list-of-interlocked-intrinsics"></a>Liste des intrinsèques verrouillés

|Nom de la fonction|Prototype de fonction|
|-------------------|------------------------|
|_InterlockedAdd|long _InterlockedAdd (long _volatile \*, long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedAdd_acq|long _InterlockedAdd_acq (long volatile \*, long)|
|_InterlockedAdd_nf|long _InterlockedAdd_nf (long volatile \*, long)|
|_InterlockedAdd_rel|long _InterlockedAdd_rel (long volatile \*, long)|
|_InterlockedAnd|long _InterlockedAnd (long volatile \*, long)|
|_InterlockedAnd16|Short _InterlockedAnd16 (Short volatile \*, short)|
|_InterlockedAnd16_acq|Short _InterlockedAnd16_acq (Short volatile \*, short)|
|_InterlockedAnd16_nf|Short _InterlockedAnd16_nf (Short volatile \*, short)|
|_InterlockedAnd16_rel|Short _InterlockedAnd16_rel (Short volatile \*, short)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedAnd8|char _InterlockedAnd8 (char volatile \*, Char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (char volatile \*, Char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char volatile \*, Char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (char volatile \*, Char)|
|_InterlockedAnd_acq|long _InterlockedAnd_acq (long volatile \*, long)|
|_InterlockedAnd_nf|long _InterlockedAnd_nf (long volatile \*, long)|
|_InterlockedAnd_rel|long _InterlockedAnd_rel (long volatile \*, long)|
|_InterlockedCompareExchange|long __cdecl _InterlockedCompareExchange (long volatile \*, long, long)|
|_InterlockedCompareExchange_acq|long _InterlockedCompareExchange_acq (long volatile \*, long, long)|
|_InterlockedCompareExchange_nf|long _InterlockedCompareExchange_nf (long volatile \*, long, long)|
|_InterlockedCompareExchange_rel|long _InterlockedCompareExchange_rel (long volatile \*, long, long)|
|_InterlockedCompareExchange16|Short _InterlockedCompareExchange16 (Short volatile \*, Short, short)|
|_InterlockedCompareExchange16_acq|Short _InterlockedCompareExchange16_acq (Short volatile \*, Short, short)|
|_InterlockedCompareExchange16_nf|Short _InterlockedCompareExchange16_nf (Short volatile \*, Short, short)|
|_InterlockedCompareExchange16_rel|Short _InterlockedCompareExchange16_rel (Short volatile \*, Short, short)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\__int64 volatile \*, \__int64, \__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char volatile \*, Char, Char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char volatile \*, Char, Char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (char volatile \*, Char, Char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (char volatile \*, Char, Char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* \*volatile, void \*, void \*)|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* \*volatile, void \*, void \*)|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* \*volatile, void \*, void \*)|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* \*volatile, void \*, void \*)|
|_InterlockedCompareExchange128|unsigned char _InterlockedCompareExchange128 (\__int64 \* volatile _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|unsigned char _InterlockedCompareExchange128_acq (\__int64 \* volatile _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|unsigned char _InterlockedCompareExchange128_nf (\__int64 \* volatile _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|unsigned char _InterlockedCompareExchange128_rel (\__int64 \* volatile _Destination, \__int64 _ExchangeHigh, \__int64 _ExchangeLow, \__int64 \* _ComparandResult)|
|_InterlockedDecrement|long __cdecl _InterlockedDecrement (long volatile \*)|
|_InterlockedDecrement16|Short _InterlockedDecrement16 (Short volatile \*)|
|_InterlockedDecrement16_acq|Short _InterlockedDecrement16_acq (Short volatile \*)|
|_InterlockedDecrement16_nf|Short _InterlockedDecrement16_nf (Short volatile \*)|
|_InterlockedDecrement16_rel|Short _InterlockedDecrement16_rel (Short volatile \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 volatile \*)|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq (\__int64 volatile \*)|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\__int64 volatile \*)|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 volatile \*)|
|_InterlockedDecrement_acq|long _InterlockedDecrement_acq (long volatile \*)|
|_InterlockedDecrement_nf|long _InterlockedDecrement_nf (long volatile \*)|
|_InterlockedDecrement_rel|long _InterlockedDecrement_rel (long volatile \*)|
|_InterlockedExchange|long __cdecl _InterlockedExchange (long volatile \* _Target, long)|
|_InterlockedExchange_acq|long _InterlockedExchange_acq (long volatile \* _Target, long)|
|_InterlockedExchange_nf|long _InterlockedExchange_nf (long volatile \* _Target, long)|
|_InterlockedExchange_rel|long _InterlockedExchange_rel (long volatile \* _Target, long)|
|_InterlockedExchange16|Short _InterlockedExchange16 (Short volatile \* _Target, short)|
|_InterlockedExchange16_acq|Short _InterlockedExchange16_acq (Short volatile \* _Target, short)|
|_InterlockedExchange16_nf|Short _InterlockedExchange16_nf (Short volatile \* _Target, short)|
|_InterlockedExchange16_rel|Short _InterlockedExchange16_rel (Short volatile \* _Target, short)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (\__int64 volatile \* _Target, \__int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char volatile \* _Target, Char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char volatile \* _Target, Char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char volatile \* _Target, Char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char volatile \* _Target, Char)|
|_InterlockedExchangeAdd|long __cdecl _InterlockedExchangeAdd (long volatile \*, long)|
|_InterlockedExchangeAdd16|Short _InterlockedExchangeAdd16 (Short volatile \*, short)|
|_InterlockedExchangeAdd16_acq|Short _InterlockedExchangeAdd16_acq (Short volatile \*, short)|
|_InterlockedExchangeAdd16_nf|Short _InterlockedExchangeAdd16_nf (Short volatile \*, short)|
|_InterlockedExchangeAdd16_rel|Short _InterlockedExchangeAdd16_rel (Short volatile \*, short)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (char volatile \*, Char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (char volatile \*, Char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (char volatile \*, Char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (char volatile \*, Char)|
|_InterlockedExchangeAdd_acq|long _InterlockedExchangeAdd_acq (long volatile \*, long)|
|_InterlockedExchangeAdd_nf|long _InterlockedExchangeAdd_nf (long volatile \*, long)|
|_InterlockedExchangeAdd_rel|long _InterlockedExchangeAdd_rel (long volatile \*, long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* \* volatile _Target, void \*)|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* \* volatile _Target, void \*)|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* \* volatile _Target, void \*)|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* \* volatile _Target, void \*)|
|_InterlockedIncrement|long __cdecl _InterlockedIncrement (long volatile \*)|
|_InterlockedIncrement16|Short _InterlockedIncrement16 (Short volatile \*)|
|_InterlockedIncrement16_acq|Short _InterlockedIncrement16_acq (Short volatile \*)|
|_InterlockedIncrement16_nf|Short _InterlockedIncrement16_nf (Short volatile \*)|
|_InterlockedIncrement16_rel|Short _InterlockedIncrement16_rel (Short volatile \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\__int64 volatile \*)|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq (\__int64 volatile \*)|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf (\__int64 volatile \*)|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\__int64 volatile \*)|
|_InterlockedIncrement_acq|long _InterlockedIncrement_acq (long volatile \*)|
|_InterlockedIncrement_nf|long _InterlockedIncrement_nf (long volatile \*)|
|_InterlockedIncrement_rel|long _InterlockedIncrement_rel (long volatile \*)|
|_InterlockedOr|long _InterlockedOr (long volatile \*, long)|
|_InterlockedOr16|Short _InterlockedOr16 (Short volatile \*, short)|
|_InterlockedOr16_acq|Short _InterlockedOr16_acq (Short volatile \*, short)|
|_InterlockedOr16_nf|Short _InterlockedOr16_nf (Short volatile \*, short)|
|_InterlockedOr16_rel|Short _InterlockedOr16_rel (Short volatile \*, short)|
|_InterlockedOr64|__int64 _InterlockedOr64 (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedOr8|char _InterlockedOr8 (char volatile \*, Char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char volatile \*, Char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char volatile \*, Char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel (char volatile \*, Char)|
|_InterlockedOr_acq|long _InterlockedOr_acq (long volatile \*, long)|
|_InterlockedOr_nf|long _InterlockedOr_nf (long volatile \*, long)|
|_InterlockedOr_rel|long _InterlockedOr_rel (long volatile \*, long)|
|_InterlockedXor|long _InterlockedXor (long volatile \*, long)|
|_InterlockedXor16|Short _InterlockedXor16 (Short volatile \*, short)|
|_InterlockedXor16_acq|Short _InterlockedXor16_acq (Short volatile \*, short)|
|_InterlockedXor16_nf|Short _InterlockedXor16_nf (Short volatile \*, short)|
|_InterlockedXor16_rel|Short _InterlockedXor16_rel (Short volatile \*, short)|
|_InterlockedXor64|__int64 _InterlockedXor64 (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\__int64 volatile \*, \__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\__int64 volatile \*, \__int64)|
|_InterlockedXor8|char _InterlockedXor8 (char volatile \*, Char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq (char volatile \*, Char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf (char volatile \*, Char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel (char volatile \*, Char)|
|_InterlockedXor_acq|long _InterlockedXor_acq (long volatile \*, long)|
|_InterlockedXor_nf|long _InterlockedXor_nf (long volatile \*, long)|
|_InterlockedXor_rel|long _InterlockedXor_rel (long volatile \*, long)|

[[Retour en haut](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest intrinsèques

Les intrinsèques de test de bit avec verrouillage brut sont communs à toutes les plateformes. ARM64 ajoute des variantes `_acq`, `_rel`et `_nf`, qui modifient simplement la sémantique de cloisonnement d’une opération, comme décrit dans [_Nf suffixe (sans délimiteur)](#nf_suffix) plus haut dans cet article.

|Nom de la fonction|Prototype de fonction|
|-------------------|------------------------|
|_interlockedbittestandreset|unsigned char _interlockedbittestandreset (long volatile \*, long)|
|_interlockedbittestandreset_acq|unsigned char _interlockedbittestandreset_acq (long volatile \*, long)|
|_interlockedbittestandreset_nf|unsigned char _interlockedbittestandreset_nf (long volatile \*, long)|
|_interlockedbittestandreset_rel|unsigned char _interlockedbittestandreset_rel (long volatile \*, long)|
|_interlockedbittestandreset64|unsigned char _interlockedbittestandreset64 (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_acq|unsigned char _interlockedbittestandreset64_acq (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_nf|unsigned char _interlockedbittestandreset64_nf (__int64 volatile \*, __int64)|
|_interlockedbittestandreset64_rel|unsigned char _interlockedbittestandreset64_rel (__int64 volatile \*, __int64)|
|_interlockedbittestandset|unsigned char _interlockedbittestandset (long volatile \*, long)|
|_interlockedbittestandset_acq|unsigned char _interlockedbittestandset_acq (long volatile \*, long)|
|_interlockedbittestandset_nf|unsigned char _interlockedbittestandset_nf (long volatile \*, long)|
|_interlockedbittestandset_rel|unsigned char _interlockedbittestandset_rel (long volatile \*, long)|
|_interlockedbittestandset64|unsigned char _interlockedbittestandset64 (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_acq|unsigned char _interlockedbittestandset64_acq (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_nf|unsigned char _interlockedbittestandset64_nf (__int64 volatile \*, __int64)|
|_interlockedbittestandset64_rel|unsigned char _interlockedbittestandset64_rel (__int64 volatile \*, __int64)|

[[Retour en haut](#top)]

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Intrinsèques ARM](arm-intrinsics.md)\
\ de référence de l' [assembleur ARM](../assembler/arm/arm-assembler-reference.md)
[C++Référence du langage](../cpp/cpp-language-reference.md)
