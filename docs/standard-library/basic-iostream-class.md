---
description: 'En savoir plus sur : classe basic_iostream'
title: basic_iostream, classe
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: c9b605c5eb36a0bc725ce21e2c89617357078d40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321512"
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

Le modèle de classe décrit un objet qui contrôle les insertions, via sa classe de base [basic_ostream](../standard-library/basic-ostream-class.md) <  `Elem` , `Tr`> et des extractions, par le biais de sa classe de base [basic_istream](../standard-library/basic-istream-class.md) <  `Elem` , `Tr`>. Les deux objets partagent une classe de base virtuelle commune [basic_ios](../standard-library/basic-ios-class.md) <  `Elem` , `Tr`>. Ils gèrent également une mémoire tampon de flux commune, avec des éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`. Le constructeur initialise ses classes de base avec `basic_istream`( **strbuf**) et `basic_ostream`( **strbuf**).

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
|[opérateur =](#op_eq)|Assigne la valeur d'un objet `basic_iostream` spécifié à cet objet. Il s'agit d'une assignation de déplacement impliquant une `rvalue` qui ne laisse pas de copie.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<istream>

**Espace de noms :** std

## <a name="basic_iostreambasic_iostream"></a><a name="basic_iostream"></a> basic_iostream :: basic_iostream

Créez un objet `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Paramètres

*strbuf*\
Objet `basic_streambuf` existant.

*Oui*\
Objet `basic_iostream` existant utilisé pour construire un nouveau `basic_iostream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise les objets de base par l’intermédiaire de `basic_istream(strbuf)` et `basic_ostream(strbuf)`.

Le deuxième constructeur initialise les objets de base en appelant `move(right)` .

## <a name="basic_iostreamoperator"></a><a name="op_eq"></a> basic_iostream :: Operator =

Assigne la valeur d'un objet `basic_iostream` spécifié à cet objet. Il s'agit d'une assignation de déplacement qui implique une rvalue qui ne laisse pas de copie.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence `rvalue` à un objet `basic_iostream` à partir duquel effectuer l'assignation.

### <a name="remarks"></a>Notes

L’opérateur membre appelle `swap(right)` .

## <a name="basic_iostreamswap"></a><a name="swap"></a> basic_iostream :: swap

Échange le contenu de l'objet `basic_iostream` fourni avec le contenu de cet objet.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `basic_iostream` à échanger.

### <a name="remarks"></a>Notes

La fonction membre appelle `swap(right)` .

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
