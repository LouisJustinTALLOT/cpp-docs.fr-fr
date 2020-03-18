---
title: messages, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: 704ee2ce40b4026cc066213181c96cf0f744d152
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419860"
---
# <a name="messages-class"></a>messages, classe

Le modèle de classe décrit un objet pouvant servir de facette de paramètres régionaux pour récupérer des messages localisés à partir d’un catalogue de messages internationalisés pour des paramètres régionaux donnés.

Actuellement, lorsque la classe de messages est implémentée, il n'y a aucun message.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

Cette facette ouvre un catalogue de messages définis dans la classe de base messages_base, récupère les informations requises et ferme le catalogue.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[messages](#messages)|Fonction constructeur de facette de message.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type de caractère utilisé pour afficher les messages.|
|[string_type](#string_type)|Type qui décrit une chaîne de type `basic_string` qui contient des caractères de type `CharType`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[close](#close)|Ferme le catalogue de messages.|
|[do_close](#do_close)|Fonction virtuelle appelée pour fermer le catalogue de messages.|
|[do_get](#do_get)|Fonction virtuelle appelée pour récupérer le catalogue de messages.|
|[do_open](#do_open)|Fonction virtuelle appelée pour ouvrir le catalogue de messages.|
|[get](#get)|Récupère le catalogue de messages.|
|[open](#open)|Ouvre le catalogue de messages.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<paramètres régionaux >

**Espace de noms :** std

## <a name="char_type"></a>  messages::char_type

Type de caractère utilisé pour afficher les messages.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="close"></a>  messages::close

Ferme le catalogue de messages.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Paramètres

*_Catval*\
Catalogue à fermer.

### <a name="remarks"></a>Notes

La fonction membre appelle [do_close](#do_close)(_ *Catval*).

## <a name="do_close"></a>  messages::do_close

Fonction virtuelle appelée pour fermer le catalogue de messages.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Paramètres

*_Catval*\
Catalogue à fermer.

### <a name="remarks"></a>Notes

La fonction membre protégée ferme le catalogue de messages *_Catval*, qui doit avoir été ouvert par un appel antérieur à [do_open](#do_open).

*_Catval* doit être obtenu à partir d’un catalogue précédemment ouvert qui n’est pas fermé.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [close](#close), qui appelle `do_close`.

## <a name="do_get"></a>  messages::do_get

Fonction virtuelle appelée pour récupérer le catalogue de messages.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Paramètres

*_Catval*\
Valeur d’identification spécifiant le catalogue de messages dans lequel rechercher.

*_Set*\
Premier identificateur utilisé pour localiser un message dans un catalogue de messages.

*_Message*\
Deuxième identificateur utilisé pour localiser un message dans un catalogue de messages.

*_Dfault*\
Chaîne à retourner en cas d’échec.

### <a name="return-value"></a>Valeur de retour

Elle retourne une copie de *_Dfault* en cas d’échec. Sinon, retourne une copie de la séquence de message spécifiée.

### <a name="remarks"></a>Notes

La fonction membre protégée tente d’obtenir une séquence de messages à partir du catalogue de messages *_Catval*. Pour ce faire, il peut utiliser *_Set*, *_Message*et *_Dfault* .

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get](#get), qui appelle `do_get`.

## <a name="do_open"></a>  messages::do_open

Fonction virtuelle appelée pour ouvrir le catalogue de messages.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Paramètres

*_Catname*\
Nom du catalogue dans lequel rechercher.

*_Loc*\
Paramètres régionaux recherchés dans le catalogue.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur inférieure à zéro en cas d’échec. Dans le cas contraire, la valeur retournée peut être utilisée comme premier argument lors d’un appel ultérieur à [get](#get).

### <a name="remarks"></a>Notes

La fonction membre protégée tente d’ouvrir un catalogue de messages dont le nom est *_Catname*. Il peut utiliser les paramètres régionaux *_Loc* de cette manière.

La valeur de retour doit être utilisée comme argument lors d’un appel ultérieur à [close](#close).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [open](#open), qui appelle `do_open`.

## <a name="get"></a>  messages::get

Récupère le catalogue de messages.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Paramètres

*_Catval*\
Valeur d’identification spécifiant le catalogue de messages dans lequel rechercher.

*_Set*\
Premier identificateur utilisé pour localiser un message dans un catalogue de messages.

*_Message*\
Deuxième identificateur utilisé pour localiser un message dans un catalogue de messages.

*_Dfault*\
Chaîne à retourner en cas d’échec.

### <a name="return-value"></a>Valeur de retour

Elle retourne une copie de *_Dfault* en cas d’échec. Sinon, retourne une copie de la séquence de message spécifiée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`).

## <a name="messages"></a>  messages::messages

Fonction constructeur de facette de message.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière qui sert à spécifier le type de gestion de la mémoire pour l’objet.

*_Locname*\
Nom des paramètres régionaux.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le paramètre *_Refs* et leur signification sont les suivantes :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \> 1 : ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="open"></a>  messages::open

Ouvre le catalogue de messages.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Paramètres

*_Catname*\
Nom du catalogue dans lequel rechercher.

*_Loc*\
Paramètres régionaux recherchés dans le catalogue.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur inférieure à zéro en cas d’échec. Dans le cas contraire, la valeur retournée peut être utilisée comme premier argument lors d’un appel ultérieur à [get](#get).

### <a name="remarks"></a>Notes

La fonction membre retourne [do_open](#do_open)( `_Catname`, `_Loc`).

## <a name="string_type"></a>  messages::string_type

Type qui décrit une chaîne de type `basic_string` qui contient des caractères de type `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md) dont les objets peuvent stocker des copies des séquences de messages.

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[messages_base, classe](../standard-library/messages-base-class.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
