---
title: basic_ios, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3abc3c08b46577f7d59b2831a68ded812a5da60a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110016"
---
# <a name="basicios-class"></a>basic_ios, classe

La classe de modèle décrit les fonctions membres et de stockage communes aux flux d’entrée (de classe de modèle [basic_istream](../standard-library/basic-istream-class.md)) et de sortie (de classe de modèle [basic_ostream](../standard-library/basic-ostream-class.md)) qui dépendent des paramètres de modèle. (La classe [ios_base](../standard-library/ios-base-class.md) décrit ce qui est commun et non dépendant des paramètres de modèle.) Un objet de classe **basic_ios\<class Elem, class Traits >** permet de contrôler un flux avec des éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Traits`.

## <a name="syntax"></a>Syntaxe

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Paramètres

*Elem*<br/>
Type.

*Caractéristiques*<br/>
Variable de type `char_traits`.

## <a name="remarks"></a>Notes

Un objet de classe **basic_ios\<class Elem, class Traits>** stocke :

- Un pointeur de lien vers un objet de type [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits>**.

- Un pointeur de mémoire tampon de flux vers un objet de type [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits>**.

- Des [informations sur la mise en forme](../standard-library/ios-base-class.md).

- Des [informations sur l’état du flux](../standard-library/ios-base-class.md) dans un objet de base de type [ios_base](../standard-library/ios-base-class.md).

- Un caractère de remplissage dans un objet de type `char_type`.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ios](#basic_ios)|Construit la classe `basic_ios`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Synonyme pour le paramètre du modèle `Elem`.|
|[int_type](#int_type)|Synonyme de `Traits::int_type`.|
|[off_type](#off_type)|Synonyme de `Traits::off_type`.|
|[pos_type](#pos_type)|Synonyme de `Traits::pos_type`.|
|[traits_type](#traits_type)|Synonyme pour le paramètre du modèle `Traits`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[bad](#bad)|Indique une perte d'intégrité de la mémoire tampon du flux.|
|[clear](#clear)|Efface tous les indicateurs d'erreur.|
|[copyfmt](#copyfmt)|Copie les indicateurs d'un flux vers un autre.|
|[eof](#eof)|Indique si la fin d'un flux a été atteinte.|
|[exceptions](#exceptions)|Indique les exceptions qui seront levées par le flux.|
|[fail](#fail)|Indique l'échec de l'extraction d'un champ valide dans un flux.|
|[fill](#fill)|Spécifie ou retourne le caractère qui est utilisé quand le texte n'est pas aussi large que le flux.|
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
|[opérateur explicite bool](#op_bool)|Autorise l’utilisation d’un `basic_ios` de l’objet comme un **bool**. La conversion de type automatique est désactivée pour éviter des effets secondaires involontaires courants.|
|[opérateur void *](#op_void_star)|Indique si le flux est toujours en bon état.|
|[operator!](#op_not)|Indique si le flux n'est pas en mauvais état.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<ios>

**Espace de noms :** std

## <a name="bad"></a>  basic_ios::bad

Indique une perte d’intégrité de la mémoire tampon de flux

```cpp
bool bad() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si `rdstate & badbit` est différente de zéro ; sinon **false**.

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

## <a name="basic_ios"></a>  basic_ios::basic_ios

Construit la classe basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Paramètres

*SB*<br/>
Mémoire tampon standard pour stocker les éléments d’entrée ou de sortie.

### <a name="remarks"></a>Notes

Le premier constructeur initialise ses objets membres en appelant [init](#init)(_ *Sb*). Le deuxième constructeur (protégé) laisse ses objets membres non initialisés. Un appel ultérieur à `init` doit initialiser l’objet avant qu’il puisse être détruit en toute sécurité.

## <a name="char_type"></a>  basic_ios::char_type

Synonyme pour le paramètre du modèle `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="clear"></a>  basic_ios::clear

Efface tous les indicateurs d'erreur.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Paramètres

*état* (facultatif) les indicateurs que vous souhaitez définir après l’effacement de tous les indicateurs. La valeur par défaut est `goodbit`.

*reraise* (facultatif) Spécifie si l’exception doit être levée de nouveau. Valeur par défaut est **false** (ne sera pas levée de nouveau l’exception).

### <a name="remarks"></a>Notes

Les indicateurs sont `goodbit`, `failbit`, `eofbit`, et `badbit`. Testez ces indicateurs avec [good](#good), [bad](#bad), [eof](#eof) et [fail](#fail)

La fonction membre remplace les informations d'état de flux stockées par :

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Si `state`**&**[exceptions](#exceptions) est différent de zéro, un objet de la classe [failure](../standard-library/ios-base-class.md#failure) est levé.

### <a name="example"></a>Exemple

Consultez [rdstate](#rdstate) et [getline](../standard-library/string-functions.md#getline) pour obtenir des exemples à l’aide de `clear`.

## <a name="copyfmt"></a>  basic_ios::copyfmt

Copie les indicateurs d'un flux vers un autre.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Flux dont vous voulez copier les indicateurs.

### <a name="return-value"></a>Valeur de retour

Objet **this** pour le flux dans lequel vous copiez les indicateurs.

### <a name="remarks"></a>Notes

La fonction membre signale l’événement de rappel **effacer\_événement**. Elle copie ensuite *droit* dans  **\*cela** le caractère de remplissage, le pointeur de lien et les informations de mise en forme. Avant de modifier le masque d’exception, il signale l’événement de rappel `copyfmt_event`. Si, une fois que la copie est terminée, **state &**[exceptions](#exceptions) est différent de zéro, la fonction appelle [clear](#clear) avec l’argument [rdstate](#rdstate). Elle retourne ensuite **\*this**.

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

## <a name="eof"></a>  basic_ios::eof

Indique si la fin d'un flux a été atteinte.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si la fin du flux a été atteinte, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

La fonction membre retourne **true** si [rdstate](#rdstate) `& eofbit` est différent de zéro. Pour plus d’informations sur `eofbit`, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

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

## <a name="exceptions"></a>  basic_ios::exceptions

Indique les exceptions qui seront levées par le flux.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Paramètres

*Newexcept*<br/>
Indicateurs pour lesquels vous voulez lever une exception.

### <a name="return-value"></a>Valeur de retour

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

## <a name="fail"></a>  basic_ios::fail

Indique l'échec de l'extraction d'un champ valide dans un flux.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si [rdstate](#rdstate) `& (badbit|failbit)` est différent de zéro, sinon **false**.

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

## <a name="fill"></a>  basic_ios::fill

Spécifie ou retourne le caractère qui est utilisé quand le texte n'est pas aussi large que le flux.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Paramètres

*Char*<br/>
Caractère souhaité comme caractère de remplissage.

### <a name="return-value"></a>Valeur de retour

Caractère de remplissage actuel.

### <a name="remarks"></a>Notes

La première fonction membre retourne le caractère de remplissage stocké. La deuxième fonction membre stocke *Char* dans le caractère de remplissage et retourne sa précédente valeur stockée.

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

## <a name="good"></a>  basic_ios::good

Indique que le flux est en bon état.

```cpp
bool good() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si [rdstate](#rdstate) `== goodbit` (aucun indicateur d’état n’est définis), sinon, **false**.

Pour plus d’informations sur `goodbit`, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Exemple

Consultez [basic_ios::bad](#bad) pour obtenir un exemple d’utilisation de `good`.

## <a name="imbue"></a>  basic_ios::imbue

Change les paramètres régionaux.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Paramètres

*Loc*<br/>
Chaîne de paramètres régionaux.

### <a name="return-value"></a>Valeur de retour

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

## <a name="init"></a>  basic_ios::init

Appelé par les constructeurs de basic_ios.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Paramètres

*_Sb*<br/>
Mémoire tampon standard pour stocker les éléments d’entrée ou de sortie.

*_Isstd*<br/>
Spécifie s’il s’agit d’un flux standard.

### <a name="remarks"></a>Notes

La fonction membre stocke les valeurs de tous les objets membres, afin que :

- [rdbuf](#rdbuf) retourne *_Sb.*

- [tie](#tie) retourne un pointeur null.

- [rdstate](#rdstate) retourne [goodbit](../standard-library/ios-base-class.md#iostate) si *_Sb* est différent de zéro ; sinon, elle retourne [badbit](../standard-library/ios-base-class.md#iostate).

- [exceptions](#exceptions) retourne `goodbit`.

- [flags](../standard-library/ios-base-class.md#flags) retourne [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).

- [width](../standard-library/ios-base-class.md#width) retourne 0.

- [precision](../standard-library/ios-base-class.md#precision) retourne 6.

- [fill](#fill) retourne l’espace.

- [getloc](../standard-library/ios-base-class.md#getloc) retourne `locale::classic`.

- [iword](../standard-library/ios-base-class.md#iword) retourne zéro et [pword](../standard-library/ios-base-class.md#pword) retourne un pointeur Null pour toutes les valeurs d’argument.

## <a name="int_type"></a>  basic_ios::int_type

Synonyme de `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="move"></a>  basic_ios::move

Déplace toutes les valeurs, sauf le pointeur vers la mémoire tampon du flux, du paramètre vers l'objet actuel.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Objet `ios_base` à partir duquel déplacer les valeurs.

### <a name="remarks"></a>Notes

La fonction membre protégée déplace toutes les valeurs stockées dans *droit* à `*this` sauf stocké `stream buffer pointer`, ce qui n’est pas modifié dans *droit* et la valeur est un pointeur null dans `*this`. Stocké `tie pointer` est défini sur un pointeur null dans *droit*.

## <a name="narrow"></a>  basic_ios::narrow

Trouve le caractère équivalent à un type `char_type` donné.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Paramètres

*Char*<br/>
Le **char** à convertir.

*Default*<br/>
Le **char** à retourné si aucun équivalent n’est trouvé.

### <a name="return-value"></a>Valeur de retour

L’équivalent **char** à une donnée `char_type`.

### <a name="remarks"></a>Notes

La fonction membre retourne [use_facet](../standard-library/basic-filebuf-class.md#open)\<ctype\<E >> ( [getloc](../standard-library/ios-base-class.md#getloc)()).`narrow` ( `Char`, `Default`).

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

## <a name="off_type"></a>  basic_ios::off_type

Synonyme de `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_void_star"></a>  basic_ios::operator void *

Indique si le flux est toujours en bon état.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Valeur de retour

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

## <a name="op_not"></a>  basic_ios::operator!

Indique si le flux n'est pas en mauvais état.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Valeur de retour

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

## <a name="op_bool"></a>  basic_ios::operator bool

Autorise l’utilisation d’un `basic_ios` de l’objet comme un **bool**. La conversion de type automatique est désactivée pour éviter des effets secondaires involontaires courants.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Notes

L’opérateur retourne une valeur convertible en **false** uniquement si `fail()`. Le type de retour est convertible uniquement en **bool**et non en `void *` ou autre type scalaire connu.

## <a name="pos_type"></a>  basic_ios::pos_type

Synonyme de `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="rdbuf"></a>  basic_ios::rdbuf

Dirige le flux vers la mémoire tampon spécifiée.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Paramètres

*_Sb*<br/>
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

## <a name="rdstate"></a>  basic_ios::rdstate

Lit l'état des bits pour les indicateurs.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Valeur de retour

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

## <a name="setstate"></a>  basic_ios::setstate

Définit des indicateurs supplémentaires.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
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

## <a name="set_rdbuf"></a>  basic_ios::set_rdbuf

Affecte une mémoire tampon de flux comme mémoire tampon de lecture pour cet objet de flux.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Paramètres

*strbuf*<br/>
Mémoire tampon de flux qui doit devenir la mémoire tampon de lecture.

### <a name="remarks"></a>Notes

La fonction membre protégée stocke *strbuf* dans le `stream buffer pointer`. Il n’appelle pas `clear`.

## <a name="tie"></a>  basic_ios::tie

Garantit qu'un flux est traité avant un autre flux.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Un flux.

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne le pointeur de lien stocké. La deuxième fonction membre stocke *str* dans le pointeur de lien et retourne sa précédente valeur stockée.

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

## <a name="traits_type"></a>  basic_ios::traits_type

Synonyme pour le paramètre du modèle `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="widen"></a>  basic_ios::widen

Recherche l’équivalent `char_type` à une donnée **char**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Paramètres

*Char*<br/>
Caractère à convertir.

### <a name="return-value"></a>Valeur de retour

Recherche l’équivalent `char_type` à une donnée **char**.

### <a name="remarks"></a>Notes

La fonction membre retourne [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **E**> >( [getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).

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

## <a name="swap"></a>  basic_ios::swap

Échange les valeurs de cet objet `basic_ios` avec celles d'un autre objet `basic_ios`. Toutefois, les pointeurs vers les mémoires tampons de flux ne sont pas échangés.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Objet `basic_ios` utilisé pour échanger des valeurs.

### <a name="remarks"></a>Notes

La fonction membre protégée échange toutes les valeurs stockées dans *droit* avec `*this` sauf stocké `stream buffer pointer`.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
