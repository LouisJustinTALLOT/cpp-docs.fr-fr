---
title: fpos, classe
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: 7d60a31e69e8a1ad82086f715cac6dde064d1fac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359203"
---
# <a name="fpos-class"></a>fpos, classe

Le modèle de classe décrit un objet qui peut stocker toutes les informations nécessaires pour restaurer un indicateur arbitraire de position de fichier dans n’importe quel flux. Un objet de classe fpos\< **St**> stocke au moins deux objets membres :

- Un décalage d’octet de type [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Un état de conversion, pour une utilisation par un `St`objet `mbstate_t`de classe basic_filebuf, de type, typiquement .

Il peut également stocker une position de fichier arbitraire, utilisable par un objet de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) de type `fpos_t`. Cependant, pour un environnement avec une taille de fichier limitée, `streamoff` et `fpos_t` peuvent parfois être utilisés de manière interchangeable. Pour un environnement où aucun flux de données n'a un encodage de dépendance d'état, `mbstate_t` peut être inutilisé. Ainsi, le nombre d'objets membres stockés peut varier.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Paramètres

*Étattype*\
Informations d'état.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[fpos](#fpos)|Créer un objet qui contient des informations sur une position (offset) dans un flux.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[seekpos](#seekpos)|Utilisée uniquement en interne par la bibliothèque C++ Standard. N'appelez pas cette méthode à partir de votre code.|
|[État](#state)|Définit ou retourne l'état de la conversion.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur!](#op_neq)|Teste l'inégalité d'indicateurs de position de fichier.|
|[opérateur](#op_add)|incrémente un indicateur de position de fichier.|
|[opérateur](#op_add_eq)|incrémente un indicateur de position de fichier.|
|[opérateur-](#operator-)|Décrémente un indicateur de position de fichier.|
|[opérateur-MD](#operator-_eq)|Décrémente un indicateur de position de fichier.|
|[opérateur](#op_eq_eq)|Teste l'égalité d'indicateurs de position de fichier.|
|[operator streamoff](#op_streamoff)|Convertit un objet de type `fpos` en objet de type `streamoff`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<ios>

**Espace de noms :** std

## <a name="fposfpos"></a><a name="fpos"></a>fpos::fpos

Créer un objet qui contient des informations sur une position (offset) dans un flux.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Paramètres

*_Off*\
Décalage dans le flux.

*_State*\
État de départ de l’objet `fpos`.

*_Filepos*\
Décalage dans le flux.

### <a name="remarks"></a>Notes

Le premier constructeur stocke la *compensation _Off*, par rapport au début du fichier et dans l’état de conversion initial (si cela compte). Si *_Off* est de -1, l’objet résultant représente une position de flux invalide.

Le deuxième constructeur stocke un décalage zéro et l’objet *_State*.

## <a name="fposoperator"></a><a name="op_neq"></a>fpos::opérateur!

Teste l'inégalité d'indicateurs de position de fichier.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Indicateur de position de fichier à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si les indicateurs de position de fichier ne sont pas égaux, sinon **false**.

### <a name="remarks"></a>Notes

La fonction membre retourne `!(*this == right)`.

### <a name="example"></a>Exemple

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="fposoperator"></a><a name="op_add"></a>fpos::opérateur

incrémente un indicateur de position de fichier.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Paramètres

*_Off*\
Décalage duquel vous voulez incrémenter l’indicateur de position de fichier.

### <a name="return-value"></a>Valeur de retour

Position dans le fichier.

### <a name="remarks"></a>Notes

La fonction membre retourne **fpos(\*this) +=** `_Off`.

### <a name="example"></a>Exemple

Consultez [operator!=](#op_neq) pour obtenir un exemple d’utilisation de `operator+`.

## <a name="fposoperator"></a><a name="op_add_eq"></a>fpos::opérateur

incrémente un indicateur de position de fichier.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Paramètres

*_Off*\
Décalage duquel vous voulez incrémenter l’indicateur de position de fichier.

### <a name="return-value"></a>Valeur de retour

Position dans le fichier.

### <a name="remarks"></a>Notes

La fonction membre ajoute *_Off* à l’objet de membre offset stocké, puis retourne ** \*ceci**. Pour le positionnement dans un fichier, le résultat est généralement valide uniquement pour les flux binaires qui n’ont pas de codage dépendant de l’état.

### <a name="example"></a>Exemple

Consultez [operator!=](#op_neq) pour obtenir un exemple d’utilisation de `operator+=`.

## <a name="fposoperator-"></a><a name="operator-"></a>fpos::opérateur-

Décrémente un indicateur de position de fichier.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Position du fichier.

*_Off*\
Décalage du flux.

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne `(streamoff)*this - (streamoff) right`. La deuxième fonction membre retourne `fpos(*this) -= _Off`.

### <a name="example"></a>Exemple

Consultez [operator!=](#op_neq) pour obtenir un exemple d’utilisation de `operator-`.

## <a name="fposoperator-"></a><a name="operator-_eq"></a>fpos::opérateur-MD

Décrémente un indicateur de position de fichier.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Paramètres

*_Off*\
Décalage du flux.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne `fpos(*this) -= _Off`.

### <a name="remarks"></a>Notes

Pour le positionnement dans un fichier, le résultat est généralement valide uniquement pour les flux binaires qui n’ont pas de codage dépendant de l’état.

### <a name="example"></a>Exemple

Consultez [operator!=](#op_neq) pour obtenir un exemple d’utilisation de `operator-=`.

## <a name="fposoperator"></a><a name="op_eq_eq"></a>fpos::opérateur

Teste l'égalité d'indicateurs de position de fichier.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Indicateur de position de fichier à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si les indicateurs de position de fichier sont égaux, sinon **false**.

### <a name="remarks"></a>Notes

La fonction membre retourne `(streamoff)*this == (streamoff)right`.

### <a name="example"></a>Exemple

Consultez [operator!=](#op_neq) pour obtenir un exemple d’utilisation de `operator+=`.

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a>fpos::opérateur streamoff

Convertit un objet de type `fpos` en objet de type `streamoff`.

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne l’objet membre de décalage stocké et tout décalage supplémentaire stocké dans le cadre de l’objet membre `fpos_t`.

### <a name="example"></a>Exemple

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="fposseekpos"></a><a name="seekpos"></a>fpos::seekpos

Cette méthode est uniquement utilisée en interne par la bibliothèque C++ Standard. N'appelez pas cette méthode à partir de votre code.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a>fpos::état

Définit ou retourne l'état de la conversion.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Paramètres

*_State*\
Nouvel état de conversion.

### <a name="return-value"></a>Valeur de retour

État de conversion.

### <a name="remarks"></a>Notes

La fonction du premier membre `St` renvoie la valeur stockée dans l’objet membre. La deuxième fonction de membre *stocke _State* dans l’objet `St` membre.

### <a name="example"></a>Exemple

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
