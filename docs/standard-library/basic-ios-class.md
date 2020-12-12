---
description: 'En savoir plus sur : classe basic_ios'
title: basic_ios, classe
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: 54b70092860002b85b2a603ad5d4dc5a611007ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321545"
---
# <a name="basic_ios-class"></a>basic_ios, classe

Le modèle de classe décrit les fonctions membres et de stockage communes aux flux d’entrée (de classe de modèle [basic_istream](../standard-library/basic-istream-class.md)) et les flux de sortie (de modèle de classe [basic_ostream](../standard-library/basic-ostream-class.md)) qui dépendent des paramètres du modèle. (La classe [ios_base](../standard-library/ios-base-class.md) décrit ce qui est commun et non dépendant des paramètres de modèle.) Un objet de classe **basic_ios \<class Elem, class Traits>** permet de contrôler un flux avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Traits` .

## <a name="syntax"></a>Syntaxe

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Paramètres

*Elem*\
Type de caractère.

*Caractéristiques*\
Type qui fournit des informations sur le type de caractère, la valeur par défaut est `char_traits < Elem >` .

## <a name="remarks"></a>Notes

Objet de la classe **basic_ios \<class Elem, class Traits>** stocke :

- Pointeur de lien vers un objet de type [basic_istream](../standard-library/basic-istream-class.md) **\<Elem, Traits>** .

- Pointeur de mémoire tampon de flux vers un objet de type [basic_streambuf](../standard-library/basic-streambuf-class.md) **\<Elem, Traits >** .

- Des [informations sur la mise en forme](../standard-library/ios-base-class.md).

- Des [informations sur l’état du flux](../standard-library/ios-base-class.md) dans un objet de base de type [ios_base](../standard-library/ios-base-class.md).

- Un caractère de remplissage dans un objet de type `char_type`.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ios](#basic_ios)|Construit la classe `basic_ios`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Synonyme pour le paramètre du modèle `Elem`.|
|[int_type](#int_type)|Synonyme de `Traits::int_type`.|
|[off_type](#off_type)|Synonyme de `Traits::off_type`.|
|[pos_type](#pos_type)|Synonyme de `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonyme pour le paramètre du modèle `Traits`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[incorrect](#bad)|Indique une perte d'intégrité de la mémoire tampon du flux.|
|[clear](#clear)|Efface tous les indicateurs d'erreur.|
|[copyfmt](#copyfmt)|Copie les indicateurs d'un flux vers un autre.|
|[EOF](#eof)|Indique si la fin d'un flux a été atteinte.|
|[exceptions](#exceptions)|Indique les exceptions qui seront levées par le flux.|
|[incident](#fail)|Indique l'échec de l'extraction d'un champ valide dans un flux.|
|[complète](#fill)|Spécifie ou retourne le caractère qui est utilisé quand le texte n'est pas aussi large que le flux.|
|[good](#good)|Indique que le flux est en bon état.|
|[imbue](#imbue)|Change les paramètres régionaux.|
|[init](#init)|Appelé par les constructeurs `basic_ios`.|
|[move](#move)|Déplace toutes les valeurs, sauf le pointeur vers la mémoire tampon du flux, du paramètre vers l'objet actuel.|
|[narrow](#narrow)|Trouve le caractère équivalent à un type `char_type` donné.|
|[rdbuf](#rdbuf)|Dirige le flux vers la mémoire tampon spécifiée.|
|[rdstate](#rdstate)|Lit l'état des bits pour les indicateurs.|
|[set_rdbuf](#set_rdbuf)|Affecte une mémoire tampon de flux comme mémoire tampon de lecture pour cet objet de flux.|
|[setstate](#setstate)|Définit des indicateurs supplémentaires.|
|[swap](#swap)|Échange les valeurs de cet objet `basic_ios` avec celles d'un autre objet `basic_ios`. Les pointeurs vers les mémoires tampons de flux ne sont pas échangés.|
|[tie](#tie)|Garantit qu'un flux est traité avant un autre flux.|
|[widen](#widen)|Trouve le type `char_type` équivalent à un caractère donné.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur explicite bool](#op_bool)|Autorise l’utilisation d’un `basic_ios` objet en tant que **`bool`** . La conversion de type automatique est désactivée pour éviter des effets secondaires involontaires courants.|
|[opérateur void *](#op_void_star)|Indique si le flux est toujours en bon état.|
|[and!](#op_not)|Indique si le flux n'est pas en mauvais état.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<ios>

**Espace de noms :** std

## <a name="basic_iosbad"></a><a name="bad"></a> basic_ios :: Bad

Indique une perte d’intégrité de la mémoire tampon de flux

```cpp
bool bad() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si `rdstate & badbit` est différent de zéro ; sinon, **`false`** .

Pour plus d’informations sur `badbit`, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Exemple

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a> basic_ios :: basic_ios

Construit la classe basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Paramètres

*aspirateur*\
Mémoire tampon standard pour stocker les éléments d’entrée ou de sortie.

### <a name="remarks"></a>Notes

Le premier constructeur initialise ses objets membres en appelant [init](#init)(_ *Sb*). Le deuxième constructeur (protégé) laisse ses objets membres non initialisés. Un appel ultérieur à `init` doit initialiser l’objet avant qu’il puisse être détruit en toute sécurité.

## <a name="basic_ioschar_type"></a><a name="char_type"></a> basic_ios :: char_type

Synonyme pour le paramètre du modèle `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a> basic_ios :: Clear

Efface tous les indicateurs d'erreur.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Paramètres

*Département*\
Facultatif Indicateurs à définir après l’effacement de tous les indicateurs. La valeur par défaut est `goodbit`.

*reraise*\
Facultatif Spécifie si l’exception doit être levée à nouveau. La valeur par défaut **`false`** est (ne déclenche pas à nouveau l’exception).

### <a name="remarks"></a>Notes

Les indicateurs sont `goodbit` , `failbit` , `eofbit` et `badbit` . Testez ces indicateurs avec [good](#good), [bad](#bad), [eof](#eof) et [fail](#fail)

La fonction membre remplace les informations d'état de flux stockées par :

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Si `state` **&** [exceptions](#exceptions) est différent de zéro, il lève alors un objet de la classe [Failure](../standard-library/ios-base-class.md#failure).

### <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de, consultez [rdstate](#rdstate) et [getline](../standard-library/string-functions.md#getline) `clear` .

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a> basic_ios :: copyfmt

Copie les indicateurs d'un flux vers un autre.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Flux dont vous voulez copier les indicateurs.

### <a name="return-value"></a>Valeur renvoyée

**`this`** Objet pour le flux vers lequel vous copiez les indicateurs.

### <a name="remarks"></a>Notes

La fonction membre signale l' **\_ événement d’effacement** d’événement de rappel. Il copie ensuite de *droite* dans **\* ce** caractère de remplissage, le pointeur de liaison et les informations de mise en forme. Avant de modifier le masque d’exception, il signale l’événement de rappel `copyfmt_event` . Si, une fois que la copie est terminée, **state &**[exceptions](#exceptions) est différent de zéro, la fonction appelle [clear](#clear) avec l’argument [rdstate](#rdstate). Elle retourne **\* This**.

### <a name="example"></a>Exemple

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="basic_ioseof"></a><a name="eof"></a> basic_ios :: EOF

Indique si la fin d'un flux a été atteinte.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si la fin du flux a été atteinte ; **`false`** sinon,.

### <a name="remarks"></a>Notes

La fonction membre retourne **`true`** si [rdstate](#rdstate) `& eofbit` est différent de zéro. Pour plus d’informations sur `eofbit`, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Exemple

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="basic_iosexceptions"></a><a name="exceptions"></a> basic_ios :: exceptions

Indique les exceptions qui seront levées par le flux.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Paramètres

*Newexcept*\
Indicateurs pour lesquels vous voulez lever une exception.

### <a name="return-value"></a>Valeur renvoyée

Les indicateurs sont actuellement spécifiés pour lever une exception pour le flux.

### <a name="remarks"></a>Notes

La première fonction membre retourne le masque d’exception stocké. La deuxième fonction membre stocke *_Except* dans le masque d’exception et retourne sa précédente valeur stockée. Notez que le stockage d’un nouveau masque d’exception peut lever une exception, tout comme l’appel [clear](#clear)( [rdstate](#rdstate) ).

### <a name="example"></a>Exemple

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="basic_iosfail"></a><a name="fail"></a> basic_ios :: Fail

Indique l'échec de l'extraction d'un champ valide dans un flux.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si [rdstate](#rdstate) `& (badbit|failbit)` est différent de zéro ; sinon, **`false`** .

Pour plus d’informations sur `failbit`, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Exemple

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="basic_iosfill"></a><a name="fill"></a> basic_ios :: Fill

Spécifie ou retourne le caractère qui est utilisé quand le texte n'est pas aussi large que le flux.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Paramètres

*Char*\
Caractère souhaité comme caractère de remplissage.

### <a name="return-value"></a>Valeur renvoyée

Caractère de remplissage actuel.

### <a name="remarks"></a>Notes

La première fonction membre retourne le caractère de remplissage stocké. La deuxième fonction membre stocke *char* dans le caractère de remplissage et retourne sa valeur stockée précédente.

### <a name="example"></a>Exemple

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="basic_iosgood"></a><a name="good"></a> basic_ios :: Good

Indique que le flux est en bon état.

```cpp
bool good() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si [rdstate](#rdstate) `== goodbit` (aucun indicateur d’État n’est défini); sinon, **`false`** .

Pour plus d’informations sur `goodbit`, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Exemple

Consultez [basic_ios::bad](#bad) pour obtenir un exemple d’utilisation de `good`.

## <a name="basic_iosimbue"></a><a name="imbue"></a> basic_ios :: imbue

Change les paramètres régionaux.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Paramètres

*Loc*\
Chaîne de paramètres régionaux.

### <a name="return-value"></a>Valeur renvoyée

Paramètres régionaux précédents.

### <a name="remarks"></a>Notes

Si [rdbuf](#rdbuf) n’est pas un pointeur null, la fonction membre appelle

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

Dans tous les cas, elle retourne [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

### <a name="example"></a>Exemple

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="basic_iosinit"></a><a name="init"></a> basic_ios :: init

Appelé par les constructeurs de basic_ios.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Paramètres

*_Sb*\
Mémoire tampon standard pour stocker les éléments d’entrée ou de sortie.

*_Isstd*\
Spécifie s’il s’agit d’un flux standard.

### <a name="remarks"></a>Notes

La fonction membre stocke les valeurs de tous les objets membres, afin que :

- [rdbuf](#rdbuf) retourne *_Sb.*

- [tie](#tie) retourne un pointeur null.

- [rdstate](#rdstate) retourne [goodbit](../standard-library/ios-base-class.md#iostate) si *_Sb* est différent de zéro ; Sinon, elle retourne [badbit](../standard-library/ios-base-class.md#iostate).

- les [exceptions](#exceptions) sont retournées `goodbit` .

- [flags](../standard-library/ios-base-class.md#flags) retourne [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [width](../standard-library/ios-base-class.md#width) retourne 0.

- [precision](../standard-library/ios-base-class.md#precision) retourne 6.

- [fill](#fill) retourne l’espace.

- [getloc](../standard-library/ios-base-class.md#getloc) retourne `locale::classic`.

- [iword](../standard-library/ios-base-class.md#iword) retourne zéro et [pword](../standard-library/ios-base-class.md#pword) retourne un pointeur Null pour toutes les valeurs d’argument.

## <a name="basic_iosint_type"></a><a name="int_type"></a> basic_ios :: int_type

Synonyme de `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a> basic_ios :: Move

Déplace toutes les valeurs, sauf le pointeur vers la mémoire tampon du flux, du paramètre vers l'objet actuel.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `ios_base` à partir duquel déplacer les valeurs.

### <a name="remarks"></a>Notes

La fonction membre protégée déplace toutes les valeurs stockées à *droite* vers **`*this`** , à l’exception de l’élément stocké `stream buffer pointer` , qui n’est pas modifié à *droite* et qui a la valeur d’un pointeur null dans **`*this`** . Le stocké `tie pointer` est défini sur un pointeur null à *droite*.

## <a name="basic_iosnarrow"></a><a name="narrow"></a> basic_ios :: Narrow

Trouve le caractère équivalent à un type `char_type` donné.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Paramètres

*Char*\
**`char`** À convertir.

*Valeurs*\
**`char`** Que vous souhaitez retourner si aucun équivalent n’est trouvé.

### <a name="return-value"></a>Valeur renvoyée

Équivalent **`char`** à un donné `char_type` .

### <a name="remarks"></a>Notes

La fonction membre retourne [use_facet](../standard-library/basic-filebuf-class.md#open) \<ctype\<E> > ( [getloc](../standard-library/ios-base-class.md#getloc)()). `narrow` ( `Char`, `Default`).

### <a name="example"></a>Exemple

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="basic_iosoff_type"></a><a name="off_type"></a> basic_ios :: off_type

Synonyme de `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a> basic_ios :: Operator void *

Indique si le flux est toujours en bon état.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’opérateur retourne un pointeur null uniquement si [fail](#fail).

### <a name="example"></a>Exemple

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="basic_iosoperator"></a><a name="op_not"></a> basic_ios :: Operator !

Indique si le flux n'est pas en mauvais état.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne [fail](#fail).

### <a name="example"></a>Exemple

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a> basic_ios :: operator bool

Autorise l’utilisation d’un `basic_ios` objet en tant que **`bool`** . La conversion de type automatique est désactivée pour éviter des effets secondaires involontaires courants.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Notes

L’opérateur retourne une valeur convertible en **`false`** uniquement si `fail()` . Le type de retour est convertible uniquement en **`bool`** , pas en ou en un `void *` autre type scalaire connu.

## <a name="basic_iospos_type"></a><a name="pos_type"></a> basic_ios ::p os_type

Synonyme de `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a> basic_ios :: rdbuf

Dirige le flux vers la mémoire tampon spécifiée.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Paramètres

*_Sb*\
Un flux.

### <a name="remarks"></a>Notes

La première fonction membre retourne le pointeur de mémoire tampon de flux stocké.

La deuxième fonction membre stocke *_Sb* dans le pointeur de mémoire tampon de flux stocké et retourne la valeur précédemment stockée.

### <a name="example"></a>Exemple

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="basic_iosrdstate"></a><a name="rdstate"></a> basic_ios :: rdstate

Lit l'état des bits pour les indicateurs.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Valeur renvoyée

Informations de l’état de flux stocké.

### <a name="example"></a>Exemple

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="basic_iossetstate"></a><a name="setstate"></a> basic_ios :: SetState

Définit des indicateurs supplémentaires.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Paramètres

*_State*\
Indicateurs supplémentaires à définir.

### <a name="remarks"></a>Notes

La fonction membre appelle [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).

### <a name="example"></a>Exemple

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a> basic_ios :: set_rdbuf

Affecte une mémoire tampon de flux comme mémoire tampon de lecture pour cet objet de flux.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Paramètres

*strbuf*\
Mémoire tampon de flux qui doit devenir la mémoire tampon de lecture.

### <a name="remarks"></a>Notes

La fonction membre protégée stocke *strbuf* dans le `stream buffer pointer` . Elle n’appelle pas `clear` .

## <a name="basic_iostie"></a><a name="tie"></a> basic_ios :: tie

Garantit qu'un flux est traité avant un autre flux.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Un flux.

### <a name="return-value"></a>Valeur renvoyée

La première fonction membre retourne le pointeur de lien stocké. La deuxième fonction membre stocke *Str* dans le pointeur de liaison et retourne sa valeur stockée précédente.

### <a name="remarks"></a>Notes

`tie` entraîne la synchronisation de deux flux, de sorte que les opérations sur un flux se produisent après la fin des opérations sur l’autre flux.

### <a name="example"></a>Exemple

Dans cet exemple, en liant cin à cout, vous garantissez que la chaîne « Entrer un nombre : » est transmise à la console avant que le nombre soit extrait de cin. De cette façon, vous évitez que la chaîne « Entrer un nombre : » reste dans la mémoire tampon pendant la lecture du nombre et vous êtes sûr que l’utilisateur est invité à répondre à des invites. Par défaut, cin et cout sont liés.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="basic_iostraits_type"></a><a name="traits_type"></a> basic_ios :: traits_type

Synonyme pour le paramètre du modèle `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a> basic_ios :: Widening

Recherche l’équivalent `char_type` d’un donné **`char`** .

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Paramètres

*Char*\
Caractère à convertir.

### <a name="return-value"></a>Valeur renvoyée

Recherche l’équivalent `char_type` d’un donné **`char`** .

### <a name="remarks"></a>Notes

La fonction membre retourne [use_facet](../standard-library/basic-filebuf-class.md#open) <  **CType** \< **E**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

### <a name="example"></a>Exemple

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="basic_iosswap"></a><a name="swap"></a> basic_ios :: swap

Échange les valeurs de cet objet `basic_ios` avec celles d'un autre objet `basic_ios`. Toutefois, les pointeurs vers les mémoires tampons de flux ne sont pas échangés.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `basic_ios` utilisé pour échanger des valeurs.

### <a name="remarks"></a>Notes

La fonction membre protégée échange toutes les valeurs stockées dans *Right* avec **`*this`** , à l’exception du stocké `stream buffer pointer` .

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
