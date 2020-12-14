---
description: 'En savoir plus sur : classe collate_byname'
title: collate_byname, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 8e5ee60a2415fe6fede6db387c774151b97396dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233953"
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

Le modèle de classe décrit un objet pouvant servir de [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class) de type [COLLATE](../standard-library/collate-class.md#collate) \<CharType> . Son comportement est déterminé par les [](../standard-library/locale-class.md#name) paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [COLLATE](../standard-library/collate-class.md#collate) \<CharType> ( `_Refs` ).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
