---
title: numpunct_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: da9259df8c527e44a4adea3a53be31b3c3ffc10b
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687609"
---
# <a name="numpunct_byname-class"></a>numpunct_byname, classe

Le modèle de classe dérivée décrit un objet qui peut servir de facette `numpunct` de paramètres régionaux donnés, permettant ainsi la mise en forme et la ponctuation d’expressions numériques et booléennes.

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

Son comportement est déterminé par les paramètres régionaux [nommés](../standard-library/locale-class.md#name) `_Locname`. Le constructeur initialise son objet de base avec [numpunct](../standard-library/numpunct-class.md#numpunct)\<CharType>( `_Refs`).

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
