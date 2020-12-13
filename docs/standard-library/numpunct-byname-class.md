---
description: 'En savoir plus sur : classe numpunct_byname'
title: numpunct_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: e4e6352f9f65b2a726acf3f8f5f8ede9bffe54f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338030"
---
# <a name="numpunct_byname-class"></a>numpunct_byname, classe

Le modèle de classe dérivée décrit un objet pouvant servir de `numpunct` facette de paramètres régionaux donnés, permettant ainsi la mise en forme et la ponctuation d’expressions numériques et booléennes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>Notes

Son comportement est déterminé par les [](../standard-library/locale-class.md#name) paramètres régionaux nommés `_Locname` . Le constructeur initialise son objet de base avec [numpunct](../standard-library/numpunct-class.md#numpunct) \<CharType> ( `_Refs` ).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
