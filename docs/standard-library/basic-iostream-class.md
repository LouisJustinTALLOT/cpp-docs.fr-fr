---
title: basic_iostream, classe
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: e2a892525afbbad6d5b42d0b836fee096a70c297
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376821"
---
# <a name="basic_iostream-class"></a>basic_iostream, classe

Classe de flux qui peut effectuer à la fois l'entrée et la sortie.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream : public basic_istream<Elem, Tr>,
    public basic_ostream<Elem, Tr>
{
public:
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};
```

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`contrôle les `Tr` insertions, à travers sa classe de base basic_ostream `Tr` ,>, et les extractions, à travers sa classe de base [basic_istream](../standard-library/basic-istream-class.md)< `Elem`,>. Les deux objets partagent une classe de `Tr` base virtuelle commune [basic_ios](../standard-library/basic-ios-class.md)< `Elem`,>. Ils gèrent également une mémoire tampon de flux commune, avec des éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`. Le constructeur initialise ses classes de base avec `basic_istream`( **strbuf**) et `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_iostream](#basic_iostream)|Créez un objet `basic_iostream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[swap](#swap)|Échange le contenu de l'objet `basic_iostream` fourni avec le contenu de cet objet.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur](#op_eq)|Assigne la valeur d'un objet `basic_iostream` spécifié à cet objet. Il s'agit d'une assignation de déplacement impliquant une `rvalue` qui ne laisse pas de copie.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<istream>

**Espace de noms :** std

## <a name="basic_iostreambasic_iostream"></a><a name="basic_iostream"></a>basic_iostream::basic_iostream

Créez un objet `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Paramètres

*strbuf (strbuf)*\
Objet `basic_streambuf` existant.

*Oui*\
Objet `basic_iostream` existant utilisé pour construire un nouveau `basic_iostream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise les objets de base par l’intermédiaire de `basic_istream(strbuf)` et `basic_ostream(strbuf)`.

Le deuxième constructeur initialise les objets `move(right)`de base en appelant .

## <a name="basic_iostreamoperator"></a><a name="op_eq"></a>basic_iostream::opérateur

Assigne la valeur d'un objet `basic_iostream` spécifié à cet objet. Il s'agit d'une assignation de déplacement qui implique une rvalue qui ne laisse pas de copie.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence `rvalue` à un objet `basic_iostream` à partir duquel effectuer l'assignation.

### <a name="remarks"></a>Notes

L’opérateur `swap(right)`membre appelle .

## <a name="basic_iostreamswap"></a><a name="swap"></a>basic_iostream::swap

Échange le contenu de l'objet `basic_iostream` fourni avec le contenu de cet objet.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `basic_iostream` à échanger.

### <a name="remarks"></a>Notes

La fonction `swap(right)`membre appelle .

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
