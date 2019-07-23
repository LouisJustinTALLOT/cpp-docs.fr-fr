---
title: is, isw, routines
ms.date: 11/04/2016
apilocation:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- isw
- is
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
ms.openlocfilehash: 1550f8f012802e03e9228e67c381915b1b4e1d64
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376033"
---
# <a name="is-isw-routines"></a>is, isw, routines

|||
|-|-|
|[isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|
|[isalpha, iswalpha, _isalpha_l, _iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower, iswlower, _islower_l, _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|
|[isblank, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint, iswprint, _isprint_l, _iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|
|[iscsym, iscsymf, __iscsym, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|
|[isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|

## <a name="remarks"></a>Remarques

Ces routines testent les caractères pour des conditions spécifiées.

Les routines **is** produisent des résultats significatifs pour tout argument entier compris entre -1 (`EOF`) et **UCHAR_MAX** (0xFF), inclus. Le type d’argument attendu est `int`.

> [!CAUTION]
> Pour les routines **is**, le fait de passer un argument de type `char` peut produire des résultats imprévisibles. Toutefois, un caractère codé sur un octet SBCS ou MBCS de type `char` avec une valeur supérieure à 0x7F est négatif. Si un `char` est passé, le compilateur peut convertir la valeur en une valeur `int` signée ou une valeur **long** signée. Le compilateur peut la convertir en valeur de type signe étendu, avec des résultats inattendus.

Les routines **isw** produisent des résultats significatifs pour toute valeur entière comprise entre -1 (**WEOF**) et 0xFFFF, inclus. Le type de données **wint_t** est défini dans WCHAR.H comme un **unsigned short**. Il peut contenir n’importe quel caractère large ou la valeur de caractère large de fin de fichier (**WEOF**).

La valeur de sortie est affectée par la valeur du paramètre de catégorie `LC_CTYPE` des paramètres régionaux. Pour plus d’informations, consultez [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis.

Dans les paramètres régionaux « C », les conditions de test des routines **is** sont comme suit :

`isalnum`<br/>
Alphanumériques (A - Z, a - z ou 0 - 9).

`isalpha`<br/>
Alphabétiques (A - Z ou a - z).

`__isascii`<br/>
Jeu de caractères ASCII (0x00 - 0x7F)

`isblank`<br/>
Tabulation horizontale ou espace (0x09 ou 0x20)

`iscntrl`<br/>
Caractère de contrôle (0x00-0x1F ou 0x7F)

`__iscsym`<br/>
Lettre, trait de soulignement ou chiffre

`__iscsymf`<br/>
Lettre ou trait de soulignement

`isdigit`<br/>
Nombre décimal (0 - 9)

`isgraph`<br/>
Caractère imprimable sauf espace ( )

`islower`<br/>
Lettre minuscule (a - z)

`isprint`<br/>
Caractère imprimable, y compris les espaces (0x20 - 0x7E)

`ispunct`<br/>
Caractère de ponctuation

`isspace`<br/>
Espace blanc (0x09-0x0D ou 0x20)

`isupper`<br/>
Lettre majuscule (A - Z)

`isxdigit`<br/>
Chiffre hexadécimal (A - F, a - f, ou 0 - 9)

Pour les routines **isw**, le résultat du test de la condition spécifiée est indépendant des paramètres régionaux. Les conditions de test pour les fonctions **isw** sont les suivantes :

`iswalnum`<br/>
`iswalpha` ou `iswdigit`.

`iswalpha`<br/>
Tout caractère large qui fait partie d’un jeu défini par l’implémentation et pour lequel aucun des `iswcntrl`, `iswdigit`, `iswpunct` ou `iswspace` n’est différent de zéro. `iswalpha` retourne une valeur différente de zéro pour les caractères larges dont `iswupper` ou `iswlower` est différent de zéro.

`iswascii`<br/>
Représentation d’un caractère ASCII (0x0000 - 0x007F) sous forme de caractère large

`iswblank`<br/>
Caractère large qui correspond au caractère espace standard ou fait partie d’un jeu de caractères larges défini par l’implémentation pour lequel `iswalnum` a la valeur false Les caractères vides standard sont l’espace (L' ') et la tabulation horizontale (L'\t').

`iswcntrl`<br/>
Caractère large de contrôle

`__iswcsym`<br/>
Tout caractère large pour lequel `isalnum` est true, ou le caractère « _ ».

`__iswcsymf`<br/>
Tout caractère large pour lequel `iswalpha` est true, ou le caractère « _ ».

`iswctype`<br/>
La propriété du caractère est spécifiée par l’argument `desc`. Pour chaque valeur valide de l’argument `desc` de `iswctype`, il existe une routine de classification de caractères larges équivalente, comme dans le tableau suivant :

### <a name="equivalence-of-iswctypec-desc-to-other-isw-testing-routines"></a>Équivalence d’iswctype(c, desc) aux autres routines de test isw

|Valeur de l’argument *desc*|équivalent d’iswctype ( *c, desc* )|
|------------------------------|----------------------------------------|
|**_ALPHA**|**iswalpha(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT**|**iswalnum(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_CONTROL**|**iswcntrl(** `c` **)**|
|**_DIGIT**|**iswdigit(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph(** `c` **)**|
|**_LOWER**|**iswlower(** `c` **)**|
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint(** `c` **)**|
|**_PUNCT**|**iswpunct(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_SPACE**|**iswspace(** `c` **)**|
|**_UPPER**|**iswupper(** `c` **)**|
|**_HEX**|**iswxdigit(** `c` **)**|

`iswdigit`<br/>
Caractère large correspondant à un caractère numérique décimal.

`iswgraph`<br/>
Caractère large imprimable, à l’exception des caractères larges d’espace (L' ').

`iswlower`<br/>
Lettre minuscule ou l’un des jeux de caractères larges définis par l’implémentation et pour lequel aucun des `iswcntrl`, `iswdigit`, `iswpunct` ou `iswspace` n’est différent de zéro. `iswlower` retourne une valeur différente de zéro uniquement pour les caractères larges qui correspondent à des lettres minuscules.

`iswprint`<br/>
Caractère large imprimable, y compris les caractères larges d’espace (L' ').

`iswpunct`<br/>
Caractère large imprimable qui n’est ni le caractère d’espace large (L' '), ni un caractère large pour lequel `iswalnum` est différent de zéro.

`iswspace`<br/>
Caractère large qui correspond au caractère d’espace blanc standard ou fait partie d’un jeu de caractères larges défini par l’implémentation pour lequel `iswalnum` a la valeur false. Les caractères d’espace blanc standard sont l’espace (L' '), le saut de page (L'\f'), le saut de ligne (L'\n'), le retour chariot (L'\r'), la tabulation horizontale (L'\t') et la tabulation verticale (L'\v').

`iswupper`<br/>
Caractère large en lettre majuscule ou qui fait partie d’un jeu de caractères larges défini par l’implémentation et pour lequel aucun des `iswcntrl`, `iswdigit`, `iswpunct` ou `iswspace` n’est différent de zéro. `iswupper` retourne une valeur différente de zéro uniquement pour les caractères larges qui correspondent à des lettres majuscules.

`iswxdigit`<br/>
Caractère large qui correspond à un caractère numérique hexadécimal.

## <a name="example"></a>Exemples

```C
// crt_isfam.c
/* This program tests all characters between 0x0
* and 0x7F, then displays each character with abbreviations
* for the character-type codes that apply.
*/

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   for( ch = 0; ch <= 0x7F; ch++ )
   {
      printf( "%.2x  ", ch );
      printf( " %c", isprint( ch )  ? ch   : ' ' );
      printf( "%4s", isalnum( ch )  ? "AN" : "" );
      printf( "%3s", isalpha( ch )  ? "A"  : "" );
      printf( "%3s", __isascii( ch )  ? "AS" : "" );
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );
      printf( "%3s", isdigit( ch )  ? "D"  : "" );
      printf( "%3s", isgraph( ch )  ? "G"  : "" );
      printf( "%3s", islower( ch )  ? "L"  : "" );
      printf( "%3s", ispunct( ch )  ? "PU" : "" );
      printf( "%3s", isspace( ch )  ? "S"  : "" );
      printf( "%3s", isprint( ch )  ? "PR" : "" );
      printf( "%3s", isupper( ch )  ? "U"  : "" );
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );
      printf( ".\n" );
   }
}
```

## <a name="output"></a>Sortie

```Output
00            AS  C                              .
01            AS  C                              .
02            AS  C                              .
03            AS  C                              .
04            AS  C                              .
05            AS  C                              .
06            AS  C                              .
07            AS  C                              .
08            AS  C                              .
09            AS  C                    S         .
0a            AS  C                    S         .
0b            AS  C                    S         .
0c            AS  C                    S         .
0d            AS  C                    S         .
0e            AS  C                              .
0f            AS  C                              .
10            AS  C                              .
11            AS  C                              .
12            AS  C                              .
13            AS  C                              .
14            AS  C                              .
15            AS  C                              .
16            AS  C                              .
17            AS  C                              .
18            AS  C                              .
19            AS  C                              .
1a            AS  C                              .
1b            AS  C                              .
1c            AS  C                              .
1d            AS  C                              .
1e            AS  C                              .
1f            AS  C                              .
20            AS                       S PR      .
21   !        AS              G    PU    PR      .
22   "        AS              G    PU    PR      .
23   #        AS              G    PU    PR      .
24   $        AS              G    PU    PR      .
25   %        AS              G    PU    PR      .
26   &        AS              G    PU    PR      .
27   '        AS              G    PU    PR      .
28   (        AS              G    PU    PR      .
29   )        AS              G    PU    PR      .
2a   *        AS              G    PU    PR      .
2b   +        AS              G    PU    PR      .
2c   ,        AS              G    PU    PR      .
2d   -        AS              G    PU    PR      .
2e   .        AS              G    PU    PR      .
2f   /        AS              G    PU    PR      .
30   0  AN    AS   CS      D  G          PR     X.
31   1  AN    AS   CS      D  G          PR     X.
32   2  AN    AS   CS      D  G          PR     X.
33   3  AN    AS   CS      D  G          PR     X.
34   4  AN    AS   CS      D  G          PR     X.
35   5  AN    AS   CS      D  G          PR     X.
36   6  AN    AS   CS      D  G          PR     X.
37   7  AN    AS   CS      D  G          PR     X.
38   8  AN    AS   CS      D  G          PR     X.
39   9  AN    AS   CS      D  G          PR     X.
3a   :        AS              G    PU    PR      .
3b   ;        AS              G    PU    PR      .
3c   <        AS              G    PU    PR      .
3d   =        AS              G    PU    PR      .
3e   >        AS              G    PU    PR      .
3f   ?        AS              G    PU    PR      .
40   @        AS              G    PU    PR      .
41   A  AN  A AS   CS CSF     G          PR  U  X.
42   B  AN  A AS   CS CSF     G          PR  U  X.
43   C  AN  A AS   CS CSF     G          PR  U  X.
44   D  AN  A AS   CS CSF     G          PR  U  X.
45   E  AN  A AS   CS CSF     G          PR  U  X.
46   F  AN  A AS   CS CSF     G          PR  U  X.
47   G  AN  A AS   CS CSF     G          PR  U   .
48   H  AN  A AS   CS CSF     G          PR  U   .
49   I  AN  A AS   CS CSF     G          PR  U   .
4a   J  AN  A AS   CS CSF     G          PR  U   .
4b   K  AN  A AS   CS CSF     G          PR  U   .
4c   L  AN  A AS   CS CSF     G          PR  U   .
4d   M  AN  A AS   CS CSF     G          PR  U   .
4e   N  AN  A AS   CS CSF     G          PR  U   .
4f   O  AN  A AS   CS CSF     G          PR  U   .
50   P  AN  A AS   CS CSF     G          PR  U   .
51   Q  AN  A AS   CS CSF     G          PR  U   .
52   R  AN  A AS   CS CSF     G          PR  U   .
53   S  AN  A AS   CS CSF     G          PR  U   .
54   T  AN  A AS   CS CSF     G          PR  U   .
55   U  AN  A AS   CS CSF     G          PR  U   .
56   V  AN  A AS   CS CSF     G          PR  U   .
57   W  AN  A AS   CS CSF     G          PR  U   .
58   X  AN  A AS   CS CSF     G          PR  U   .
59   Y  AN  A AS   CS CSF     G          PR  U   .
5a   Z  AN  A AS   CS CSF     G          PR  U   .
5b   [        AS              G    PU    PR      .
5c   \        AS              G    PU    PR      .
5d   ]        AS              G    PU    PR      .
5e   ^        AS              G    PU    PR      .
5f   _        AS   CS CSF     G    PU    PR      .
60   `        AS              G    PU    PR      .
61   a  AN  A AS   CS CSF     G  L       PR     X.
62   b  AN  A AS   CS CSF     G  L       PR     X.
63   c  AN  A AS   CS CSF     G  L       PR     X.
64   d  AN  A AS   CS CSF     G  L       PR     X.
65   e  AN  A AS   CS CSF     G  L       PR     X.
66   f  AN  A AS   CS CSF     G  L       PR     X.
67   g  AN  A AS   CS CSF     G  L       PR      .
68   h  AN  A AS   CS CSF     G  L       PR      .
69   i  AN  A AS   CS CSF     G  L       PR      .
6a   j  AN  A AS   CS CSF     G  L       PR      .
6b   k  AN  A AS   CS CSF     G  L       PR      .
6c   l  AN  A AS   CS CSF     G  L       PR      .
6d   m  AN  A AS   CS CSF     G  L       PR      .
6e   n  AN  A AS   CS CSF     G  L       PR      .
6f   o  AN  A AS   CS CSF     G  L       PR      .
70   p  AN  A AS   CS CSF     G  L       PR      .
71   q  AN  A AS   CS CSF     G  L       PR      .
72   r  AN  A AS   CS CSF     G  L       PR      .
73   s  AN  A AS   CS CSF     G  L       PR      .
74   t  AN  A AS   CS CSF     G  L       PR      .
75   u  AN  A AS   CS CSF     G  L       PR      .
76   v  AN  A AS   CS CSF     G  L       PR      .
77   w  AN  A AS   CS CSF     G  L       PR      .
78   x  AN  A AS   CS CSF     G  L       PR      .
79   y  AN  A AS   CS CSF     G  L       PR      .
7a   z  AN  A AS   CS CSF     G  L       PR      .
7b   {        AS              G    PU    PR      .
7c   |        AS              G    PU    PR      .
7d   }        AS              G    PU    PR      .
7e   ~        AS              G    PU    PR      .
7f            AS  C                              .
```

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../c-runtime-library/locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[to, fonctions](../c-runtime-library/to-functions.md)
