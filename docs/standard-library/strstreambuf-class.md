---
title: strstreambuf, classe
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: 28399a1cd55407aadbc5d59e1e835892218ad0c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376611"
---
# <a name="strstreambuf-class"></a>strstreambuf, classe

Décrit un tampon de flux qui contrôle la transmission des éléments vers et à partir d’une séquence d’éléments stockés dans un objet de tableau **d’omble** chevalier.

## <a name="syntax"></a>Syntaxe

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>Notes

Selon la façon dont l'objet est construit, il peut être alloué, étendu et libéré en fonction des modifications apportées à la séquence.

Un objet de classe `strstreambuf` stocke plusieurs bits d'information de mode en tant que mode `strstreambuf`. Ces bits indiquent si la séquence contrôlée :

- a été allouée et doit être libérée par la suite ;

- est modifiable ;

- est extensible en réallouant le stockage ;

- a été figée et doit donc être défigée avant que l'objet soit détruit, ou libérée (si elle a été allouée) par une agence autre que l'objet.

Vous ne pouvez pas modifier ou étendre une séquence contrôlée figée, quel que soit l'état de ces bits de mode distincts.

L'objet stocke également des pointeurs vers deux fonctions qui contrôlent l'allocation de `strstreambuf`. Si ces pointeurs sont null, l'objet définit sa propre méthode d'allocation et de libération du stockage pour la séquence contrôlée.

> [!NOTE]
> Cette classe est déconseillée. Utilisez à la place [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) ou [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[strstreambuf](#strstreambuf)|Construit un objet de type `strstreambuf`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Gèlent](#freeze)|Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.|
|[Débordement](#overflow)|Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.|
|[pbackfail](#pbackfail)|Fonction membre virtuelle protégée qui tente de replacer un élément dans le flux d'entrée, puis d'en faire l'élément actif (vers lequel pointe le pointeur suivant).|
|[pcount](#pcount)|Retourne le nombre d'éléments écrits dans la séquence contrôlée.|
|[seekoff](#seekoff)|Fonction membre virtuelle protégée qui tente de modifier les positions actuelles des flux contrôlés.|
|[seekpos](#seekpos)|Fonction membre virtuelle protégée qui tente de modifier les positions actuelles des flux contrôlés.|
|[Str](#str)|Appelle [freeze](#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|
|[underflow](#underflow)|Fonction virtuelle protégée pour extraire l'élément actuel du flux d'entrée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<strstream>

**Espace de noms :** std

## <a name="strstreambuffreeze"></a><a name="freeze"></a>strstreambuf::gel

Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Paramètres

*_Freezeit*\
Un **bool** indiquant si vous voulez que le flux soit gelé.

### <a name="remarks"></a>Notes

Si *_Freezeit* est vrai, la fonction `strstreambuf` modifie le mode stocké pour que la séquence contrôlée soit gelée. Dans le cas contraire, elle rend la séquence contrôlée non gelée.

[str](#str) implique `freeze`.

> [!NOTE]
> Une mémoire tampon gelée n’est pas libérée pendant la destruction de `strstreambuf`. Vous devez dégeler la mémoire tampon avant de la libérer pour éviter une fuite de mémoire.

### <a name="example"></a>Exemple

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="strstreambufoverflow"></a><a name="overflow"></a>strstreambuf::débordement

Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon, ou `EOF`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `EOF`. Sinon, * \_* si Meta == `EOF`, il `EOF`retourne une certaine valeur autre que . Sinon, il * \_* retourne Meta .

### <a name="remarks"></a>Notes

Si * \_Meta* `EOF`! , la fonction de membre `(char)_Meta` virtuel protégée tente d’insérer l’élément dans le tampon de sortie. Elle peut le faire de différentes manières :

- Si une position d’écriture est disponible, elle peut stocker l’élément dans la position d’écriture et incrémenter le pointeur suivant pour la mémoire tampon de sortie.

- Si le mode strstreambuf stocké indique que la séquence contrôlée est modifiable, extensible et non gelée, la fonction peut proposer une position d’écriture en en allouant une nouvelle pour la mémoire tampon de sortie. Cette façon d’étendre la mémoire tampon de sortie permet également d’étendre les mémoires tampons d’entrée associées.

## <a name="strstreambufpbackfail"></a><a name="pbackfail"></a>strstreambuf::pbackfail

Fonction membre virtuelle protégée qui tente de replacer un élément dans le flux d’entrée, puis d’en faire l’élément actif (vers lequel pointe le pointeur suivant).

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon, ou `EOF`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `EOF`. Sinon, * \_* si Meta == `EOF`, il `EOF`retourne une certaine valeur autre que . Sinon, il * \_* retourne Meta .

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée tente de replacer un élément dans la mémoire tampon d’entrée, puis d’en faire l’élément actif (vers lequel pointe le pointeur suivant).

Si * \_Meta* == `EOF`, l’élément à repousser est effectivement celui déjà dans le flux avant l’élément actuel. Sinon, cet élément `ch = (char)_Meta`est remplacé par . La fonction peut replacer un élément de différentes manières :

- Si une position de remise est disponible, et `ch`l’élément stocké il se compare à égal à , il peut décroisser le pointeur suivant pour le tampon d’entrée.

- Si une position de remise est disponible, et si le mode strstreambuf indique `ch` que la séquence contrôlée est modifiable, la fonction peut stocker dans la position de remise et décrérer le pointeur suivant pour le tampon d’entrée.

## <a name="strstreambufpcount"></a><a name="pcount"></a>strstreambuf::pcount

Retourne le nombre d'éléments écrits dans la séquence contrôlée.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valeur de retour

Un décompte du nombre d’éléments écrits dans la séquence contrôlée.

### <a name="remarks"></a>Notes

En particulier, si [pptr](../standard-library/basic-streambuf-class.md#pptr) est un pointeur Null, la fonction retourne zéro. Sinon, il `pptr`  - retourne [pbase](../standard-library/basic-streambuf-class.md#pbase).

### <a name="example"></a>Exemple

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="strstreambufseekoff"></a><a name="seekoff"></a>strstreambuf::seekoff

Fonction membre virtuelle protégée qui tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual streampos seekoff(streamoff _Off,
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

Si la fonction réussit à modifier une ou les deux positions de flux, elle retourne la position de flux obtenue. Sinon, elle échoue et retourne une position de flux non valide.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée s’efforce de modifier les positions actuelles des flux contrôlés. Pour un objet de classe strstreambuf, une position de flux se compose uniquement d’un décalage de flux. Le décalage zéro désigne le premier élément de la séquence contrôlée.

La nouvelle position est déterminée comme suit :

- Si `_Way == ios_base::beg`, la nouvelle position est le début du flux plus *_Off*.

- Si `_Way == ios_base::cur`, la nouvelle position est la position actuelle du flux plus *_Off*.

- Si `_Way == ios_base::end`, la nouvelle position est la fin du flux plus *_Off*.

S’il `_Which & ios_base::in` n’existe pas de tampon et que le tampon d’entrée existe, la fonction modifie la position suivante pour lire dans le tampon d’entrée. Si `_Which & ios_base::out` elle n’est `_Way != ios_base::cur`pas non zéro, et que le tampon de sortie existe, la fonction définit également la position suivante à écrire pour correspondre à la position suivante à lire.

Dans le cas contraire, si `_Which & ios_base::out` est différent de zéro et que la mémoire tampon de sortie existe, la fonction modifie la position suivante d’écriture dans la mémoire tampon de sortie. Dans le cas contraire, l’opération de positionnement échoue. Pour qu’une opération de positionnement réussisse, la position de flux obtenue doit se trouver dans la séquence contrôlée.

## <a name="strstreambufseekpos"></a><a name="seekpos"></a>strstreambuf::seekpos

Fonction membre virtuelle protégée qui tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Sp*\
Position à rechercher.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit à modifier une ou les deux positions de flux, elle retourne la position de flux obtenue. Sinon, elle échoue et retourne une position de flux non valide. Pour déterminer si la position du flux n’est pas valide, comparez la valeur de retour à `pos_type(off_type(-1))`.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée s’efforce de modifier les positions actuelles des flux contrôlés. Pour un objet de classe strstreambuf, une position de flux se compose uniquement d’un décalage de flux. Le décalage zéro désigne le premier élément de la séquence contrôlée. La nouvelle position est déterminée par *_Sp*.

Si `_Which` & **ios_base::in** est différent de zéro et que la mémoire tampon d’entrée existe, la fonction modifie la position suivante de lecture dans la mémoire tampon d’entrée. Si `_Which` & `ios_base::out` est différent de zéro et que la mémoire tampon de sortie existe, la fonction définit également la position suivante d’écriture pour qu’elle corresponde à la position suivante de lecture. Dans le cas contraire, si `_Which` & `ios_base::out` est différent de zéro et que la mémoire tampon de sortie existe, la fonction modifie la position suivante d’écriture dans la mémoire tampon de sortie. Dans le cas contraire, l’opération de positionnement échoue. Pour qu’une opération de positionnement réussisse, la position de flux obtenue doit se trouver dans la séquence contrôlée.

## <a name="strstreambufstr"></a><a name="str"></a>strstreambuf::str

Appelle [freeze](#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

Aucun élément Null de fin n’existe, à moins que n’en insériez explicitement un.

### <a name="example"></a>Exemple

Consultez [strstreambuf::freeze](#freeze) pour obtenir un exemple qui utilise **str**.

## <a name="strstreambufstrstreambuf"></a><a name="strstreambuf"></a>strstreambuf::strstreambuf

Construit un objet de type `strstreambuf`.

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*_Allocfunc*\
Fonction utilisée pour allouer de la mémoire tampon.

*Compter*\
Détermine la longueur du tampon pointé vers *_Getptr*. Si *_Getptr n’est* pas un argument (premier formulaire constructeur), une taille d’allocation suggérée pour les tampons.

*_Freefunc*\
Fonction utilisée pour libérer de la mémoire tampon.

*_Getptr*\
Mémoire tampon utilisée pour l’entrée.

*_Putptr*\
Mémoire tampon utilisée pour la sortie.

### <a name="remarks"></a>Notes

Le premier constructeur stocke un pointeur Null dans tous les pointeurs contrôlant la mémoire tampon d’entrée, la mémoire tampon de sortie et l’allocation strstreambuf. Il définit le mode strstreambuf stocké pour rendre la séquence contrôlée modifiable et extensible. Il accepte également *le compte* comme une taille d’allocation initiale suggérée.

Le deuxième constructeur se comporte comme le premier, sauf qu’il stocke * \_Allocfunc* comme pointeur à la fonction d’appeler à allouer le stockage et * \_Freefunc* comme pointeur à la fonction d’appeler pour libérer ce stockage.

Les trois constructeurs :

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

se comportent également comme le premier, si ce n’est que `_Getptr` désigne l’objet tableau utilisé pour contenir la séquence contrôlée. (Par conséquent, il ne doit pas être un pointeur nul.) Le nombre d’éléments *N* dans le tableau est déterminé comme suit :

- Si`count` (> 0), alors *N* N `count`est .

- Si`count` (0), alors *N* N `strlen`est (const `_Getptr` **const** `char` ) .

- Si`count` (< 0), alors *N* est **INT_MAX**.

Si `_Putptr` est un pointeur Null, la fonction établit simplement une mémoire tampon d’entrée en exécutant :

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

Sinon, elle établit des mémoires tampons d’entrée et de sortie en exécutant :

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

Dans ce cas, `_Putptr` doit se trouver dans l’intervalle [ `_Getptr`, `_Getptr` + *N*].

Enfin, les trois constructeurs :

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

se comportent tous comme :

```cpp
streambuf((char *)_Getptr, count);
```

si ce n’est que le mode stocké ne rend la séquence contrôlée ni modifiable, ni extensible.

## <a name="strstreambufunderflow"></a><a name="underflow"></a>strstreambuf::underflow

Fonction virtuelle protégée pour extraire l'élément actuel du flux d'entrée.

```cpp
virtual int underflow();
```

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `EOF`. Sinon, elle retourne l’élément actuel dans le flux d’entrée, converti comme décrit ci-dessus.

### <a name="remarks"></a>Notes

La fonction virtuelle protégée des membres `ch` s’efforce d’extraire l’élément actuel du tampon`int`d’entrée, puis de faire progresser la position actuelle du flux, et de retourner l’élément comme ( ))`unsigned char` **ch**. Il ne peut le faire que d’une seule `ch` manière: si une position de lecture est disponible, il prend comme l’élément stocké dans la position de lecture et avance le pointeur suivant pour le tampon d’entrée.

## <a name="see-also"></a>Voir aussi

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
