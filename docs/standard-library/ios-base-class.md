---
title: ios_base, classe
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
ms.openlocfilehash: 056b7e47c474c64bf357523e2995ef49d456a9cd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449184"
---
# <a name="ios_base-class"></a>ios_base, classe

La classe décrit les fonctions membres et de stockage communes aux flux d'entrée et de sortie qui ne dépendent pas des paramètres du modèle. (La classe de modèle [basic_ios](../standard-library/basic-ios-class.md) décrit ce qui est commun et qui dépend des paramètres de modèle.)

Un objet de la classe ios_base stocke des informations de mise en forme, qui comprennent :

- Des indicateurs de format dans un objet de type [fmtflags](#fmtflags).

- Un masque d’exception dans un objet de type [iostate](#iostate).

- Une largeur de champ dans un objet de type **int**.

- Précision d’affichage dans un objet de type **int**.

- Objet de paramètres régionaux dans un objet de type `locale`.

- Deux tableaux extensibles, avec des éléments de type **long** et un pointeur **void** .

Un objet de la classe ios_base stocke également des informations d’état de flux dans un objet de type [iostate](#iostate) et une pile des rappels.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[ios_base](#ios_base)|Construit des objets `ios_base`.|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[event_callback](#event_callback)|Décrit une fonction passée à [register_call](#register_callback).|
|[fmtflags](#fmtflags)|Constantes pour spécifier l'apparence de la sortie.|
|[iostate](#iostate)|Définit des constantes décrivant l'état d'un flux.|
|[openmode](#openmode)|Décrit comment interagir avec un flux.|
|[seekdir](#seekdir)|Spécifie le point de départ pour les opérations de décalage.|

### <a name="enums"></a>Énumérations

|||
|-|-|
|[event](#event)|Spécifie des types d'événements.|

### <a name="constants"></a>Constantes

|||
|-|-|
|[adjustfield](#fmtflags)|Masque de bits défini comme `internal` &#124; `left` &#124; `right`.|
|[app](#openmode)|Spécifie qu'une recherche doit être effectuée jusqu'à la fin d'un flux avant chaque insertion.|
|[ate](#openmode)|Spécifie qu'une recherche doit être effectuée jusqu'à la fin d'un flux quand son objet de contrôle est créé en premier.|
|[badbit](#iostate)|Enregistre une perte d'intégrité de la mémoire tampon du flux.|
|[basefield](#fmtflags)|Masque de bits défini comme `dec` &#124; `hex` &#124; `oct`.|
|[beg](#seekdir)|Spécifie qu'une recherche doit être effectuée relativement au début d'une séquence.|
|[binary](#openmode)|Spécifie qu'un fichier doit être lu comme un flux binaire, et non pas comme un flux de texte.|
|[boolalpha](#fmtflags)|Spécifie l’insertion ou l’extraction d’objets de type **bool** en tant que noms (tels que **true** et **false**) plutôt que de valeurs numériques.|
|[cur](#seekdir)|Spécifie qu'une recherche doit être effectuée relativement à la position actuelle dans une séquence.|
|[dec](#fmtflags)|Spécifie l'insertion ou l'extraction de valeurs entières au format décimal.|
|[end](#seekdir)|Spécifie qu'une recherche doit être effectuée relativement à la fin d'une séquence.|
|[eofbit](#iostate)|Enregistre la fin de fichier lors de l'extraction à partir d'un flux.|
|[failbit](#iostate)|Enregistre un échec de l'extraction d'un champ valide dans un flux.|
|[fixed](#fmtflags)|Spécifie l'insertion de valeurs à virgule flottante dans un format à virgule fixe (sans champ d'exposant).|
|[floatfield](#fmtflags)|A bitmask defined as `fixed` &#124; `scientific`|
|[goodbit](#iostate)|Tous les bits d'état sont effacés.|
|[hex](#fmtflags)|Spécifie l'insertion ou l'extraction de valeurs entières au format hexadécimal.|
|[in](#openmode)|Spécifie l'extraction à partir d'un flux.|
|[internal](#fmtflags)|Complète jusqu'à une largeur de champ en insérant des caractères de remplissage à un point interne dans un champ numérique généré.|
|[left](#fmtflags)|Spécifie la justification à gauche.|
|[oct](#fmtflags)|Spécifie l'insertion ou l'extraction de valeurs entières au format octal.|
|[out](#openmode)|Spécifie l'insertion dans un flux.|
|[right](#fmtflags)|Spécifie la justification à droite.|
|[scientific](#fmtflags)|Spécifie l'insertion de valeurs à virgule flottante au format scientifique (sans champ d'exposant).|
|[showbase](#fmtflags)|Spécifie l'insertion d'un préfixe qui indique la base d'un champ d'entier généré.|
|[showpoint](#fmtflags)|Spécifie l'insertion inconditionnelle de la virgule décimale dans un champ à virgule flottante généré.|
|[showpos](#fmtflags)|Spécifie l'insertion d'un signe plus dans un champ numérique généré non négatif.|
|[skipws](#fmtflags)|Spécifie qu'il faut ignorer l'espace blanc du début avant certaines extractions.|
|[trunc](#openmode)|Spécifie la suppression du contenu d'un fichier existant lors de la création de son objet de contrôle.|
|[unitbuf](#fmtflags)|Provoque le vidage de la sortie après chaque insertion.|
|[uppercase](#fmtflags)|Spécifie l'insertion d'équivalents majuscules des lettres minuscules dans certaines insertions.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[failure](#failure)|La classe membre sert de classe de base pour toutes les exceptions levées par la fonction membre [clear](../standard-library/basic-ios-class.md#clear) dans la classe de modèle [basic_ios](../standard-library/basic-ios-class.md).|
|[flags](#flags)|Définit ou retourne les valeurs de l'indicateur actuel.|
|[getloc](#getloc)|Retourne l’objet des paramètres régionaux stockés.|
|[imbue](#imbue)|Change les paramètres régionaux.|
|[Init](#init)|Crée les objets iostream standard lors de la construction.|
|[iword](#iword)|Affecte une valeur à stocker comme `iword`.|
|[precision](#precision)|Spécifie le nombre de chiffres à afficher dans un nombre à virgule flottante.|
|[pword](#pword)|Affecte une valeur à stocker comme `pword`.|
|[register_callback](#register_callback)|Spécifie une fonction de rappel.|
|[setf](#setf)|Définit les indicateurs spécifiés.|
|[sync_with_stdio](#sync_with_stdio)|Garantit que les opérations d'iostream et de la bibliothèque Runtime C se produisent dans l'ordre où elles apparaissent dans le code source.|
|[unsetf](#unsetf)|Désactive les indicateurs spécifiés.|
|[width](#width)|Définit la longueur du flux de sortie.|
|[xalloc](#xalloc)|Spécifie qu'une variable fera partie du flux.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator=](#op_eq)|Opérateur d'affectation pour les objets `ios_base`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<ios>

**Espace de noms :** std

## <a name="event"></a>événement

Spécifie des types d'événements.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Notes

Le type est un type énuméré qui décrit un objet capable de stocker l’événement de rappel utilisé comme argument d’une fonction inscrite avec [register_callback](#register_callback). Les valeurs d’événements distinctes sont les suivantes :

- `copyfmt_event`, pour identifier un rappel qui se produit près de la fin d’un appel à [copyfmt](../standard-library/basic-ios-class.md#copyfmt), juste avant que le [masque d’exception](../standard-library/ios-base-class.md) soit copié.

- `erase_event`, pour identifier un rappel qui se produit au début d’un appel à [copyfmt](../standard-library/basic-ios-class.md#copyfmt), ou au début d’un appel au destructeur pour  **\*ce**.

- `imbue_event`, pour identifier un rappel qui se produit à la fin d’un appel à [imbue](#imbue), juste avant le retour de la fonction.

### <a name="example"></a>Exemples

Pour obtenir un exemple, consultez [register_callback](#register_callback).

## <a name="event_callback"></a>event_callback

Décrit une fonction passée à [register_call](#register_callback).

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>Paramètres

*_E*\
Correspond à l’[event](#event).

*Atteindre la*\
Flux dans lequel l’événement a été appelé.

*_I*\
Nombre défini par l’utilisateur.

### <a name="remarks"></a>Notes

Ce type décrit un pointeur vers une fonction qui peut être inscrite avec [register_callback](#register_callback). Ce type de fonction ne doit pas lever d’exception.

### <a name="example"></a>Exemples

Pour obtenir un exemple qui utilise `event_callback`, consultez [register_call](#register_callback).

## <a name="failure"></a>toute

La classe `failure` définit la classe de base pour les types de tous les objets levés comme exceptions, par des fonctions de la bibliothèque `iostreams`, pour signaler les erreurs détectées pendant les opérations de mise en mémoire tampon de flux.

```cpp
namespace std {
    class failure : public system_error {
    public:
        explicit failure(
            const string& _Message,
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,
            const error_code& _Code = io_errc::stream);
    };
}
```

### <a name="remarks"></a>Notes

La valeur retournée par `what()` est une copie de `_Message`, éventuellement augmentée avec un test basé sur `_Code`. Si `_Code` n’est pas spécifié, la valeur par défaut est `make_error_code(io_errc::stream)`.

### <a name="example"></a>Exemple

```cpp
// ios_base_failure.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.exceptions(ios::failbit);
    try
    {
        file.open( "rm.txt", ios_base::in );
        // Opens nonexistent file for reading
    }
    catch( ios_base::failure f )
    {
        cout << "Caught an exception: " << f.what() << endl;
    }
}
```

```Output
Caught an exception: ios_base::failbit set
```

## <a name="flags"></a>père

Définit ou retourne les valeurs de l'indicateur actuel.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>Paramètres

*fmtfl*\
Nouveau paramètre `fmtflags`.

### <a name="return-value"></a>Valeur de retour

Paramètre `fmtflags` précédent ou actif.

### <a name="remarks"></a>Notes

Pour obtenir la liste des indicateurs, consultez [ios_base::fmtflags](#fmtflags).

La première fonction membre retourne les indicateurs de format stockés. La deuxième fonction membre stocke *fmtfl* dans les indicateurs de format et retourne sa valeur stockée précédente.

### <a name="example"></a>Exemples

```cpp
// ios_base_flags.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    cout << cout.flags( ) << endl;
    cout.flags( ios::dec | ios::boolalpha );
    cout << cout.flags( );
}
```

```Output
513
16896
```

## <a name="fmtflags"></a>fmtflags

Constantes pour spécifier l'apparence de la sortie.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type fmtflags;
   static const fmtflags boolalpha;
   static const fmtflags dec;
   static const fmtflags fixed;
   static const fmtflags hex;
   static const fmtflags internal;
   static const fmtflags left;
   static const fmtflags oct;
   static const fmtflags right;
   static const fmtflags scientific;
   static const fmtflags showbase;
   static const fmtflags showpoint;
   static const fmtflags showpos;
   static const fmtflags skipws;
   static const fmtflags unitbuf;
   static const fmtflags uppercase;
   static const fmtflags adjustfield;
   static const fmtflags basefield;
   static const fmtflags floatfield;
   // ...
};
```

### <a name="remarks"></a>Notes

Prend en charge les manipulateurs dans [ios](../standard-library/ios.md).

Le type est un type de masque de bits qui décrit un objet pouvant stocker des indicateurs de format. Les valeurs distinctes des indicateurs (éléments) sont :

- `dec`, pour insérer ou extraire des valeurs entières au format décimal.

- `hex`, pour insérer ou extraire des valeurs entières au format hexadécimal.

- `oct`, pour insérer ou extraire des valeurs entières au format octal.

- `showbase`, pour insérer un préfixe qui indique la base d'un champ entier généré.

- `internal`, pour compléter une largeur de champ selon les besoins, en insérant des caractères de remplissage à un point interne d'un champ numérique généré. (Pour plus d’informations sur la définition de la largeur de champ, consultez [setw](../standard-library/iomanip-functions.md#setw)).

- `left`, pour compléter une largeur de champ selon les besoins, en insérant des caractères de remplissage à la fin d'un champ généré (justification à gauche).

- `right`, pour compléter une largeur de champ selon les besoins, en insérant des caractères de remplissage au début d'un champ généré (justification à droite).

- `boolalpha`, pour insérer ou extraire des objets de type **bool** en tant que noms (tels que **true** et **false**) plutôt qu’en tant que valeurs numériques.

- `fixed`, pour insérer des valeurs à virgule flottante dans un format à virgule fixe (sans champ d'exposant).

- `scientific`, pour insérer des valeurs à virgule flottante au format scientifique (avec un champ d'exposant).

- `showpoint`, pour insérer un séparateur décimal de façon inconditionnelle dans un champ à virgule flottante généré.

- `showpos`, pour insérer un signe plus dans un champ numérique généré non négatif.

- `skipws`, pour ignorer l'espace blanc initial avant certaines extractions.

- `unitbuf`, pour vider la sortie après chaque insertion.

- `uppercase`, pour insérer des équivalents majuscules des lettres minuscules dans certaines insertions.

Les valeurs suivantes sont également utiles :

- `adjustfield`, un masque de bits défini comme `internal` &#124; `left` &#124; `right`

- `basefield`, défini comme `dec` &#124; `hex` &#124; `oct`

- `floatfield`, défini comme `fixed` &#124; `scientific`

Pour obtenir des exemples de fonctions qui modifient ces indicateurs de format, consultez [\<iomanip>](../standard-library/iomanip.md).

## <a name="getloc"></a>getloc

Retourne l’objet des paramètres régionaux stockés.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Valeur de retour

Objet des paramètres régionaux stocké.

### <a name="example"></a>Exemple

```cpp
// ios_base_getlock.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << cout.getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="imbue"></a>imbue

Change les paramètres régionaux.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>Paramètres

*_Loc*\
Nouveaux paramètres régionaux.

### <a name="return-value"></a>Valeur de retour

Paramètres régionaux précédents.

### <a name="remarks"></a>Notes

La fonction membre stocke *_Loc* dans l’objet de paramètres régionaux, puis signale l' `imbue_event`événement de rappel et. Elle retourne la valeur stockée précédente.

### <a name="example"></a>Exemple

Pour obtenir un exemple, consultez [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue).

## <a name="init"></a>Rein

Crée les objets iostream standard lors de la construction.

```cpp
class Init { };
```

### <a name="remarks"></a>Notes

La classe imbriquée décrit un objet dont la construction garantit que les objets iostreams standard sont construits correctement, même avant l’exécution d’un constructeur d’objet statique arbitraire.

## <a name="ios_base"></a>ios_base

Construit des objets ios_base.

```cpp
ios_base();
```

### <a name="remarks"></a>Notes

Le constructeur (protégé) ne fait rien. Un appel ultérieur à **basic_ios::** [init](../standard-library/basic-ios-class.md#init) doit initialiser l’objet avant qu’il puisse être détruit en toute sécurité. Ainsi, la seule utilisation sécurisée de la classe ios_base est en tant que classe de base pour la classe de modèle [basic_ios](../standard-library/basic-ios-class.md).

## <a name="iostate"></a>iostate

Type des constantes qui décrivent l’état d’un flux.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Notes

Le type est un type de masque de bits qui décrit un objet pouvant stocker des informations d’état de flux. Les valeurs distinctes des indicateurs (éléments) sont :

- `badbit`, pour enregistrer une perte d’intégrité de la mémoire tampon du flux.

- `eofbit`, pour enregistrer la fin de fichier lors de l’extraction à partir d’un flux.

- `failbit`, pour enregistrer un échec d’extraction d’un champ valide à partir d’un flux.

En outre, une valeur utile est `goodbit`, où aucun des bits mentionnés précédemment n’est défini (`goodbit` la valeur est garantie comme étant égale à zéro).

## <a name="iword"></a>iword

Affecte une valeur à stocker comme `iword`.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>Paramètres

*mét*\
Index de la valeur à stocker en tant que `iword`.

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à l’élément *idx* du tableau extensible avec des éléments de type **long**. Tous les éléments sont effectivement présents et contiennent initialement la valeur zéro. La référence retournée n’est pas valide après l’appel suivant à `iword` pour l’objet, après que l’objet a été modifié par un appel à **basic_ios::** [copyfmt](../standard-library/basic-ios-class.md#copyfmt) ou après sa destruction.

Si *idx* est négative ou si le stockage unique n’est pas disponible pour l’élément, la fonction appelle [SetState](../standard-library/basic-ios-class.md#setstate) **(badbit)** et retourne une référence qui n’est peut-être pas unique.

Pour obtenir un index unique, pour une utilisation parmi tous les objets de type `ios_base`, appelez [xalloc](#xalloc).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `iword`, consultez [xalloc](#xalloc).

## <a name="openmode"></a>OpenMode

Décrit comment interagir avec un flux.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Notes

Le type est un `bitmask type` qui décrit un objet capable de stocker le mode d’ouverture de plusieurs objets iostreams. Les valeurs distinctes des indicateurs (éléments) sont :

- `app`, pour rechercher jusqu’à la fin d’un flux avant chaque insertion.

- `ate`, pour rechercher jusqu’à la fin d’un flux de données lorsque son objet de contrôle est créé pour la première fois.

- `binary`, pour lire un fichier en tant que flux binaire, plutôt qu’en tant que flux de texte.

- `in`, pour permettre l’extraction à partir d’un flux.

- `out`, pour autoriser l’insertion dans un flux.

- `trunc`, pour supprimer le contenu d’un fichier existant quand son objet de contrôle est créé.

### <a name="example"></a>Exemple

```cpp
// ios_base_openmode.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
}
```

## <a name="op_eq"></a>opérateur =

Opérateur d’affectation pour les objets ios_base.

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet de type `ios_base`.

### <a name="return-value"></a>Valeur de retour

Objet qui est affecté.

### <a name="remarks"></a>Notes

L’opérateur copie les informations de mise en forme stockées, ce qui crée une copie des tableaux extensibles. Il retourne ensuite **\*this**. Notez que la pile de rappels n’est pas copiée.

Cet opérateur est utilisé uniquement par les classes dérivées de `ios_base`.

## <a name="precision"></a>précision

Spécifie le nombre de chiffres à afficher dans un nombre à virgule flottante.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>Paramètres

*_Prec*\
Nombre de chiffres significatifs à afficher, ou nombre de chiffres après la virgule décimale dans la notation fixe.

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne la [précision d’affichage](../standard-library/ios-base-class.md) stockée. La deuxième fonction membre stocke *_Prec* dans la précision d’affichage et retourne sa valeur stockée précédente.

### <a name="remarks"></a>Notes

Les chiffres à virgule flottante sont affichés dans la notation fixe avec [fixed](../standard-library/ios-functions.md#fixed).

### <a name="example"></a>Exemples

```cpp
// ios_base_precision.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    float i = 31.31234F;

    cout.precision( 3 );
    cout << i << endl;          // display three significant digits
    cout << fixed << i << endl; // display three digits after decimal
                                // point
}
```

```Output
31.3
31.312
```

## <a name="pword"></a>pWord

Affecte une valeur à stocker comme `pword`.

```cpp
void *& pword(int _Idx);
```

### <a name="parameters"></a>Paramètres

*_Idx*\
Index de la valeur à stocker en tant que `pword`.

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à l’élément _ *idx* du tableau extensible avec des éléments de type pointeur **void** . Tous les éléments sont effectivement présents et contiennent initialement le pointeur Null. La référence retournée n’est pas valide après l’appel suivant à `pword` pour l’objet, après que l’objet a été modifié par un appel à **basic_ios::** [copyfmt](../standard-library/basic-ios-class.md#copyfmt) ou après sa destruction.

Si _ *Idx* est négatif ou si aucun stockage unique n’est disponible pour l’élément, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate) **(badbit)** et retourne une référence susceptible de ne pas être unique.

Pour obtenir un index unique, pour une utilisation parmi tous les objets de type `ios_base`, appelez [xalloc](#xalloc).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `pword`, consultez [xalloc](#xalloc).

## <a name="register_callback"></a>register_callback

Spécifie une fonction de rappel.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>Paramètres

*PFN*\
Pointeur vers la fonction de rappel.

*mét*\
Nombre défini par l’utilisateur.

### <a name="remarks"></a>Notes

La fonction membre exécute un push de `{pfn, idx}` la paire sur la [pile de rappels](../standard-library/ios-base-class.md)de la pile de rappels stockée. Lorsqu’un événement de rappel **ev** est signalé, les fonctions sont appelées, dans l’ordre inverse du Registre, `(*pfn)(ev, *this, idx)`par l’expression.

### <a name="example"></a>Exemple

```cpp
// ios_base_register_callback.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void callback1( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback1" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

void callback2( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback2" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

int main( )
{
    // Make sure the imbue will not throw an exception
    // assert( setlocale( LC_ALL, "german" )!=NULL );

    cout.register_callback( callback1, 0 );
    cin.register_callback( callback2, 0 );

    try
    {
        // If no exception because the locale's not found,
        // generate an imbue_event on callback1
        cout.imbue(locale("german"));
    }
    catch(...)
    {
        cout << "exception" << endl;
    }

    // This will
    // (1) erase_event on callback1
    // (2) copyfmt_event on callback2
    cout.copyfmt(cin);

    // We get two erase events from callback2 at the end because
    // both cin and cout have callback2 registered when cin and cout
    // are destroyed at the end of program.
}
```

```Output
in callback1
an imbue event
in callback1
an erase event
in callback2
an copyfmt event
in callback2
an erase event
in callback2
an erase event
```

## <a name="seekdir"></a>seekdir

Spécifie le point de départ pour les opérations de décalage.

```cpp
namespace std {
    class ios_base {
    public:
        typedef implementation-defined-enumerated-type seekdir;
        static const seekdir beg;
        static const seekdir cur;
        static const seekdir end;
        // ...
    };
}
```

### <a name="remarks"></a>Notes

Le type est un type énuméré qui décrit un objet pouvant stocker le mode de recherche utilisé comme argument pour les fonctions membres de plusieurs classes iostream. Les valeurs distinctes des indicateurs sont :

- `beg`, pour rechercher (modifier la position actuelle de lecture ou d’écriture) par rapport au début d’une séquence (tableau, flux ou fichier).

- `cur`, pour effectuer une recherche par rapport à la position actuelle dans une séquence.

- `end`, pour effectuer une recherche par rapport à la fin d’une séquence.

### <a name="example"></a>Exemple

```cpp
// ios_base_seekdir.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
    file.seekp( 0, ios_base::beg );
    file << "a";
    file.seekp( 0, ios_base::end );
    file << "a";
}
```

## <a name="setf"></a>SETF

Définit les indicateurs spécifiés.

```cpp
fmtflags setf(
    fmtflags _Mask
);
fmtflags setf(
    fmtflags _Mask,
    fmtflags _Unset
);
```

### <a name="parameters"></a>Paramètres

*_Mask*\
Indicateurs à activer.

*_Unset*\
Indicateurs à désactiver.

### <a name="return-value"></a>Valeur de retour

Indicateurs de format précédents

### <a name="remarks"></a>Notes

La première fonction membre appelle efficacement [Flags](#flags)( &#124;  *\_indicateurs*de  *\_masque* ) (définissez les bits sélectionnés), puis retourne les indicateurs de format précédents. La deuxième fonction membre appelle `flags(_Mask & fmtfl, flags & ~_Mask)` effectivement (remplacer les bits sélectionnés sous un masque), puis retourne les indicateurs de format précédents.

### <a name="example"></a>Exemples

```cpp
// ios_base_setf.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    int i = 10;
    cout << i << endl;

    cout.unsetf( ios_base::dec );
    cout.setf( ios_base::hex );
    cout << i << endl;

    cout.setf( ios_base::dec );
    cout << i << endl;
    cout.setf( ios_base::hex, ios_base::dec );
    cout << i << endl;
}
```

## <a name="sync_with_stdio"></a>sync_with_stdio

Garantit que les opérations d'iostream et de la bibliothèque Runtime C se produisent dans l'ordre où elles apparaissent dans le code source.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>Paramètres

*_Sync*\
Indique si tous les flux sont synchronisés avec `stdio`.

### <a name="return-value"></a>Valeur de retour

Paramètre précédent pour cette fonction.

### <a name="remarks"></a>Notes

La fonction membre statique stocke `stdio` un indicateur de synchronisation, qui a pour **valeur true**. Si la **valeur est true**, cet indicateur garantit que les opérations sur le même fichier sont correctement synchronisées entre les fonctions [iostreams](../standard-library/iostreams-conventions.md) et C++ celles définies dans la bibliothèque standard. Dans le cas contraire, la synchronisation peut être garantie ou non, mais les performances peuvent être améliorées. La fonction stocke *_Sync* dans `stdio` l’indicateur de synchronisation et retourne sa valeur stockée précédente. Vous pouvez l’appeler de façon fiable uniquement avant d’effectuer des opérations sur les flux standard.

## <a name="unsetf"></a>unsetf

Désactive les indicateurs spécifiés.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>Paramètres

*_Mask*\
Indicateurs que vous souhaitez désactiver.

### <a name="remarks"></a>Notes

La fonction membre appelle efficacement [Flags](#flags)(`~` *_Mask* **& Flags**) (effacer les bits sélectionnés).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation `unsetf`de, consultez [ios_base :: SETF](#setf) .

## <a name="width"></a>Largeur

Définit la longueur du flux de sortie.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>Paramètres

*_Wide*\
Taille du flux de sortie souhaitée.

### <a name="return-value"></a>Valeur de retour

Paramètre de largeur actuel.

### <a name="remarks"></a>Notes

La première fonction membre retourne la largeur du champ stocké. La deuxième fonction membre stocke *_Wide* dans la largeur de champ et retourne sa valeur stockée précédente.

### <a name="example"></a>Exemple

```cpp
// ios_base_width.cpp
// compile with: /EHsc
#include <iostream>

int main( ) {
    using namespace std;

    cout.width( 20 );
    cout << cout.width( ) << endl;
    cout << cout.width( ) << endl;
}
```

```Output
20
0
```

## <a name="xalloc"></a>xalloc

Spécifie qu’une variable fait partie du flux.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>Valeur de retour

La fonction membre statique retourne une valeur statique stockée, qu’elle incrémente à chaque appel.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la valeur de retour comme argument d’index unique lors de l’appel des fonctions membres [iword](#iword) ou [pWord](#pword).

### <a name="example"></a>Exemple

```cpp
// ios_base_xalloc.cpp
// compile with: /EHsc
// Lets you store user-defined information.
// iword, jword, xalloc
#include <iostream>

int main( )
{
    using namespace std;

    static const int i = ios_base::xalloc();
    static const int j = ios_base::xalloc();
    cout.iword( i ) = 11;
    cin.iword( i ) = 13;
    cin.pword( j ) = "testing";
    cout << cout.iword( i ) << endl;
    cout << cin.iword( i ) << endl;
    cout << ( char * )cin.pword( j ) << endl;
}
```

```Output
11
13
testing
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
