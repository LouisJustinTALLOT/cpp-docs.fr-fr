---
title: '&lt;charconv, &gt; fonctions'
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: 92f838ededad3e2b8493e934ae2b614247f18458
ms.sourcegitcommit: 4eda68a0b3c23d8cefa56b7ba11583412459b32f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565948"
---
# <a name="ltcharconvgt-functions"></a>&lt;charconv, &gt; fonctions

L' \<charconv> en-tête comprend les fonctions non-membres suivantes :

| **Fonctions non-membres** | **Description** |
|-|-|
|[to_chars](#to_chars) | Convertit une valeur entière ou à virgule flottante en une séquence de **`char`** . |
|[from_chars](#from_chars) | Convertit une séquence de **`char`** en valeur entière ou à virgule flottante. |

Ces fonctions de conversion sont optimisées pour les performances et prennent également en charge le comportement des allers-retours les plus courts. Le comportement d’aller-retour le plus court signifie que lorsqu’un nombre est converti en caractères, seule une précision suffisante est écrite pour permettre la récupération du nombre d’origine lors de la conversion de ces caractères en virgule flottante.

- Lors de la conversion de caractères en nombre, il n’est pas nécessaire que la valeur numérique se termine par un caractère null. De même, lors de la conversion d’un nombre en caractères, le résultat ne se termine pas par un caractère null.
- Les fonctions de conversion n’allouent pas de mémoire. Vous êtes propriétaire de la mémoire tampon dans tous les cas.
- Les fonctions de conversion ne lèvent pas d’exception. Un résultat est retourné à partir duquel vous pouvez déterminer si la conversion a réussi.
- Les fonctions de conversion ne sont pas sensibles au mode d’arrondi du Runtime.
- Les fonctions de conversion ne prennent pas en charge les paramètres régionaux. Ils impriment et analysent toujours les points décimaux en tant que `'.'` , et jamais en tant que', 'pour les paramètres régionaux qui utilisent des virgules.

## `to_chars`

Convertit une valeur entière ou à virgule flottante en une séquence de **`char`** .

Convertit `value` en une chaîne de caractères en remplissant la plage \[ `first` , `last` ), où \[ `first` , `last` ) doit être une plage valide.
Retourne une [structure to_chars_result](to-chars-result-structure.md). Si la conversion réussit, comme indiqué par `to_char_result.ec` , le membre `ptr` est le pointeur le plus à la fin des caractères écrits. Sinon, `to_char_result.ec` a la valeur `errc::value_too_large` , `to_char_result.ptr` a la valeur `last` et le contenu de la plage \[ `first` , `last` ) n’est pas spécifié.

La seule façon dont `to_chars` peut échouer est si vous fournissez une mémoire tampon insuffisante pour contenir le résultat.

```cpp
// integer to chars

to_chars_result to_chars(char* first, char* last, char value, int base = 10);
to_chars_result to_chars(char* first, char* last, signed char value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned char value, int base = 10);
to_chars_result to_chars(char* first, char* last, short value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned short value, int base = 10);
to_chars_result to_chars(char* first, char* last, int value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned int value, int base = 10);
to_chars_result to_chars(char* first, char* last, long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long value, int base = 10);
to_chars_result to_chars(char* first, char* last, long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, bool value, int base = 10) = delete;

// floating-point to chars

to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="parameters"></a>Paramètres

*premier*\
Pointe vers le début de la mémoire tampon à remplir.

*famille*\
Pointe un caractère au-delà de la fin de la mémoire tampon à remplir.

*ajoutée*\
Valeur à convertir. Si `value` est négatif, la représentation commence par `-` .

*base*\
Pour les conversions entières, base à utiliser lors `value` de la conversion en caractères. Doit être compris entre 2 et 36 inclus. Il n’y aura pas de zéro non significatif. Les chiffres de la plage 10.. 35 (inclusives) sont représentés sous forme de caractères minuscules a.. Lettre

*fmt*\
Pour les conversions à virgule flottante, un masque de bits spécifiant le format de conversion à utiliser, par exemple, scientifique, fixe ou hexadécimal. Pour plus d’informations, consultez [chars_format](chars-format-class.md) .

*précision*\
Pour les conversions à virgule flottante, nombre de chiffres de précision pour la valeur convertie.

### <a name="return-value"></a>Valeur de retour

[To_chars_result](to-chars-result-structure.md) contenant le résultat de la conversion.

### <a name="remarks"></a>Notes

Les fonctions qui prennent un paramètre [chars_format](chars-format-class.md) déterminent le spécificateur de conversion comme s’ils utilisaient `printf()` comme suit : le spécificateur de conversion est `'f'` si `fmt` est, si est, si est, `chars_format::fixed` `'e'` `fmt` `chars_format::scientific` `'a'` (sans le début `0x` dans le résultat) si `fmt` est `chars_format::hex` et `'g'` si `fmt` est `chars_format::general` . La spécification de la notation fixe la plus courte peut toujours aboutir à une sortie longue, car il peut s’agir de la représentation la plus courte possible lorsque la valeur est très grande ou très petite.

Le tableau suivant décrit le comportement de conversion en fonction de différentes combinaisons de `fmt` `precision` paramètres et. Le terme « comportement des allers-retours les plus courts » fait référence à l’écriture du plus petit nombre de chiffres nécessaires pour que l’analyse de cette représentation à l’aide de la `from_chars` fonction correspondante récupère exactement la valeur.

| `fmt`et `precision` combinaison | Sortie |
|--|--|
|  Aucun | Le cas échéant, la notation fixe ou scientifique est plus petite, en privilégiant les critère.</br>Ce comportement ne peut pas être simulé par une surcharge qui prend le `fmt` paramètre. |
| `fmt` | Le comportement le plus bref des allers-retours pour le format spécifié, tel que le format scientifique le plus bref. |
| `fmt` et `precision` | Utilise la précision donnée, le `printf()` style suivant, sans le comportement le plus bref des allers-retours. |

### <a name="return-value"></a>Valeur de retour

[To_chars_result](to-chars-result-structure.md) qui contient le résultat de la conversion.

### <a name="example"></a>Exemple

```cpp
#include <charconv>
#include <stdio.h>
#include <system_error>

template <typename T> void TestToChars(const T t)
{
    static_assert(std::is_floating_point_v<T>);
    constexpr bool IsFloat = std::is_same_v<T, float>;

    char buf[100]; // 100 is large enough for double and long double values because the longest possible outputs are "-1.23456735e-36" and "-1.2345678901234567e-100".
    constexpr size_t size = IsFloat ? 15 : 24;
    const std::to_chars_result res = std::to_chars(buf, buf + size, t);  // points to buffer area it can use. Must be char, not wchar_t, etc.
    
    if (res.ec == std::errc{}) // no error
    {
        // %.*s provides the exact number of characters to output because the output range, [buf, res.ptr), isn't null-terminated
        printf("success: %.*s\n", static_cast<int>(res.ptr - buf), buf);
    }
    else // probably std::errc::value_too_large
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }
}

int main()
{
    TestToChars(123.34);
    return 0;
}
```

## `from_chars`

Convertit une séquence de **`char`** en valeur entière ou à virgule flottante.

```cpp
// char to an integer value

from_chars_result from_chars(const char* first, const char* last, char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, signed char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long long& value, int base = 10);

// char to a floating-point value

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

### <a name="parameters"></a>Paramètres

*premier*\
Pointe vers le début de la mémoire tampon de caractères à convertir.

*famille*\
Points un après le dernier élément de la mémoire tampon de caractères à convertir.

*ajoutée*\
Si la conversion réussit, contient le résultat de la conversion.

*base*\
Pour les conversions entières, base à utiliser pendant la conversion. Doit être compris entre 2 et 36 inclus.

*fmt*\
Pour les conversions à virgule flottante, format de la séquence de caractères en cours de conversion. Pour plus d’informations, consultez [chars_format](chars-format-class.md) .

### <a name="remarks"></a>Notes

Les `from_chars()` fonctions analysent la chaîne \[ `first` , `last` ) pour un modèle de nombre, où \[ `first` , `last` ) doit être une plage valide.

Lors de l’analyse de caractères, l’espace blanc n’est pas ignoré. Contrairement `strtod()` à, par exemple, la mémoire tampon doit commencer par une représentation numérique valide.

Retourne une [structure from_chars_result](from-chars-result-structure.md).

Si aucun caractère ne correspond à un modèle de nombre, `value` est non modifié, `from_chars_result.ptr` pointe vers `first` et `from_chars_result.ec` est `errc::invalid_argument` .

Si seuls certains caractères correspondent à un modèle de nombre, `from_chars_result.ptr` pointe vers le premier caractère qui ne correspond pas au modèle, ou a la valeur du `last` paramètre si tous les caractères correspondent.

Si la valeur analysée n’est pas dans la plage qui peut être représentée par le type de `value` , `value` n’est pas modifiée et `from_chars_result.ec` est `errc::result_out_of_range` .

Sinon, `value` est défini sur la valeur analysée, après arrondi, et `from_chars_result.ec` est égal à `errc{}` .

### <a name="example"></a>Exemple

```cpp
#include <charconv>
#include <stdio.h>
#include <string_view>
#include <system_error>

double TestFromChars(const std::string_view sv)
{
    const char* const first = sv.data();
    const char* const last = first + sv.size();
    double dbl;

    const std::from_chars_result res = std::from_chars(first, last, dbl);

    if (res.ec == std::errc{}) // no error
    {
        printf("success: %g\n", dbl);
    }
    else
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }

    return dbl;
}

int main()
{
    double dbl = TestFromChars("123.34");
    return 0;
}
```

## <a name="requirements"></a>Configuration requise

**En-tête :**\<charconv>

**Espace de noms :** std

/std : c++ 17, ou version ultérieure, est requis.

## <a name="see-also"></a>Voir aussi

[\<charconv>](charconv.md)  
[Chaîne décimale la plus petite qui effectue des allers-retours](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/) 
 [spécificateurs de format printf ()](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)