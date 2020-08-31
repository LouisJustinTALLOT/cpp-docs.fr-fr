---
title: '&lt;fonctions de bits &gt;'
description: Fonctions permettant d’accéder, de manipuler et de traiter des bits individuels et des séquences de bits
ms.date: 08/28/2020
f1_keywords:
- bit/std::bit_cast
- bit/std::has_single_bit
- bit/std::bit_ceil
- bit/std::bit_floor
- bit/std::bit_width
- bit/std::rotl
- bit/std::rotr
- bit/std::countl_zero
- bit/std::countl_one
- bit/std::countr_zero
- bit/std::countr_one
- bit/std::popcount
helpviewer_keywords:
- std::bit [C++], bit_cast
- std::bit [C++], has_single_bit
- std::bit [C++], bit_ceil
- std::bit [C++], bit_floor
- std::bit [C++], bit_width
- std::bit [C++], rotl
- std::bit [C++], rotr
- std::bit [C++], countl_zero
- std::bit [C++], countl_one
- std::bit [C++], countr_zero
- std::bit [C++], countr_one
- std::bit [C++], popcount
ms.openlocfilehash: 44ec7c4fb2f3fc303b9a96b2b6d5273279fcac12
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194548"
---
# <a name="ltbitgt-functions"></a>&lt;fonctions de bits &gt;

L' \<bit> en-tête comprend les fonctions de modèle non membres suivantes :

| **Fonctions non-membres** | **Description** |
|--------|---------|
|[bit_cast](#bit_cast) | Réinterpréter la représentation de l’objet d’un type à un autre. |
|[bit_ceil](#bit_ceil) | Recherche la plus petite puissance de deux supérieure ou égale à une valeur. |
|[bit_floor](#bit_floor) | Recherche la plus grande puissance de deux non supérieure à une valeur. |
|[bit_width](#bit_width) | Recherche le plus petit nombre de bits nécessaires pour représenter une valeur. |
|[countl_zero](#countl_zero) | Comptez le nombre de bits consécutifs définis sur zéro, en partant du bit le plus significatif. |
|[countl_one](#countl_one) | Comptez le nombre de bits consécutifs définis sur un, en commençant par le bit le plus significatif. |
|[countr_zero](#countr_zero) | Comptez le nombre de bits consécutifs définis sur zéro, à partir du bit le moins significatif. |
|[countr_one](#countl_one) | Comptez le nombre de bits consécutifs définis sur un, en commençant par le bit le moins significatif. |
|[has_single_bit](#has_single_bit) | Vérifiez si une valeur n’a qu’un seul bit défini sur un. Cela revient à tester si une valeur est une puissance de deux. |
|[popcount](#popcount) | Comptez le nombre de bits définis sur un. |
|[rotl](#rotl) | Calcule le résultat d’une rotation vers la gauche au niveau du bit. |
|[rotr](#rotr) | Calcule le résultat d’une rotation vers la droite au niveau du bit. |

## <a name="bit_cast"></a>`bit_cast`

Copiez un modèle de bits à partir d’un objet de type `From` vers un nouvel objet de type `To` .

```cpp
template <class To, class From>
[[nodiscard]] constexpr To bit_cast(const From& from) noexcept;
```

### <a name="parameters"></a>Paramètres

*À*\
Type de la sortie.

*De*\
Type de la valeur à convertir.

*De*\
Valeur à convertir.

### <a name="return-value"></a>Valeur retournée

Objet de type `To`.

Chaque bit du résultat correspond au bit correspondant dans `from` , sauf s’il existe des bits de remplissage dans `To` , auquel cas ces bits dans le résultat ne sont pas spécifiés.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <iostream>

int main()
{
    float f = std::numeric_limits<float>::infinity();
    int i = std::bit_cast<int>(f);
    std::cout << "float f = " << std::hex << f
              << "\nstd::bit_cat<int>(f) = " << std::hex << i << '\n';
    return 0;
}
```

```Output
float f = inf
std::bit_cat<int>(f) = 7f800000
```

### <a name="remarks"></a>Remarques

Le code de bas niveau doit souvent interpréter un objet d’un type comme un autre type. L’objet réinterprété a la même représentation de bit que l’original, mais il s’agit d’un type différent.

Au lieu d’utiliser `reinterpret_cast` , ou `memcpy()` , `bit_cast()` est un meilleur moyen d’effectuer ces conversions. Il est préférable de procéder comme suit :
- `bit_cast()` a la valeur `constexpr`.
- `bit_cast()` requiert que les types soient copiables de façon triviale et de la même taille. Cela empêche les problèmes potentiels que vous pouvez rencontrer à l’aide de `reinterpret_cast` et `memcpy` parce qu’ils peuvent être utilisés par inadvertance et par inadvertance pour convertir des types non triviales. En outre, `memcpy()` peut être utilisé pour effectuer une copie par inadvertance entre des types qui n’ont pas la même taille. Par exemple, un double (8 octets) dans un entier non signé (4 octets), ou l’inverse.

Cette surcharge participe uniquement à la résolution de surcharge dans les cas suivants :
-  `sizeof(To) == sizeof(From)`
- `To` et `From` sont [is_trivially_copyable](https://docs.microsoft.com/cpp/standard-library/is-trivially-copyable-class?view=vs-2019`).

Ce modèle de fonction est `constexpr` si et seulement si `To` , et `From` les types de leurs sous-objets sont :
- n’est pas un type d’Union ou de pointeur
- n’est pas un pointeur vers un type de membre
- non volatile-Qualified
- n’a pas de données membres non static qui est un type référence

## <a name="bit_ceil"></a>`bit_ceil`

Recherche la plus petite puissance de deux supérieure ou égale à une valeur. Par exemple, donné `3` , retourne `4` .

```cpp
template<class T>
[[nodiscard]] constexpr T bit_ceil(T value);
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

 Puissance la plus petite de deux supérieure ou égale à `value` .

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_ceil() takes an unsigned integer type
    {
        auto nextClosestPowerOf2 = std::bit_ceil(i);
        std::cout << "\nbit_ceil(0b" << std::bitset<4>(i) << ") = "
            << "0b" << std::bitset<4>(nextClosestPowerOf2);
    }
    return 0;
}
```

```Output
bit_ceil(0b0000) = 0b0001
bit_ceil(0b0001) = 0b0001
bit_ceil(0b0010) = 0b0010
bit_ceil(0b0011) = 0b0100
bit_ceil(0b0100) = 0b0100
bit_ceil(0b0101) = 0b1000
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="bit_floor"></a>`bit_floor`

Recherche la plus grande puissance de deux non supérieure à une valeur. Par exemple, donné `5` , retourne `4` .

```cpp
template< class T >
[[nodiscard]] constexpr T bit_floor(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

La plus grande puissance de deux qui n’est pas supérieure à `value` . \
Si `value` est égal à zéro, retourne zéro.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_floor() takes an unsigned integer type
    {
        auto previousPowerOf2 = std::bit_floor(i);
        std::cout << "\nbit_floor(0b" << std::bitset<4>(i) << ") = 0b"
            << std::bitset<4>(previousPowerOf2);
    }
    return 0;
}
```

```Output
bit_floor(0b0000) = 0b0000
bit_floor(0b0001) = 0b0001
bit_floor(0b0010) = 0b0010
bit_floor(0b0011) = 0b0010
bit_floor(0b0100) = 0b0100
bit_floor(0b0101) = 0b0100
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="bit_width"></a>`bit_width`

Recherche le plus petit nombre de bits nécessaires pour représenter une valeur.

Par exemple, en fonction de 5 (0b101), retourne 3, car il prend 3 bits binaires pour exprimer la valeur 5.

```cpp
template<class T>
[[nodiscard]] constexpr T bit_width(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

Nombre de bits nécessaires pour représenter `value` . \
Si `value` est égal à zéro, retourne zéro.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <iostream>

int main()
{
    for (unsigned i=0u; i <= 8u; ++i)
    {
        std::cout << "\nbit_width(" << i << ") = "
                      << std::bit_width(i);
    }
    return 0;
}
```

```Output
bit_width(0) = 0
bit_width(1) = 1
bit_width(2) = 2
bit_width(3) = 2
bit_width(4) = 3
bit_width(5) = 3
bit_width(6) = 3
bit_width(7) = 3
bit_width(8) = 4
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="countl_zero"></a>`countl_zero`

Comptez le nombre de bits consécutifs définis sur zéro, en partant du bit le plus significatif.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_zero(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

Nombre de bits nuls consécutifs, à partir du bit le plus significatif. \
Si `value` est égal à zéro, nombre de bits dans le type de `value` .

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountl_zero(0b" << std::bitset<8>(result) << ") = " << std::countl_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countl_zero(0b00000000) = 8
countl_zero(0b00000001) = 7
countl_zero(0b00000010) = 6
countl_zero(0b00000100) = 5
countl_zero(0b00001000) = 4
countl_zero(0b00010000) = 3
countl_zero(0b00100000) = 2
countl_zero(0b01000000) = 1
countl_zero(0b10000000) = 0
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="countl_one"></a>`countl_one`

Comptez le nombre de bits consécutifs définis sur un, en commençant par le bit le plus significatif.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_one(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

Nombre de bits consécutifs définis sur un, à partir du bit le plus significatif.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
        for (unsigned char bit = 128; bit > 0; bit /= 2)
    {
        value |= bit;
        std::cout << "\ncountl_one(0b" << std::bitset<8>(value) << ") = "
            << std::countl_one(value);
    }
    return 0;
}
```

```Output
countl_one(0b10000000) = 1
countl_one(0b11000000) = 2
countl_one(0b11100000) = 3
countl_one(0b11110000) = 4
countl_one(0b11111000) = 5
countl_one(0b11111100) = 6
countl_one(0b11111110) = 7
countl_one(0b11111111) = 8
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="countr_zero"></a>`countr_zero`

Comptez le nombre de bits consécutifs définis sur zéro, à partir du bit le moins significatif.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_zero(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

Nombre de bits nuls consécutifs, à partir du bit le moins significatif. \
Si `value` est égal à zéro, nombre de bits dans le type de `value` .

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountr_zero(0b" << std::bitset<8>(result) << ") = "
            << std::countr_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countr_zero(0b00000000) = 8
countr_zero(0b00000001) = 0
countr_zero(0b00000010) = 1
countr_zero(0b00000100) = 2
countr_zero(0b00001000) = 3
countr_zero(0b00010000) = 4
countr_zero(0b00100000) = 5
countr_zero(0b01000000) = 6
countr_zero(0b10000000) = 7
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="countr_one"></a>`countr_one`

Comptez le nombre de bits consécutifs définis sur un, en commençant par le bit le moins significatif.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_one(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

Nombre de bits consécutifs définis sur un, à partir du bit le moins significatif.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (int bit = 1; bit <= 128; bit *= 2)
    {
        value |= bit;
        std::cout << "\ncountr_one(0b" << std::bitset<8>(value) << ") = "
                      << std::countr_one(value);
    }
    return 0;
}
```

```Output
countr_one(0b00000001) = 1
countr_one(0b00000011) = 2
countr_one(0b00000111) = 3
countr_one(0b00001111) = 4
countr_one(0b00011111) = 5
countr_one(0b00111111) = 6
countr_one(0b01111111) = 7
countr_one(0b11111111) = 8
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="has_single_bit"></a>`has_single_bit`

Vérifie si une valeur n’a qu’un seul bit défini. Cela revient à tester si une valeur est une puissance de deux.
 
```cpp
template <class T>
[[nodiscard]] constexpr bool has_single_bit(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

`true` Si `value` a un seul jeu de bits, ce qui signifie également qu' `value` il s’agit d’une puissance de deux. Sinon, `false`.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>
#include <iomanip>

int main()
{
    for (auto i = 0u; i < 10u; ++i)
    {
        std::cout << "has_single_bit(0b" << std::bitset<4>(i) << ") = "
            << std::boolalpha << std::has_single_bit(i) << '\n';
    }
    return 0;
}
```

```Output
has_single_bit(0b0000) = false
has_single_bit(0b0001) = true
has_single_bit(0b0010) = true
has_single_bit(0b0011) = false
has_single_bit(0b0100) = true
has_single_bit(0b0101) = false
has_single_bit(0b0110) = false
has_single_bit(0b0111) = false
has_single_bit(0b1000) = true
has_single_bit(0b1001) = false
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="popcount"></a>`popcount`

Comptez le nombre de bits définis sur un dans une valeur entière non signée.
 
```cpp
template<class T>
[[nodiscard]] constexpr int popcount(T value) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à tester.

### <a name="return-value"></a>Valeur retournée

Nombre de bits défini sur un dans `value` .

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
   for (unsigned char value = 0; value < 16; value++)
    {
        std::cout << "\npopcount(0b" << std::bitset<4>(value) << ") = "
                      << std::popcount(value);
    }
    return 0;
}
```

```Output
popcount(0b0000) = 0
popcount(0b0001) = 1
popcount(0b0010) = 1
popcount(0b0011) = 2
popcount(0b0100) = 1
popcount(0b0101) = 2
popcount(0b0110) = 2
popcount(0b0111) = 3
popcount(0b1000) = 1
popcount(0b1001) = 2
popcount(0b1010) = 2
popcount(0b1011) = 3
popcount(0b1100) = 2
popcount(0b1101) = 3
popcount(0b1110) = 3
popcount(0b1111) = 4
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="rotl"></a>`rotl`

Fait pivoter les bits d’une valeur entière non signée à gauche du nombre de fois spécifié. Les bits qui « se déposent » du bit le plus à gauche sont pivotés dans le bit le plus à droite.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotl(T value, int s) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à faire pivoter.

*x*\
Nombre de rotations gauches à effectuer.

### <a name="return-value"></a>Valeur retournée

Résultat de rotation `value` gauche, `s` heures.
Si `s` est égal à zéro, retourne `value` . \
Si `s` est négatif, le fait `rotr(value, -s)` . Les bits qui se trouvent dans le bit le plus à droite sont pivotés dans le bit le plus à gauche.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 1;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotl(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotl(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotl(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotl(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotl(0b00000001, 1) = 0b00000010
rotl(0b00000010, 1) = 0b00000100
rotl(0b00000100, 1) = 0b00001000
rotl(0b00001000, 1) = 0b00010000
rotl(0b00010000, 1) = 0b00100000
rotl(0b00100000, 1) = 0b01000000
rotl(0b01000000, 1) = 0b10000000
rotl(0b10000000, 1) = 0b00000001
rotl(0b00000001,-1) = 0b10000000
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="rotr"></a>`rotr`

Fait pivoter les bits du `value` nombre de fois spécifié. Les bits qui « se déplacent » du bit le plus à droite sont retournés vers le bit le plus à gauche.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotr(T value, int s) noexcept;
```

### <a name="parameters"></a>Paramètres

*ajoutée*\
Valeur entière non signée à faire pivoter.

*x*\
Nombre de rotations appropriées à effectuer.

### <a name="return-value"></a>Valeur retournée

Résultat de rotation de `value` droite, d' `s` heures.
Si `s` est égal à zéro, retourne `value` . \
Si `s` est négatif, le fait `rotl(value, -s)` . Les bits qui se déplacent du bit le plus à gauche sont retournés vers le bit le plus à droite.

### <a name="example"></a>Exemple

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 128;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotr(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotr(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotr(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotr(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotr(0b10000000, 1) = 0b01000000
rotr(0b01000000, 1) = 0b00100000
rotr(0b00100000, 1) = 0b00010000
rotr(0b00010000, 1) = 0b00001000
rotr(0b00001000, 1) = 0b00000100
rotr(0b00000100, 1) = 0b00000010
rotr(0b00000010, 1) = 0b00000001
rotr(0b00000001, 1) = 0b10000000
rotr(0b10000000,-1) = 0b00000001
```

### <a name="remarks"></a>Remarques

Cette fonction de modèle participe uniquement à la résolution de surcharge si `T` est un type entier non signé. Par exemple :,,,, `unsigned int` `unsigned long` `unsigned short` `unsigned char` et ainsi de suite.

## <a name="requirements"></a>Spécifications

**En-tête :**\<bit>

**Espace de noms :** std

`/std:c++latest` est obligatoire

## <a name="see-also"></a>Voir aussi

[\<bit>](bit.md)