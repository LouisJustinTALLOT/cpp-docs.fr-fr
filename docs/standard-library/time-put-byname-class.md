---
description: 'En savoir plus sur : classe time_put_byname'
title: time_put_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: b519b28b7af8f5b54f9150d1d84f68cd6695bc49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167251"
---
# <a name="time_put_byname-class"></a>time_put_byname, classe

Le modèle de classe dérivée décrit un objet pouvant servir de facette de paramètres régionaux de type `time_put` \< CharType, OutputIterator > .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Paramètres

*_Locname*\
Nom de paramètres régionaux.

*_Refs*\
Nombre initial de références.

## <a name="remarks"></a>Notes

Son comportement est déterminé par les [](../standard-library/locale-class.md#name) paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [time_put](../standard-library/time-put-class.md#time_put) \<CharType, OutputIterator> ( `_Refs` ).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
