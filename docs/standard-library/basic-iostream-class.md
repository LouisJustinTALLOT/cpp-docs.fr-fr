---
title: basic_iostream, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 662c4915753cc49534fa9f489eb61504907744c4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954706"
---
# <a name="basiciostream-class"></a>basic_iostream, classe

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

La classe de modèle décrit un objet qui contrôle les insertions, par le biais de sa classe de base [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`>, et les extractions, par le biais de sa classe de base [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Les deux objets partagent une classe de base virtuelle commune [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. Ils gèrent également une mémoire tampon de flux commune, avec des éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`. Le constructeur initialise ses classes de base avec `basic_istream`( **strbuf**) et `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_iostream](#basic_iostream)|Créez un objet `basic_iostream`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[swap](#swap)|Échange le contenu de l'objet `basic_iostream` fourni avec le contenu de cet objet.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Assigne la valeur d'un objet `basic_iostream` spécifié à cet objet. Il s'agit d'une assignation de déplacement impliquant une `rvalue` qui ne laisse pas de copie.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<istream>

**Espace de noms :** std

## <a name="basic_iostream"></a>  basic_iostream::basic_iostream

Créez un objet `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Paramètres

*strbuf* existant `basic_streambuf` objet.

*droit* existant `basic_iostream` objet qui est utilisé pour construire un nouveau `basic_iostream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise les objets de base par l’intermédiaire de `basic_istream(strbuf)` et `basic_ostream(strbuf)`.

Le deuxième constructeur initialise les objets de base en appelant `move(right)`.

## <a name="op_eq"></a>  basic_iostream::operator=

Assigne la valeur d'un objet `basic_iostream` spécifié à cet objet. Il s'agit d'une assignation de déplacement qui implique une rvalue qui ne laisse pas de copie.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Paramètres

*droit* un `rvalue` font référence à un `basic_iostream` objet affecter à partir de.

### <a name="remarks"></a>Notes

L’opérateur membre appelle `swap(right)`.

## <a name="swap"></a>  basic_iostream::swap

Échange le contenu de l'objet `basic_iostream` fourni avec le contenu de cet objet.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Paramètres

*droit* le `basic_iostream` objet à échanger.

### <a name="remarks"></a>Notes

La fonction membre appelle `swap(right)`.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
