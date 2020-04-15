---
title: basic_filebuf, classe
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376880"
---
# <a name="basic_filebuf-class"></a>basic_filebuf, classe

Décrit un tampon de flux qui contrôle la transmission d’éléments de type *Char_T*, dont les traits de caractère sont déterminés par la classe *Tr*, à et à partir d’une séquence d’éléments stockés dans un fichier externe.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Paramètres

*Char_T*\
Élément de base de la mémoire tampon de fichier.

*Tr*\
Les traits de l’élément de `char_traits<Char_T>`base du tampon de fichier (généralement ).

## <a name="remarks"></a>Notes

Le modèle de classe décrit un tampon de flux qui contrôle la transmission d’éléments de type *Char_T*, dont les traits de caractère sont déterminés par la classe *Tr*, à et à partir d’une séquence d’éléments stockés dans un fichier externe.

> [!NOTE]
> Les objets `basic_filebuf` de type sont créés avec `char_type` un tampon interne de type __char\* __ indépendamment du paramètre spécifié par le type *Char_T*. Cela signifie qu’une chaîne Unicode (contenant **wchar_t** caractères) sera convertie en chaîne ANSI (contenant des **caractères d’omble)** avant d’être écrite au tampon interne. Pour stocker les chaînes Unicode dans le tampon, créez un nouveau tampon [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` de type **wchar_t** et définissez-le en utilisant la méthode. Pour obtenir un exemple qui illustre ce comportement, voir ci-dessous.

Un objet `basic_filebuf<Char_T, Tr>` de classe stocke un `FILE` pointeur de fichier, qui désigne l’objet qui contrôle le flux associé à un fichier ouvert. Il stocke également des pointeurs vers deux facettes de conversion de fichier utilisables par les fonctions membres protégées [overflow](#overflow) et [underflow](#underflow). Pour plus d’informations, consultez [`basic_filebuf::open`](#open).

## <a name="example"></a>Exemple

L'exemple suivant montre comment forcer un objet de type `basic_filebuf<wchar_t>` à stocker des caractères Unicode dans sa mémoire tampon interne en appelant la méthode `pubsetbuf()`.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_filebuf](#basic_filebuf)|Construit un objet de type `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Associe un nom de type au paramètre de modèle `Char_T`.|
|[int_type](#int_type)|Rend ce type dans la portée de `basic_filebuf` équivalent au type du même nom dans la portée de `Tr`.|
|[off_type](#off_type)|Rend ce type dans la portée de `basic_filebuf` équivalent au type du même nom dans la portée de `Tr`.|
|[pos_type](#pos_type)|Rend ce type dans la portée de `basic_filebuf` équivalent au type du même nom dans la portée de `Tr`.|
|[traits_type](#traits_type)|Associe un nom de type au paramètre de modèle `Tr`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Proche](#close)|Ferme un fichier.|
|[is_open](#is_open)|Indique si un fichier est ouvert.|
|[open](#open)|Ouvre un fichier.|
|[Débordement](#overflow)|Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.|
|[pbackfail](#pbackfail)|La fonction membre virtuelle protégée tente de remettre un élément dans le flux d'entrée, puis d'en faire l'élément actif (vers lequel pointe le pointeur suivant).|
|[seekoff](#seekoff)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[seekpos](#seekpos)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[setbuf](#setbuf)|La fonction membre virtuelle protégée effectue une opération spécifique à chaque mémoire tampon de flux dérivée.|
|[Swap](#swap)|Échange le contenu de ce `basic_filebuf` avec le contenu du paramètre `basic_filebuf` fourni.|
|[Synchronisation](#sync)|La fonction virtuelle protégée tente de synchroniser les flux contrôlés avec n’importe quel flux externe associé.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Fonction virtuelle protégée pour extraire l'élément actif du flux d'entrée.|
|[underflow](#underflow)|Fonction virtuelle protégée pour extraire l'élément actif du flux d'entrée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<fstream>

**Espace de noms :** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf::basic_filebuf

Construit un objet de type `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Notes

Le premier constructeur stocke un pointeur null dans tous les pointeurs contrôlant la mémoire tampon d’entrée et la mémoire tampon de sortie. Il stocke également un pointeur null dans le pointeur de fichier.

Le deuxième constructeur initialise l’objet avec le contenu du *droit,* traité comme une référence rvalue.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf::char_type

Associe un nom de type au paramètre de modèle `Char_T`.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf::fermer

Ferme un fichier.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne un pointeur null si le pointeur de fichier est un pointeur null.

### <a name="remarks"></a>Notes

`close` appelle `fclose(fp)`. Si cette fonction retourne une valeur différente de zéro, la fonction retourne un pointeur null. Sinon, elle retourne **this** pour indiquer que le fichier a été fermé.

Pour un large flux, si des insertions ont eu lieu depuis `streampos`l’ouverture [`overflow`](#overflow)du flux, ou depuis le dernier appel à , la fonction appelle . Il insère également toute séquence nécessaire pour restaurer l’état `fac` de `fac.unshift` conversion initial, en utilisant la facette de conversion de fichier pour appeler au besoin. Chaque élément `byte` produit de l’omble de type `fp` est écrit au flux `fputc(byte, fp)`associé désigné par le pointeur de fichier comme par des appels successifs du formulaire . **char** Si l’appel ou une `fac.unshift` écriture échoue, la fonction ne réussit pas.

### <a name="example"></a>Exemple

L’échantillon suivant suppose deux fichiers dans l’annuaire actuel : *basic_filebuf_close.txt* (le contenu est "test") et *iotest.txt* (le contenu est "sss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf::int_type

Rend ce `basic_filebuf` type dans une portée équivalente `Tr` au type du même nom dans la portée.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf::is_open

Indique si un fichier est ouvert.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valeur de retour

**vrai** si le pointeur de fichier n’est pas nul.

### <a name="example"></a>Exemple

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf::off_type

Rend ce `basic_filebuf` type dans une portée équivalente `Tr` au type du même nom dans la portée.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf::ouvert

Ouvre un fichier.

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>Paramètres

*Fichier*\
Nom du fichier à ouvrir.

*Mode*\
L’un des énumérations dans [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode).

*Protection*\
La protection d’ouverture de fichier par défaut, équivalente au paramètre *shflag* dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Valeur de retour

Si le tampon est déjà ouvert, ou si le pointeur de fichier est un pointeur nul, la fonction renvoie un pointeur nul. Sinon, elle retourne **this**.

### <a name="remarks"></a>Notes

La fonction membre ouvre le fichier avec [`fopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)` *nom nom,* en appelant . `strmode`est déterminé `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)`à partir de :

- `ios_base::in`devient `"r"` (fichier existant ouvert pour la lecture).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) or `ios_base::out | ios_base::trunc` becomes `"w"` (tronquer le fichier existant ou créer pour l’écriture).

- `ios_base::out | app`devient `"a"` (fichier existant ouvert pour appending tous les écrits).

- `ios_base::in | ios_base::out`devient `"r+"` (fichier existant ouvert pour la lecture et l’écriture).

- `ios_base::in | ios_base::out | ios_base::trunc`devient `"w+"` (tronquer le fichier existant ou créer pour la lecture et l’écriture).

- `ios_base::in | ios_base::out | ios_base::app`devient `"a+"` (fichier existant ouvert pour la lecture et pour l’appending tous les écrits).

S’il `mode & ios_base::binary` n’est pas zéro, la fonction `b` s’engage à `strmode` ouvrir un flux binaire au lieu d’un flux de texte. Il stocke ensuite `fopen` la valeur `fp`retournée dans le pointeur de fichier . S’il `mode & ios_base::ate` n’est pas zéro et que le pointeur de fichier n’est pas un pointeur nul, la fonction appelle `fseek(fp, 0, SEEK_END)` à positionner le flux à la fin du fichier. Si cette opération de positionnement [`close`](#close) `(fp)` échoue, la fonction appelle et stocke un pointeur nul dans le pointeur de fichier.

Si le pointeur de fichier n’est pas un pointeur `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)`nul, la fonction détermine la facette de conversion de fichier : , pour l’utilisation par [le sous-flux](#underflow) et [le débordement.](#overflow)

Si le pointeur de fichier est un pointeur null, la fonction membre retourne un pointeur null. Sinon, elle retourne **this**.

### <a name="example"></a>Exemple

Voir [`basic_filebuf::close`](#close) par exemple `open`qui utilise .

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf::opérateur

Affecter le contenu de cet objet de mémoire tampon de flux. Il s’agit d’une affectation de déménagement impliquant une rvalue qui ne laisse pas une copie derrière.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence rvalue à un objet [basic_filebuf](../standard-library/basic-filebuf-class.md).

### <a name="return-value"></a>Valeur de retour

Retours __-ceci__.

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet en utilisant le contenu du *droit,* traité comme une référence rvalue. Pour plus d’informations, voir [Rvalue reference declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf::débordement

Appelé quand un nouveau caractère est inséré dans une mémoire tampon saturée.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Le personnage à insérer dans le tampon ou `traits_type::eof`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut `traits_type::eof`pas réussir, elle revient . Sinon, il `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`revient .

### <a name="remarks"></a>Notes

Si `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), la fonction de membre `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` virtuel protégé tente d’insérer l’élément dans le tampon de sortie. Elle peut le faire de différentes manières :

- Si une position d’écriture est disponible, elle peut stocker l’élément dans la position d’écriture et incrémenter le pointeur suivant pour la mémoire tampon de sortie.

- Elle peut rendre disponible une position d’écriture en allouant du stockage nouveau ou supplémentaire à la mémoire tampon de sortie.

- Il peut convertir n’importe quelle sortie `ch`en attente dans le `fac` tampon `fac.out` de sortie, suivie par , en utilisant la facette de conversion de fichier pour appeler au besoin. Chaque élément `ch` produit de l’omble de type `fp` est écrit au flux `fputc(ch, fp)`associé désigné par le pointeur de fichier comme par des appels successifs du formulaire . *char* Si une conversion ou écriture échoue, la fonction échoue.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::pbackfail

Tente de remettre un élément dans le flux d’entrée, puis d’en faire l’élément actuel (désigné par le pointeur suivant).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon, ou `traits_type::eof`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut `traits_type::eof`pas réussir, elle revient . Sinon, il `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`revient .

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée remet un élément dans la mémoire tampon d’entrée, puis en fait l’élément actuel (désigné par le pointeur suivant). Si `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), l’élément à repousser est effectivement celui déjà dans le flux avant l’élément actuel. Sinon, cet élément `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)`est remplacé par . La fonction peut replacer un élément de différentes manières :

- Si `putback` une position est disponible, et l’élément stocké il se compare à égal à `ch`, il peut décroisser le pointeur suivant pour le tampon d’entrée.

- Si la fonction `putback` peut rendre une position disponible, elle peut le faire, `ch` définir le pointeur suivant pour pointer à cette position, et stocker dans cette position.

- Si la fonction peut repousser un élément sur le flux d’entrée, elle peut le faire, par exemple en appelant `ungetc` à un élément de type **char**.

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::pos-type

Rend ce `basic_filebuf` type dans une portée équivalente `Tr` au type du même nom dans la portée.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf::seekoff

Tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Off*\
La position à rechercher par rapport à *_Way*.

*_Way*\
Point de départ des opérations de décalage. Consultez [seekdir](../standard-library/ios-base-class.md#seekdir) pour connaître les valeurs possibles.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle position ou une position de flux non valide.

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée tente de modifier les positions actuelles pour les flux contrôlés. Pour un objet [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`de classe, une position de flux `fpos_t`peut être représentée par un objet de type , qui stocke un décalage et toute information d’état nécessaire pour analyser un large flux. Décalage zéro se réfère au premier élément du flux. (Un objet [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) de type `fpos_t` stocke au moins un objet.)

Dans le cas d’un fichier ouvert pour lecture et écriture, les flux d’entrée et de sortie sont positionnés en tandem. Pour passer de l’insertion et de [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)l’extraction, vous devez appeler l’un ou l’autre ou . Appels `pubseekoff` à (et `seekoff`donc à ) ont diverses limitations pour les [flux de texte](../c-runtime-library/text-and-binary-streams.md), flux [binaires](../c-runtime-library/text-and-binary-streams.md), et [de larges flux](../c-runtime-library/byte-and-wide-streams.md).

Si le `fp` pointeur de fichier est un pointeur nul, la fonction échoue. Sinon, il tente de modifier `fseek(fp, _Off, _Way)`la position du flux en appelant . Si cette fonction réussit `fposn` et que la `fgetpos(fp, &fposn)`position qui en résulte peut être déterminée en appelant, la fonction réussit. Si la fonction réussit, elle `pos_type` renvoie une valeur de type contenant `fposn`. Sinon, elle retourne une position de flux non valide.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf::seekpos

Tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Sp*\
Position à rechercher.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur de retour

Si le `fp` pointeur de fichier est un pointeur nul, la fonction échoue. Sinon, il tente de modifier `fsetpos(fp, &fposn)`la `fposn` position `fpos_t` du flux `pos`en appelant , où est l’objet stocké dans . Si la fonction réussit, elle retourne `pos`. Sinon, elle retourne une position de flux non valide. Pour déterminer si la position du flux n’est pas valide, comparez la valeur de retour à `pos_type(off_type(-1))`.

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée tente de modifier les positions actuelles pour les flux contrôlés. Pour un objet [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`de classe, une position de flux `fpos_t`peut être représentée par un objet de type , qui stocke un décalage et toute information d’état nécessaire pour analyser un large flux. Décalage zéro se réfère au premier élément du flux. (Un objet de type `pos_type` stocke au moins un objet `fpos_t`.)

Dans le cas d’un fichier ouvert pour lecture et écriture, les flux d’entrée et de sortie sont positionnés en tandem. Pour passer de l’insertion et de [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)l’extraction, vous devez appeler l’un ou l’autre ou . Appels `pubseekoff` à (et à `seekoff`) ont diverses limitations pour les flux de texte, les flux binaires, et les flux larges.

Pour un flux large, si des insertions se sont produites depuis l’ouverture du flux ou depuis le dernier appel à `streampos`, la fonction appelle [overflow](#overflow). Il insère également toute séquence nécessaire pour restaurer l’état `fac` de `fac.unshift` conversion initial, en utilisant la facette de conversion de fichier pour appeler au besoin. Chaque élément `byte` produit de l’omble de type `fp` est écrit au flux `fputc(byte, fp)`associé désigné par le pointeur de fichier comme par des appels successifs du formulaire . **char** Si l’appel ou une `fac.unshift` écriture échoue, la fonction ne réussit pas.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf::setbuf

Effectue une opération spécifique pour chaque mémoire tampon de flux dérivée.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*_Buffer*\
Pointeur vers une mémoire tampon.

*Compter*\
Taille de la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

La fonction membre protégée retourne un zéro si le pointeur de fichier `fp` est un pointeur null.

### <a name="remarks"></a>Notes

`setbuf`d’offrir `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` la `count` gamme d’éléments à partir *de _Buffer* comme tampon pour le flux. Si cette fonction retourne une valeur différente de zéro, la fonction retourne un pointeur null. Sinon, elle retourne **this** pour signaler la réussite.

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf::swap

Échange le contenu de ce `basic_filebuf` avec le contenu du `basic_filebuf` fourni.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Une référence lvalue `basic_filebuf`à un autre .

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf::sync

Tente de synchroniser les flux contrôlés avec n’importe quel flux externe associé.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Valeur de retour

Retourne zéro si `fp` le pointeur de fichier est un pointeur nul. Dans le cas contraire, il ne `fflush(fp)` renvoie zéro que si les appels à la fois [déborder](#overflow) et réussir à rincer toute sortie en attente sur le flux.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf::traits_type

Associe un nom de type au paramètre de modèle `Tr`.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf::underflow

Extrait l’élément actuel du flux d’entrée.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)pas réussir, elle revient . Sinon, il `ch`revient , converti comme décrit dans la section Remarques.

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée `ch` tente d’extraire l’élément actuel du flux d’entrée, et de retourner l’élément comme `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)`. Elle peut le faire de différentes manières :

- Si une position de lecture `ch` est disponible, elle prend l’élément stocké dans la position de lecture et avance le pointeur suivant pour le tampon d’entrée.

- Il peut lire un ou **char**plusieurs éléments de type char `fgetc(fp)`, comme par `ch` des appels successifs de la forme , et les convertir en un élément de type `Char_T` en utilisant la facette `fac` de conversion de fichier à appeler `fac.in` au besoin. En cas d’échec d’une conversion ou d’une lecture, la fonction échoue.

## <a name="see-also"></a>Voir aussi

[\<fstream>](../standard-library/fstream.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
