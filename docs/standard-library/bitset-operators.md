---
title: '&lt;bitset&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: 30367e003d2dad95e870854098e7fcae34f50efa
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243332"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt;, opérateurs

## <a name="op_amp"></a>, opérateur&amp;

Exécute une opération `AND` au niveau du bit entre deux bitsets.

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Le premier des deux bitsets dont les éléments respectifs doivent être combinés avec l’opérateur `AND` au niveau du bit.

*Oui*\
Le deuxième des deux bitsets dont les éléments respectifs doivent être combinés avec l’opérateur `AND` au niveau du bit.

### <a name="return-value"></a>Valeur de retour

Un bitset dont les éléments sont le résultat de l’exécution le `AND` opération sur les éléments correspondants de *gauche* et *droit*.

### <a name="example"></a>Exemple

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a> Opérateur&lt;&lt;

Insère une représentation textuelle de la séquence de bits dans le flux de sortie.

```
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet de type **bitset\<N>** qui doit être inséré dans le flux de sortie sous forme de chaîne.

### <a name="return-value"></a>Valeur de retour

Une représentation textuelle de la séquence de bits dans `ostr`.

### <a name="remarks"></a>Notes

Les surcharges de fonction de modèle `operator<<`, ce qui permet d’être écrit sans conversion en une chaîne d’un bitset. La fonction de modèle est exécutée :

**ostr** << _*droite*. [to_string](bitset-class.md) <**CharType**, **Traits**, **allocateur**\<**CharType**>> ()

### <a name="example"></a>Exemples

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a> Opérateur&gt;&gt;

Lit une chaîne de bits dans un bitset.

```
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>&
_Istr,
    bitset<N>&
    right);
```

### <a name="parameters"></a>Paramètres

*_Istr*\
Chaîne entrée dans le flux d’entrée à insérer dans le bitset.

*Oui*\
Bitset qui reçoit les bits du flux d’entrée.

### <a name="return-value"></a>Valeur de retour

La fonction de modèle retourne la chaîne *_Istr*.

### <a name="remarks"></a>Notes

Les surcharges de fonction de modèle `operator>>` à stocker dans le bitset _ *droite* la valeur bitset (`str`), où `str` est un objet de type [basic_string](basic-string-class.md)  <  **CharType**, **Traits**, **allocateur** \< **CharType**>> **&** extraites *_Istr*.

La fonction de modèle extrait des éléments de *_Istr* et les insère dans le bitset jusqu'à ce que :

- Tous les éléments de bit ont été extraits du flux d’entrée et stockés dans le bitset.

- Le bitset est rempli avec les bits du flux d’entrée.

- Un élément d’entrée est rencontré, qui n’est ni 0, ni 1.

### <a name="example"></a>Exemple

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a> opérateur ^

Exécute une opération `EXCLUSIVE-OR` au niveau du bit entre deux bitsets.

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Le premier des deux bitsets dont les éléments respectifs doivent être combinés avec l’opérateur `EXCLUSIVE-OR` au niveau du bit.

*Oui*\
Le deuxième des deux bitsets dont les éléments respectifs doivent être combinés avec l’opérateur `EXCLUSIVE-OR` au niveau du bit.

### <a name="return-value"></a>Valeur de retour

Un bitset dont les éléments sont le résultat de l’exécution le `EXCLUSIVE-OR` opération sur les éléments correspondants de *gauche* et *droit*.

### <a name="example"></a>Exemples

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a> opérateur&#124;

Exécute une opération `OR` au niveau du bit entre deux bitsets.

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Le premier des deux bitsets dont les éléments respectifs doivent être combinés avec l’opérateur `OR` au niveau du bit.

*Oui*\
Le deuxième des deux bitsets dont les éléments respectifs doivent être combinés avec l’opérateur `OR` au niveau du bit.

### <a name="return-value"></a>Valeur de retour

Un bitset dont les éléments sont le résultat de l’exécution le `OR` opération sur les éléments correspondants de *gauche* et *droit*.

### <a name="example"></a>Exemple

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```
