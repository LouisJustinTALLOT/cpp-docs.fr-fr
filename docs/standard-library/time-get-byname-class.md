---
title: time_get_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: b466f8a893a14f7a94ee7b9e54b72e43aa6cf6e3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460026"
---
# <a name="timegetbyname-class"></a>time_get_byname, classe

La classe de modèle dérivée décrit un objet pouvant servir de facette de paramètres régionaux de type `time_get`\<CharType, InputIterator>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>Paramètres

*_Locname*\
Paramètres régionaux nommés.

*_Refs*\
Nombre initial de références.

## <a name="requirements"></a>Configuration requise

Son comportement est déterminé par les paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator>( `_Refs`).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
