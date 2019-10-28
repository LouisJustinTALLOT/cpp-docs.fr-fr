---
title: collate_byname, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688270"
---
# <a name="collate_byname-class"></a>collate_byname, classe

Modèle de classe dérivée qui décrit un objet pouvant servir de facette d’assemblage de paramètres régionaux donnés, permettant ainsi la récupération d’informations spécifiques à une zone culturelle concernant les conventions de tri de chaînes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Paramètres

*_Locname*\
Paramètres régionaux nommés.

*_Refs*\
Nombre initial de références.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet pouvant servir de [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class) de type [collate](../standard-library/collate-class.md#collate)\<CharType >. Son comportement est déterminé par les paramètres régionaux [nommés](../standard-library/locale-class.md#name) *_Locname*. Chaque constructeur initialise son objet de base avec [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
