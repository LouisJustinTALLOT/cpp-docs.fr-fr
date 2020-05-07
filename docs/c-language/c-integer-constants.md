---
title: Constantes entières C
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 48561599896bb8a6f9ee159630ff15df6c0454be
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400510"
---
# <a name="c-integer-constants"></a>Constantes entières C

Une *constante entière* est un nombre décimal (base 10), octal (base 8) ou hexadécimal (base 16) qui représente une valeur intégrale. Utilisez les constantes Integer pour représenter des valeurs entières qui ne peuvent pas être modifiées.

## <a name="syntax"></a>Syntaxe

*integer-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*chiffre différent de zéro*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*

*octal-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**entre**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*

*hexadecimal-constant* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*

*hexadecimal-prefix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0x**

*nonzero-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*octal-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*hexadecimal-digit* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*integer-suffix* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*

*unsigned-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*long-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*long-long-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll LL**

*64-bit-integer-suffix* : un des éléments suivants :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**i64 I64**

Les suffixes **i64** et **I64** sont spécifiques à Microsoft.

Les constantes entières sont positives, sauf si elles sont précédées**-** d’un signe moins (). Le signe moins est interprété comme l'opérateur de négation arithmétique unaire. Pour plus d’informations sur cet opérateur, consultez [Opérateurs arithmétiques unaires](../c-language/unary-arithmetic-operators.md).

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
