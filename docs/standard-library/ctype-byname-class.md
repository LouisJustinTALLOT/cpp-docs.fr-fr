---
description: 'En savoir plus sur : classe ctype_byname'
title: ctype_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: cc5f44e1c544d2088030621b684c9e070175d695
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233134"
---
# <a name="ctype_byname-class"></a>ctype_byname, classe

Le modèle de classe dérivée décrit un objet pouvant servir de facette CType de paramètres régionaux donnés, permettant ainsi la classification des caractères et la conversion de caractères entre les jeux de caractères et les jeux de caractères spécifiés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>Notes

Son comportement est déterminé par les paramètres régionaux nommés `_Locname`. Chaque constructeur initialise son objet de base avec [CType](../standard-library/ctype-class.md) \<CharType> ( `_Refs` ) ou l’équivalent pour la classe de base `ctype<char>` .

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
