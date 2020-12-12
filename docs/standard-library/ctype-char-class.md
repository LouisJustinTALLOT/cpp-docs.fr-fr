---
description: 'En savoir plus sur : CType &lt; Char, &gt; classe'
title: ctype&lt;char&gt;, classe
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: f423b66f75cc0e1ee823251977e7d048b3c19e02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324666"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt;, classe

La classe est une spécialisation explicite de la classe template `ctype\<CharType>` à taper **`char`** , décrivant un objet pouvant servir de facette de paramètres régionaux pour caractériser diverses propriétés d’un caractère de type **`char`** .

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>Notes

La spécialisation explicite diffère du modèle de classe de plusieurs façons :

- Un objet de classe `ctype<char>` stocke un pointeur vers le premier élément d’une table de masque CType, un tableau d’éléments UCHAR_MAX + 1 de type `ctype_base::mask` . Il stocke également un objet booléen qui indique si le tableau doit être supprimé (à l’aide de `operator delete[]` ) quand l' \< **Elem**> objet CType est détruit.

- Son seul constructeur public vous permet de spécifier `tab` , la table de masque CType et `del` , l’objet booléen qui est true si le tableau doit être supprimé lors de la destruction de l' `ctype<char>` objet, ainsi que les références de paramètre de nombre de références.

- La fonction membre protégée `table` retourne la table de masque CType stockée.

- L’objet de membre statique `table_size` spécifie le nombre minimal d’éléments dans une table de masque CType.

- La fonction membre statique protégée `classic_table` (retourne la table du masque CType appropriée aux paramètres régionaux « C ».

- Il n’y a aucune fonction membre virtuelle protégée [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is) ou [do_scan_not](../standard-library/ctype-class.md#do_scan_not). Les fonctions membres publiques correspondantes effectuent les opérations équivalentes.

Les fonctions membres [do_narrow](../standard-library/ctype-class.md#do_narrow) et [do_widen](../standard-library/ctype-class.md#do_widen) copient des éléments non modifiés.

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[facette, classe](locale-class.md#facet_class)\
[Classe ctype_base](../standard-library/ctype-base-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
