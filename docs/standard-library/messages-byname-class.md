---
title: messages_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 56d8931cb404d9c0f3f5113f8b2ca0f1158209f2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689330"
---
# <a name="messages_byname-class"></a>messages_byname, classe

Le modèle de classe dérivée décrit un objet pouvant servir de facette de message de paramètres régionaux donnés, permettant ainsi la récupération de messages localisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>Paramètres

*_Locname* \
Paramètres régionaux nommés.

*_Refs* \
Nombre initial de références.

## <a name="remarks"></a>Notes

Son comportement est déterminé par les paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`).

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
