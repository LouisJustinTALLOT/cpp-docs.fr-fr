---
title: numpunct_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: 64e8918b052b05088ff48aefb0f0f9ab8c6df586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432871"
---
# <a name="numpunctbyname-class"></a>numpunct_byname, classe

La classe de modèle dérivée décrit un objet pouvant servir de facette `numpunct` de paramètres régionaux donnés, permettant la mise en forme et la ponctuation d’expressions numériques et booléennes.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
