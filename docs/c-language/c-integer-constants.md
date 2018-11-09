---
title: Constantes entières C
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 4a3d6b945f3611b8e51029c0a5ec5dc77b2cbaa0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620218"
---
# <a name="c-integer-constants"></a>Constantes entières C

Une *constante entière* est un nombre décimal (base 10), octal (base 8) ou hexadécimal (base 16) qui représente une valeur intégrale. Utilisez les constantes Integer pour représenter des valeurs entières qui ne peuvent pas être modifiées.

## <a name="syntax"></a>Syntaxe

*integer-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub><br/>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*<br/>

*octal-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*<br/>

*hexadecimal-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*<br/>

*hexadecimal-prefix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**<br/>

*nonzero-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**<br/>

*octal-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**<br/>

*hexadecimal-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**<br/>

*integer-suffix* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*<br/>

*unsigned-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**<br/>

*long-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**<br/>

*long-long-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll LL**<br/>

*64-bit-integer-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**i64 I64**<br/>

Les suffixes **i64** et **I64** sont spécifiques à Microsoft.

Les constantes Integer sont positives, à moins d’être précédées du signe moins (**-**). Le signe moins est interprété comme l'opérateur de négation arithmétique unaire. Pour plus d’informations sur cet opérateur, consultez [Opérateurs arithmétiques unaires](../c-language/unary-arithmetic-operators.md).

Si une constante Integer commence par **0x** ou **0X**, elle est hexadécimale. Si elle commence par le chiffre **0**, elle est octale. Sinon, elle est supposée être décimale.

Les constantes entières suivantes sont équivalentes :

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Aucun espace blanc ne peut séparer les chiffres d'une constante Integer. Ces exemples illustrent certaines des constantes décimales, octales et hexadécimales valides.

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>Voir aussi

[Constantes C](../c-language/c-constants.md)<br/>
