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
ms.openlocfilehash: 817e7fb2b434d06d6c0dfdfc100be8004f6fa4ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377148"
---
# <a name="basicfilebuf-class"></a>basic_filebuf, classe

Décrit une mémoire tampon de flux qui contrôle la transmission d’éléments de type *Elem*, dont les caractéristiques sont déterminées par la classe *Tr*, vers et à partir d’une séquence d’éléments stockés dans un fichier externe.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Elem*<br/>
Élément de base de la mémoire tampon de fichier.

*Tr*<br/>
Caractéristiques de l’élément de base de la mémoire tampon de fichier (généralement `char_traits`< `Elem`>).

## <a name="remarks"></a>Notes

La classe de modèle décrit une mémoire tampon de flux qui contrôle la transmission d’éléments de type *Elem*, dont les caractéristiques sont déterminées par la classe *Tr*, vers et à partir d’une séquence d’éléments stockés dans un fichier externe.

> [!NOTE]
> Objets de type `basic_filebuf` sont créés avec une mémoire tampon interne de type `char *` quel que soit le `char_type` spécifié par le paramètre de type *Elem*. Cela signifie qu’une chaîne Unicode (contenant **wchar_t** caractères) sera convertie en une chaîne ANSI (contenant **char** caractères) avant de les écrire dans la mémoire tampon interne. Pour stocker des chaînes Unicode dans la mémoire tampon, créez une nouvelle mémoire tampon de type **wchar_t** et définissez-la à l’aide du [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` (méthode). Pour obtenir un exemple qui illustre ce comportement, voir ci-dessous.

Un objet de classe `basic_filebuf`< `Elem`, `Tr`> stocke un pointeur de fichier qui désigne l’objet `FILE` qui contrôle le flux associé à un fichier ouvert. Il stocke également des pointeurs vers deux facettes de conversion de fichier utilisables par les fonctions membres protégées [overflow](#overflow) et [underflow](#underflow). Pour plus d’informations, consultez [basic_filebuf::open](#open).

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

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Associe un nom de type au paramètre de modèle `Elem`.|
|[int_type](#int_type)|Rend ce type dans la portée de `basic_filebuf` équivalent au type du même nom dans la portée de `Tr`.|
|[off_type](#off_type)|Rend ce type dans la portée de `basic_filebuf` équivalent au type du même nom dans la portée de `Tr`.|
|[pos_type](#pos_type)|Rend ce type dans la portée de `basic_filebuf` équivalent au type du même nom dans la portée de `Tr`.|
|[traits_type](#traits_type)|Associe un nom de type au paramètre de modèle `Tr`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[close](#close)|Ferme un fichier.|
|[is_open](#is_open)|Indique si un fichier est ouvert.|
|[open](#open)|Ouvre un fichier.|
|[overflow](#overflow)|Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.|
|[pbackfail](#pbackfail)|La fonction membre virtuelle protégée tente de remettre un élément dans le flux d'entrée, puis d'en faire l'élément actif (vers lequel pointe le pointeur suivant).|
|[seekoff](#seekoff)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[seekpos](#seekpos)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[setbuf](#setbuf)|La fonction membre virtuelle protégée effectue une opération spécifique à chaque mémoire tampon de flux dérivée.|
|[Swap](#swap)|Échange le contenu de ce `basic_filebuf` avec le contenu du paramètre `basic_filebuf` fourni.|
|[sync](#sync)|La fonction virtuelle protégée tente de synchroniser les flux contrôlés avec n’importe quel flux externe associé.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Fonction virtuelle protégée pour extraire l'élément actif du flux d'entrée.|
|[underflow](#underflow)|Fonction virtuelle protégée pour extraire l'élément actif du flux d'entrée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<fstream>

**Espace de noms :** std

## <a name="basic_filebuf"></a>  basic_filebuf::basic_filebuf

Construit un objet de type `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Notes

Le premier constructeur stocke un pointeur null dans tous les pointeurs contrôlant la mémoire tampon d’entrée et la mémoire tampon de sortie. Il stocke également un pointeur null dans le pointeur de fichier.

Le deuxième constructeur initialise l’objet avec le contenu de `right`, traité comme une référence rvalue.

## <a name="char_type"></a>  basic_filebuf::char_type

Associe un nom de type au paramètre de modèle `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>  basic_filebuf::close

Ferme un fichier.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne un pointeur null si le pointeur de fichier est un pointeur null.

### <a name="remarks"></a>Notes

`close` appels `fclose`( **fp**). Si cette fonction retourne une valeur différente de zéro, la fonction retourne un pointeur null. Sinon, elle retourne **this** pour indiquer que le fichier a été fermé.

Pour un flux large, si des insertions se sont produites depuis l’ouverture du flux ou depuis le dernier appel à `streampos`, la fonction appelle [overflow](#overflow). Elle insère également toute séquence nécessaire pour restaurer l’état de conversion initial, en utilisant la facette de conversion de fichier `fac` pour appeler `fac.unshift` en fonction des besoins. Chaque élément `byte` de type **char** ainsi produit est écrit dans le flux associé désigné par le pointeur de fichier `fp` que par les appels successifs de la forme `fputc`( **octets**, **fp**). Si l’appel à `fac.unshift` ou toute écriture échoue, la fonction échoue.

### <a name="example"></a>Exemple

L’exemple suivant suppose deux fichiers dans le répertoire actif : basic_filebuf_close.txt (le contenu est « testing ») et iotest.txt (le contenu est « ssss »).

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

## <a name="int_type"></a>  basic_filebuf::int_type

Rend ce type dans la portée de basic_filebuf équivalent au type du même nom dans la `Tr` étendue.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>  basic_filebuf::is_open

Indique si un fichier est ouvert.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le pointeur de fichier n’est pas un pointeur null.

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

## <a name="off_type"></a>  basic_filebuf::off_type

Rend ce type dans la portée de basic_filebuf équivalent au type du même nom dans la `Tr` étendue.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>  basic_filebuf::open

Ouvre un fichier.

```cpp
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Paramètres

*_Filename*<br/>
Nom du fichier à ouvrir.

*_Mode*<br/>
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Le fichier par défaut ouverture de protection, équivalente à la *shflag* paramètre dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Valeur de retour

Si le pointeur de fichier est un pointeur null, la fonction membre retourne un pointeur null. Sinon, elle retourne **this**.

### <a name="remarks"></a>Notes

La fonction membre ouvre le fichier dont le nom est *filename* en appelant [fopen](../c-runtime-library/reference/fopen-wfopen.md)(*filename*, **strmode**). `strmode` est déterminé à partir de **mode &**~ ( [ate](../standard-library/ios-base-class.md#openmode) & &#124; [binaire](../standard-library/ios-base-class.md#openmode)) :

- `ios_base::in` devient **« r »** (ouvrir le fichier existant pour lecture).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) ou **ios_base::out &#124; ios_base::trunc** devient **"w"** (tronquer le fichier existant ou créer un fichier pour écriture).

- **ios_base::out &#124; app** devient **"a"** (ouvrir le fichier existant pour ajouter toutes les écritures).

- **ios_base::in &#124; ios_base::out** devient **"r+"** (ouvrir le fichier existant pour lecture et écriture).

- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** devient **"w+"** (tronquer le fichier existant ou créer un fichier pour lecture et écriture).

- **ios_base::in &#124; ios_base::out &#124; ios_base::app** devient **"a+"** (ouvrir le fichier existant pour lecture et pour ajouter toutes les écritures).

Si **mode & ios_base::binary** est différent de zéro, la fonction ajoute `b` à `strmode` pour ouvrir un flux binaire au lieu d’un flux de texte. Il stocke ensuite la valeur retournée par `fopen` dans le pointeur de fichier `fp`. Si **mode & ios_base::ate** est différent de zéro et que le pointeur de fichier n’est pas null, la fonction appelle `fseek`(**fp**, 0, `SEEK_END`) pour positionner le flux à la fin du fichier. Si cette opération de positionnement échoue, les appels de fonction [fermer](#close)( `fp`) et stocke un pointeur null dans le pointeur de fichier.

Si le pointeur de fichier n’est pas un pointeur null, la fonction détermine la facette de conversion de fichier : `use_facet`< `codecvt`< **Elem**, `char`, **traits_type ::**[state_type](../standard-library/char-traits-struct.md#state_type)>> ( [getloc](../standard-library/basic-streambuf-class.md#getloc)), pour une utilisation par [dépassement de capacité négatif](#underflow) et [dépassement de capacité](#overflow).

Si le pointeur de fichier est un pointeur null, la fonction membre retourne un pointeur null. Sinon, elle retourne **this**.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](#close) pour obtenir un exemple d’utilisation de `open`.

## <a name="op_eq"></a>  basic_filebuf::operator=

Affecter le contenu de cet objet de mémoire tampon de flux. Il s'agit d'une assignation de déplacement qui implique une rvalue qui ne laisse pas de copie.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Référence rvalue à un objet [basic_filebuf](../standard-library/basic-filebuf-class.md).

### <a name="return-value"></a>Valeur de retour

Retourne *this.

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet en utilisant le contenu de *droit*, traité comme une référence rvalue. Pour plus d'informations, consultez [Déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>  basic_filebuf::overflow

Appelé quand un nouveau caractère est inséré dans une mémoire tampon saturée.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Paramètres

*_Meta*<br/>
Caractère à insérer dans la mémoire tampon ou `traits_type::eof`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `traits_type::eof`. Sinon, elle retourne **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Notes

Si *_Meta* **! = traits_type ::**[eof](../standard-library/char-traits-struct.md#eof), la fonction membre virtuelle protégée s’efforce d’insérer l’élément **ch = traits_type ::** [ to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*_Meta*) dans la mémoire tampon de sortie. Elle peut le faire de différentes manières :

- Si une position d’écriture est disponible, elle peut stocker l’élément dans la position d’écriture et incrémenter le pointeur suivant pour la mémoire tampon de sortie.

- Elle peut rendre disponible une position d’écriture en allouant du stockage nouveau ou supplémentaire à la mémoire tampon de sortie.

- Il peut convertir toute sortie en attente dans la mémoire tampon de sortie, suivie de `ch`, à l’aide de la facette de conversion de fichier `fac` pour appeler `fac.out` en fonction des besoins. Chaque élément `ch` de type *char* ainsi produit est écrit dans le flux associé désigné par le pointeur de fichier `fp` que par les appels successifs de la forme `fputc`( **ch**, **fp**). Si une conversion ou écriture échoue, la fonction échoue.

## <a name="pbackfail"></a>  basic_filebuf::pbackfail

Tente de remettre un élément dans le flux d’entrée, puis d’en faire l’élément actuel (désigné par le pointeur suivant).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Paramètres

*_Meta*<br/>
Caractère à insérer dans la mémoire tampon, ou `traits_type::eof`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `traits_type::eof`. Sinon, elle retourne **traits_type ::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(*\_Meta*).

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée remet un élément dans la mémoire tampon d’entrée, puis en fait l’élément actuel (désigné par le pointeur suivant). Si  *\_Meta* **== traits_type ::**[eof](../standard-library/char-traits-struct.md#eof), l’élément à remettre est celui déjà dans le flux avant l’élément actuel. Sinon, cet élément est remplacé par **ch = traits_type ::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*). La fonction peut replacer un élément de différentes manières :

- Si une position de remise est disponible, et l’élément stocké est égal à `ch`, elle peut décrémenter le pointeur suivant pour la mémoire tampon d’entrée.

- Si la fonction peut rendre un `putback` position disponible, il peut faire, définissez le pointeur suivant pour pointer vers cette position et stocker `ch` dans cette position.

- Si la fonction peut remettre un élément dans le flux d’entrée, il peut faire, par exemple en appelant `ungetc` pour un élément de type **char**.

## <a name="pos_type"></a>  basic_filebuf::pos_type

Rend ce type dans la portée de basic_filebuf équivalent au type du même nom dans la `Tr` étendue.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_filebuf::seekoff

Tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
La position à rechercher par rapport à *_Way*.

*_Way*<br/>
Point de départ des opérations de décalage. Consultez [seekdir](../standard-library/ios-base-class.md#seekdir) pour connaître les valeurs possibles.

*_Which*<br/>
Spécifie le mode pour la position du pointeur. Par défaut, vous êtes autorisé à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle position ou une position de flux non valide.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée s’efforce de modifier les positions actuelles des flux contrôlés. Pour un objet de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, une position de flux peut être représentée par un objet de type `fpos_t` qui stocke un décalage et toutes les informations d’état nécessaires pour analyser un flux large. Le décalage zéro désigne le premier élément du flux. (Un objet de type [pos_type](../standard-library/basic-streambuf-class.md#pos_type) stocke au moins un objet `fpos_t`.)

Dans le cas d’un fichier ouvert pour lecture et écriture, les flux d’entrée et de sortie sont positionnés en tandem. Pour basculer entre l’insertion et l’extraction, vous devez appeler [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) ou [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Les appels à `pubseekoff` (et donc à `seekoff`) ont plusieurs limites pour les [flux de texte](../c-runtime-library/text-and-binary-streams.md), les [flux binaires](../c-runtime-library/text-and-binary-streams.md) et les [flux larges](../c-runtime-library/byte-and-wide-streams.md).

Si le pointeur de fichier `fp` est un pointeur null, la fonction échoue. Sinon, elle s’efforce de modifier la position du flux en appelant `fseek`( **fp**, `_Off`, `_Way`). Si cette fonction réussit et la position résultante `fposn` peut être déterminée en appelant `fgetpos`( **fp**, **& fposn**), la fonction réussit. Si la fonction réussit, elle retourne une valeur de type `pos_type` contenant `fposn`. Sinon, elle retourne une position de flux non valide.

## <a name="seekpos"></a>  basic_filebuf::seekpos

Tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Sp*<br/>
Position à rechercher.

*_Which*<br/>
Spécifie le mode pour la position du pointeur. Par défaut, vous êtes autorisé à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur de retour

Si le pointeur de fichier `fp` est un pointeur null, la fonction échoue. Sinon, elle s’efforce de modifier la position du flux en appelant `fsetpos`( **fp**, **& fposn**), où `fposn` est la `fpos_t` objet stocké dans `pos`. Si la fonction réussit, elle retourne `pos`. Sinon, elle retourne une position de flux non valide. Pour déterminer si la position du flux est non valide, comparez la valeur de retour à `pos_type(off_type(-1))`.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée s’efforce de modifier les positions actuelles des flux contrôlés. Pour un objet de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, une position de flux peut être représentée par un objet de type `fpos_t` qui stocke un décalage et toutes les informations d’état nécessaires pour analyser un flux large. Le décalage zéro désigne le premier élément du flux. (Un objet de type `pos_type` stocke au moins un objet `fpos_t`.)

Dans le cas d’un fichier ouvert pour lecture et écriture, les flux d’entrée et de sortie sont positionnés en tandem. Pour basculer entre l’insertion et l’extraction, vous devez appeler [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) ou [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Les appels à `pubseekoff` (et donc à `seekoff`) ont plusieurs limites pour les flux de texte, les flux binaires et les flux larges.

Pour un flux large, si des insertions se sont produites depuis l’ouverture du flux ou depuis le dernier appel à `streampos`, la fonction appelle [overflow](#overflow). Elle insère également toute séquence nécessaire pour restaurer l’état de conversion initial, en utilisant la facette de conversion de fichier `fac` pour appeler **fac** `.unshift` en fonction des besoins. Chaque élément `byte` de type **char** ainsi produit est écrit dans le flux associé désigné par le pointeur de fichier `fp` que par les appels successifs de la forme `fputc`( **octets**, **fp**). Si l’appel à `fac.unshift` ou toute écriture échoue, la fonction échoue.

## <a name="setbuf"></a>  basic_filebuf::setbuf

Effectue une opération spécifique pour chaque mémoire tampon de flux dérivée.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*_Buffer*<br/>
Pointeur vers une mémoire tampon.

*count*<br/>
Taille de la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

La fonction membre protégée retourne un zéro si le pointeur de fichier `fp` est un pointeur null.

### <a name="remarks"></a>Notes

`setbuf` appelle `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**) ) pour présenter le tableau d’éléments `count` commençant par _ *Buffer* comme mémoire tampon pour le flux. Si cette fonction retourne une valeur différente de zéro, la fonction retourne un pointeur null. Sinon, elle retourne **this** pour signaler la réussite.

## <a name="swap"></a>  basic_filebuf::swap

Échange le contenu de ce `basic_filebuf` avec le contenu du `basic_filebuf` fourni.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Référence `lvalue` à un autre `basic_filebuf`.

## <a name="sync"></a>  basic_filebuf::sync

Tente de synchroniser les flux contrôlés avec n’importe quel flux externe associé.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Valeur de retour

Retourne zéro si le pointeur de fichier `fp` est un pointeur null. Sinon, elle retourne zéro uniquement si les appels à [overflow](#overflow) et `fflush`( **fp**) parviennent à vider toute sortie en attente dans le flux.

## <a name="traits_type"></a>  basic_filebuf::traits_type

Associe un nom de type au paramètre de modèle `Tr`.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>  basic_filebuf::underflow

Extrait l’élément actuel du flux d’entrée.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). Sinon, elle retourne `ch`, converti comme décrit dans la section Notes.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée s’efforce d’extraire l’élément actuel `ch` à partir de l’entrée de flux et retourne l’élément en tant que **traits_type ::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`ch`). Elle peut le faire de différentes manières :

- Si une position de lecture est disponible, elle accepte `ch` comme élément stocké dans la position de lecture et avance le pointeur suivant pour la mémoire tampon d’entrée.

- Elle peut lire un ou plusieurs éléments de type **char**, comme lors d’appels successifs de la forme `fgetc`(**fp**) et les convertir en un élément **ch** de type `Elem`en utilisant le fac de facette de conversion de fichier pour appeler `fac.in` en fonction des besoins. En cas d’échec d’une conversion ou d’une lecture, la fonction échoue.

## <a name="see-also"></a>Voir aussi

[\<fstream>](../standard-library/fstream.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
