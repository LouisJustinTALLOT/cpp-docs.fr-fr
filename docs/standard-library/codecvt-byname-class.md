---
description: 'En savoir plus sur : classe codecvt_byname'
title: codecvt_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: 526988f46b729e1a3d4ab6892d2c8f1fecba78a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234070"
---
# <a name="codecvt_byname-class"></a>codecvt_byname, classe

Modèle de classe dérivée qui décrit un objet pouvant servir de facette d’assemblage de paramètres régionaux donnés, permettant ainsi la récupération d’informations spécifiques à une zone culturelle concernant les conversions.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>Paramètres

*_Locname*\
Paramètres régionaux nommés.

*_Refs*\
Nombre initial de références.

## <a name="remarks"></a>Notes

Les facettes byname sont créées automatiquement pendant la construction de paramètres régionaux nommés.

Son comportement est déterminé par les paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [codecvt](../standard-library/codecvt-class.md) \<CharType, Byte, StateType> ( `_Refs` ).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
