---
title: codecvt_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_byname
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
ms.openlocfilehash: b48f01126eba7082230fc5e19150d42d1dfad2f3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688290"
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

*_Locname* \
Paramètres régionaux nommés.

*_Refs* \
Nombre initial de références.

## <a name="remarks"></a>Notes

Les facettes byname sont créées automatiquement pendant la construction de paramètres régionaux nommés.

Son comportement est déterminé par les paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [odecvt](../standard-library/codecvt-class.md)\<CharType, Byte, StateType>( `_Refs`).

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
